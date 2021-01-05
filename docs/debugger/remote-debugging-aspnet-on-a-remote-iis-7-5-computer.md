---
title: Eseguire il debug remoto di ASP.NET in un computer IIS
description: Informazioni su come configurare e configurare un'applicazione ASP.NET MVC 4.5.2 di Visual Studio, distribuirla in IIS e alleghire il debugger remoto da Visual Studio.
ms.custom:
- remotedebugging
- seodec18
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 8a3520220da15ef771c8cecbd7962e4448727910
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815711"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Eseguire il debug remoto di ASP.NET in un computer IIS remoto
Per eseguire il debug di un'applicazione ASP.NET distribuita in IIS, installare ed eseguire Remote Tools nel computer in cui è stata distribuita l'app e quindi connettersi all'app in esecuzione da Visual Studio.

![Componenti del debugger remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Questa guida illustra come configurare e configurare un'applicazione ASP.NET MVC 4.5.2 di Visual Studio, come distribuirla in IIS e come connettersi al debugger remoto da Visual Studio.

> [!NOTE]
> Per eseguire il debug remoto ASP.NET Core in alternativa, vedere [ASP.NET Core di debug remoto in un computer IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Per app Azure servizio, è possibile distribuire ed eseguire il debug in un'istanza preconfigurata di IIS usando il [snapshot debugger](../debugger/debug-live-azure-applications.md) (4.6.1 .NET obbligatorio) o [connettendo il debugger da Esplora server](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"
Visual Studio 2019 è necessario per seguire i passaggi illustrati in questo articolo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 è necessario per seguire i passaggi illustrati in questo articolo.
::: moniker-end

Queste procedure sono state testate in queste configurazioni del server:
* Windows Server 2012 R2 e IIS 8 (per Windows Server 2008 R2, i passaggi del server sono diversi)

## <a name="network-requirements"></a>Requisiti di rete

Il debugger remoto è supportato in Windows Server a partire da Windows Server 2008 Service Pack 2. Per un elenco completo dei requisiti, vedere [requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Il debug tra due computer connessi tramite un proxy non è supportato. Non è consigliabile eseguire il debug su una connessione ad alta latenza o larghezza di banda ridotta, ad esempio Internet remoto, o su Internet tra paesi, e potrebbe avere esito negativo o essere inaccettabile.

## <a name="app-already-running-in-iis"></a>L'app è già in esecuzione in IIS?

Questo articolo include i passaggi per configurare una configurazione di base di IIS in Windows Server e la distribuzione dell'app da Visual Studio. Questi passaggi sono inclusi per assicurarsi che nel server siano installati i componenti necessari, che l'app possa essere eseguita correttamente e che si è pronti per il debug remoto.

* Se l'app è in esecuzione in IIS e si vuole solo scaricare il debugger remoto e avviare il debug, vedere [scaricare e installare Remote Tools in Windows Server](#BKMK_msvsmon).

* Per assicurarsi che l'applicazione sia configurata, distribuita ed eseguita correttamente in IIS in modo che sia possibile eseguire il debug, seguire tutti i passaggi descritti in questo argomento.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Creare l'applicazione ASP.NET 4.5.2 nel computer di Visual Studio

1. Creare una nuova applicazione MVC ASP.NET

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019, digitare **CTRL + Q** per aprire la casella di ricerca, digitare **ASP.NET**, scegliere **modelli**, quindi fare clic su **Crea nuova applicazione Web ASP.NET (.NET Framework)**. Nella finestra di dialogo visualizzata, denominare il progetto **MyASPApp**, quindi scegliere **Crea**. Selezionare **MVC** e scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Per eseguire questa operazione in Visual Studio 2017, scegliere **File > nuovo progetto >**, quindi selezionare **Visual C# > Web > ASP.NET Web Application**. Nella sezione modelli **ASP.NET 4.5.2** selezionare **MVC**. Assicurarsi che l'opzione **Abilita supporto Docker** non sia selezionata e che **l'autenticazione** sia impostata su **Nessuna autenticazione**. Denominare il progetto **MyASPApp**.
    ::: moniker-end

2. Aprire il file  *HomeController.cs* e impostare un punto di interruzione nel `About()` metodo.

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a> Installare e configurare IIS in Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se in Internet Explorer è abilitata la configurazione della sicurezza avanzata (abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per consentire il download di alcuni componenti del server Web. Aggiungere i siti attendibili passando a **Opzioni Internet > sicurezza > siti attendibili > siti**. Aggiungere i seguenti domini.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Quando si Scarica il software, è possibile ottenere richieste per concedere l'autorizzazione per caricare varie risorse e script del sito Web. Alcune di queste risorse non sono necessarie, ma per semplificare il processo fare clic su **Aggiungi** quando richiesto.

## <a name="install-aspnet-45-on-windows-server"></a><a name="BKMK_deploy_asp_net"></a> Installare ASP.NET 4,5 in Windows Server

Per informazioni più dettagliate sull'installazione di ASP.NET in IIS, vedere [iis 8,0 con ASP.NET 3,5 e ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Nel riquadro sinistro di Server Manager selezionare **IIS**. Fare clic con il pulsante destro del mouse sul server e scegliere **gestione Internet Information Services (IIS)**.

1. Usare l'installazione guidata piattaforma Web (WebPI) per installare ASP.NET 4,5 (dal nodo del server in Windows Server 2012 R2, scegliere **Ottieni nuovi componenti della piattaforma Web** e quindi cercare ASP.NET)

    ![Screenshot dell'installazione guidata piattaforma Web 5,0 che mostra i risultati della ricerca per asp.net con il componente della piattaforma Web IIS: ASP.NET 4,5 con cerchio in rosso.](../debugger/media/remotedbg_iis_aspnet_45.png)

    > [!NOTE]
    > Se si usa Windows Server 2008 R2, installare ASP.NET 4 usando invece questo comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Riavviare il sistema o eseguire **net stop was /y** seguito da **net start w3svc** da un prompt dei comandi per visualizzare una modifica al percorso di sistema.

## <a name="choose-a-deployment-option"></a>Scegliere un'opzione di distribuzione

Se è necessario assistenza per la distribuzione dell'app in IIS, prendere in considerazione le opzioni seguenti:

* Eseguire la distribuzione creando un file di impostazioni di pubblicazione in IIS e importando le impostazioni in Visual Studio. In alcuni scenari, si tratta di un modo rapido per distribuire l'app. Quando si crea il file delle impostazioni di pubblicazione, le autorizzazioni vengono configurate automaticamente in IIS.

* Eseguire la distribuzione pubblicando in una cartella locale e copiando l'output in base a un metodo preferito in una cartella dell'app preparata in IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Opzionale Eseguire la distribuzione usando un file di impostazioni di pubblicazione

È possibile usare questa opzione per creare un file di impostazioni di pubblicazione e importarlo in Visual Studio.

> [!NOTE]
> Questo metodo di distribuzione utilizza Distribuzione Web, che deve essere installato nel server. Se si desidera configurare Distribuzione Web manualmente anziché importare le impostazioni, è possibile installare Distribuzione Web 3,6 anziché Distribuzione Web 3,6 per i server di hosting. Tuttavia, se si configura Distribuzione Web manualmente, sarà necessario assicurarsi che una cartella dell'app nel server sia configurata con i valori e le autorizzazioni corretti (vedere [configurare il sito Web ASP.NET](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installare e configurare Distribuzione Web per i server di hosting in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Creare il file delle impostazioni di pubblicazione in IIS in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Quando la distribuzione è completata, l'app viene avviata automaticamente. Se l'app non viene avviata da Visual Studio, avviare l'app in IIS.

1. Nella finestra di dialogo **Impostazioni** abilitare il debug facendo clic su **Avanti**, scegliere una configurazione di **debug** , quindi scegliere **Rimuovi file aggiuntivi nella destinazione** sotto le opzioni di **pubblicazione file** .

    > [!IMPORTANT]
    > Se si sceglie una configurazione di versione, si disabilita il debug nel file di *web.config* durante la pubblicazione.

1. Fare clic su **Save (Salva** ) e quindi pubblicare nuovamente l'app.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Opzionale Eseguire la distribuzione tramite la pubblicazione in una cartella locale

È possibile usare questa opzione per distribuire l'app se si vuole copiare l'app in IIS usando PowerShell, RoboCopy o si desidera copiare manualmente i file.

### <a name="configure-the-aspnet-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Configurare il sito Web ASP.NET nel computer Windows Server

1. Aprire Esplora risorse e creare una nuova cartella, **C:\publish**, in cui si distribuirà successivamente il progetto ASP.NET.

2. Se non è già aperto, aprire **gestione Internet Information Services (IIS)**. Nel riquadro sinistro di Server Manager selezionare **IIS**. Fare clic con il pulsante destro del mouse sul server e selezionare **Gestione Internet Information Services (IIS)**.

3. In **connessioni** nel riquadro sinistro passare a **siti**.

4. Selezionare il **sito Web predefinito**, scegliere **impostazioni di base** e impostare il **percorso fisico** su **C:\publish**.

5. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

6. Impostare il campo **alias** su **MyASPApp**, accettare il pool di applicazioni predefinito (**DefaultAppPool**) e impostare il **percorso fisico** su **C:\publish**.

7. In **connessioni** selezionare **pool di applicazioni**. Aprire **DefaultAppPool** e impostare il campo pool di applicazioni su **ASP.NET v 4.0** (ASP.NET 4,5 non è un'opzione per il pool di applicazioni).

8. Con il sito selezionato in Gestione IIS, scegliere **modifica autorizzazioni** e verificare che IUSR, IIS_IUSRS o l'utente configurato per il pool di applicazioni sia un utente autorizzato con lettura & Esegui diritti. Se nessuno di questi utenti è presente, aggiungere IUSR come utente con i diritti di esecuzione Read &.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Pubblicare e distribuire l'app pubblicando in una cartella locale da Visual Studio

È anche possibile pubblicare e distribuire l'app usando il file system o altri strumenti.

1. (ASP.NET 4.5.2) Verificare che nel file di web.config sia elencata la versione corretta di .NET.  Ad esempio, se la destinazione è ASP.NET 4.5.2, verificare che questa versione sia elencata in web.config.

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    Ad esempio, la versione deve essere 4,0 se si installa ASP.NET 4 anziché 4.5.2.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Scaricare e installare Remote Tools in Windows Server

Scaricare la versione di Remote Tools corrispondente alla versione di Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Configurare il debugger remoto in Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere autorizzazioni per utenti aggiuntivi, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [configurare il debugger remoto](../debugger/remote-debugging.md#configure_msvsmon).

Per informazioni sull'esecuzione del debugger remoto come servizio, vedere [eseguire il debugger remoto come servizio](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Connettersi all'applicazione ASP.NET dal computer che esegue Visual Studio

1. Nel computer di Visual Studio aprire la soluzione di cui si sta provando a eseguire il debug (**MyASPApp** se si seguono i passaggi descritti in questo articolo).
2. In Visual Studio fare clic su **Debug > Connetti a processo** (CTRL + ALT + P).

    > [!TIP]
    > In Visual Studio 2017 e versioni successive, è possibile ricollegarsi allo stesso processo collegato in precedenza utilizzando **Debug > Riconnetti a processo...** (MAIUSC + ALT + P).

3. Impostare il campo qualificatore su **\<remote computer name>** e premere **invio**.

    Verificare che in Visual Studio venga aggiunta la porta richiesta al nome del computer, che viene visualizzato nel formato: **\<remote computer name> :p Ort**

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 dovrebbe essere visualizzato **\<remote computer name> : 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 dovrebbe essere visualizzato **\<remote computer name> : 4022**
    ::: moniker-end
    La porta è obbligatoria. Se il numero di porta non è visibile, aggiungerlo manualmente.

4. Fare clic su **Aggiorna**.
    Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.

    Se non vengono visualizzati processi, provare a usare l'indirizzo IP anziché il nome del computer remoto (la porta è obbligatoria). È possibile usare `ipconfig` in una riga di comando per ottenere l'indirizzo IPv4.

5. Selezionare  **Mostra i processi di tutti gli utenti**.

6. Digitare la prima lettera del nome di un processo per trovare rapidamente **w3wp.exe** per ASP.NET 4,5.

    Se sono presenti più processi che mostrano **w3wp.exe**, controllare la colonna **nome utente** . In alcuni scenari, nella colonna **nome utente** viene visualizzato il nome del pool di applicazioni, ad esempio **IIS APPPOOL\DefaultAppPool**. Se il pool di app viene visualizzato, un modo semplice per identificare il processo corretto consiste nel creare un nuovo pool di app denominato per l'istanza dell'app di cui si vuole eseguire il debug, quindi è possibile trovarlo facilmente nella colonna **nome utente** .

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Fare clic su **Connetti**

8. Aprire il sito Web del computer remoto. In un browser passare a **http:// \<remote computer name>**.

    Verrà visualizzata la pagina Web ASP.NET.
9. Nell'applicazione ASP.NET in esecuzione fare clic sul collegamento alla pagina **About** .

    Il punto di interruzione verrà raggiunto in Visual Studio.

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Risoluzione dei problemi Aprire le porte necessarie in Windows Server

Nella maggior parte delle configurazioni, le porte obbligatorie vengono aperte mediante l'installazione di ASP.NET e del debugger remoto. Tuttavia, potrebbe essere necessario verificare che le porte siano aperte.

> [!NOTE]
> In una macchina virtuale di Azure è necessario aprire le porte tramite il [gruppo di sicurezza di rete](/azure/virtual-machines/windows/nsg-quickstart-portal).

Porte obbligatorie:

* 80-obbligatorio per IIS
::: moniker range=">=vs-2019"
* 4024: richiesto per il debug remoto da Visual Studio 2019. per ulteriori informazioni, vedere le [assegnazioni delle porte del debugger remoto](../debugger/remote-debugger-port-assignments.md) .
::: moniker-end
::: moniker range="vs-2017"
* 4022: richiesto per il debug remoto da Visual Studio 2017. per ulteriori informazioni, vedere le [assegnazioni delle porte del debugger remoto](../debugger/remote-debugger-port-assignments.md) .
::: moniker-end
* UDP 3702-(facoltativo) la porta di individuazione consente di **accedere** al pulsante trova quando ci si connette al debugger remoto in Visual Studio.

1. Per aprire una porta in Windows Server, aprire il menu **Start** , cercare **Windows Firewall con sicurezza avanzata**.

2. Scegliere quindi **regole in ingresso > nuova regola > porta**. Scegliere **Avanti** e in **porte locali specifiche**, immettere il numero di porta, fare clic su **Avanti**, quindi **consentire la connessione**, fare clic su avanti e aggiungere il nome (**IIS**, **distribuzione Web** o **msvsmon**) per la regola in ingresso.

    Per altri dettagli sulla configurazione di Windows Firewall, vedere [configurare il Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Creare regole aggiuntive per le altre porte obbligatorie.