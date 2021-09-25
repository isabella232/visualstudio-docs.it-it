---
title: Eseguire il debug remoto di ASP.NET in un computer IIS
description: Informazioni su come configurare un'applicazione Visual Studio ASP.NET MVC 4.5.2, distribuirla in IIS e connettere il debugger remoto da Visual Studio.
ms.custom:
- remotedebugging
- seodec18
ms.date: 08/31/2021
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: 406f05fbb5d1517fd953c8732eaa8f4ac9522b3d
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427239"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Eseguire il debug remoto di ASP.NET in un computer IIS remoto

Per eseguire il debug di un'applicazione ASP.NET distribuita in IIS, installare ed eseguire gli strumenti remoti nel computer in cui è stata distribuita l'app e quindi connettersi all'app in esecuzione da Visual Studio.

![Componenti del debugger remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Questa guida illustra come configurare e configurare un'applicazione Visual Studio ASP.NET MVC 4.5.2, distribuirla in IIS e connettere il debugger remoto da Visual Studio.

> [!NOTE]
> Per eseguire il debug ASP.NET Core remoto, vedere Remote Debug ASP.NET Core on an IIS Computer (Debug [remoto ASP.NET Core in un computer IIS).](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) Ad Servizio app di Azure, è possibile distribuire ed eseguire facilmente il debug in un'istanza preconfigurata di IIS usando [Snapshot Debugger](../debugger/debug-live-azure-applications.md) (è necessario .NET 4.6.1) o collegando il [debugger da Esplora server](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"
Visual Studio 2019 è necessario per seguire la procedura illustrata in questo articolo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 è necessario seguire la procedura illustrata in questo articolo.
::: moniker-end

Queste procedure sono state testate in queste configurazioni del server:

* Windows Server 2012 R2 e IIS 8 (per Windows Server 2008 R2, i passaggi del server sono diversi)

## <a name="network-requirements"></a>Requisiti di rete

Il debugger remoto è supportato in Windows Server a partire da Windows Server 2008 Service Pack 2. Per un elenco completo dei requisiti, vedere [Requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Il debug tra due computer connessi tramite un proxy non è supportato. Il debug tramite una connessione a latenza elevata o a larghezza di banda ridotta, ad esempio una connessione internet remota o tramite Internet tra paesi diversi, non è consigliato e può avere esito negativo o essere inaccettabilmente lento.

## <a name="app-already-running-in-iis"></a>App già in esecuzione in IIS?

Questo articolo include i passaggi per configurare una configurazione di base di IIS Windows server e distribuire l'app da Visual Studio. Questi passaggi sono inclusi per assicurarsi che nel server siano installati componenti necessari, che l'app possa essere eseguita correttamente e che si sia pronti per il debug remoto.

* Se l'app è in esecuzione in IIS e si vuole semplicemente scaricare il debugger remoto e avviare il debug, passare a Scaricare e installare gli strumenti remoti [in Windows Server](#BKMK_msvsmon).

* Per assicurarsi che l'app sia configurata, distribuita e in esecuzione correttamente in IIS in modo da poter eseguire il debug, seguire tutti i passaggi descritti in questo argomento.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Creare l'ASP.NET 4.5.2 nel computer Visual Studio locale

1. Creare una nuova applicazione MVC ASP.NET

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 digitare **CTRL+Q** per aprire la casella di ricerca, digitare **asp.net**, scegliere **Modelli,** quindi scegliere Crea nuova **applicazione Web ASP.NET (.NET Framework).** Nella finestra di dialogo visualizzata assegnare al progetto il nome **MyASPApp** e quindi scegliere **Crea**. Selezionare **MVC** e scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    A tale scopo in Visual Studio 2017, scegliere **File > Nuovo > Project**, quindi selezionare Visual **C# > Web > ASP.NET App Web**. Nella sezione modelli **ASP.NET 4.5.2** selezionare **MVC**. Assicurarsi che **l'opzione Abilita supporto Docker** non sia selezionata e che **l'opzione Autenticazione** sia impostata su **Nessuna autenticazione**. Assegnare al progetto **il nome MyASPApp.**
    ::: moniker-end

2. Aprire il file  *HomeController.cs* e impostare un punto di interruzione nel `About()` metodo .

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Installare e configurare IIS in Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se La configurazione di sicurezza avanzata è abilitata in Internet Explorer (abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per consentire il download di alcuni componenti del server Web. Aggiungere i siti attendibili selezionando Opzioni Internet > **Sicurezza > siti attendibili > Siti attendibili**. Aggiungere i domini seguenti.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Quando si scarica il software, è possibile che si otterrà la richiesta di concedere l'autorizzazione per caricare vari script e risorse del sito Web. Alcune di queste risorse non sono necessarie, ma per semplificare il processo, fare clic **su Aggiungi** quando richiesto.

## <a name="install-aspnet-45-on-windows-server"></a><a name="BKMK_deploy_asp_net"></a>Installare ASP.NET 4.5 in Windows Server

Per informazioni più dettagliate sull'installazione di ASP.NET in IIS, vedere [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5 ( IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)).

1. Nel riquadro sinistro della Server Manager selezionare **IIS**. Fare clic con il pulsante destro del mouse sul server **e scegliere Gestione Internet Information Services (IIS).**

1. Usare l'Installazione guidata piattaforma Web (WebPI) per installare ASP.NET 4.5 (dal nodo Server in Windows Server 2012 R2 scegliere Ottieni nuovi componenti della piattaforma **Web** e quindi cercare ASP.NET)

    ![Screenshot di Web Platform Installer 5.0 che mostra i risultati della ricerca per asp.net con il componente della piattaforma Web IIS: ASP.NET 4.5 cerchiato in rosso.](../debugger/media/remotedbg_iis_aspnet_45.png)

    > [!NOTE]
    > Se si usa Windows Server 2008 R2, installare ASP.NET 4 usando questo comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Riavviare il sistema o eseguire **net stop was /y** seguito da **net start w3svc** da un prompt dei comandi per visualizzare una modifica al percorso di sistema.

## <a name="choose-a-deployment-option"></a>Scegliere un'opzione di distribuzione

Se è necessario assistenza per distribuire l'app in IIS, prendere in considerazione queste opzioni:

* Eseguire la distribuzione creando un file di impostazioni di pubblicazione in IIS e importando le impostazioni in Visual Studio. In alcuni scenari si tratta di un modo rapido per distribuire l'app. Quando si crea il file di impostazioni di pubblicazione, le autorizzazioni vengono impostate automaticamente in IIS.

* Eseguire la distribuzione pubblicando in una cartella locale e copiando l'output con un metodo preferito in una cartella dell'app preparata in IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Facoltativo) Eseguire la distribuzione usando un file di impostazioni di pubblicazione

È possibile usare questa opzione per creare un file di impostazioni di pubblicazione e importarlo in Visual Studio.

> [!NOTE]
> Questo metodo di distribuzione Distribuzione Web, che deve essere installato nel server. Se si vuole configurare manualmente Distribuzione Web anziché importare le impostazioni, è possibile installare Distribuzione Web 3.6 anziché Distribuzione Web 3.6 per i server di hosting. Tuttavia, se si configura Distribuzione Web manualmente, è necessario assicurarsi che una cartella dell'app nel server sia configurata con i valori e le autorizzazioni corretti (vedere Configurare un sito [Web](#BKMK_deploy_asp_net)di ASP.NET ).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installare e configurare Distribuzione Web server di hosting in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Creare il file delle impostazioni di pubblicazione in IIS in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Quando la distribuzione è completata, l'app viene avviata automaticamente. Se l'app non viene avviata Visual Studio, avviare l'app in IIS.

1. Passare a una configurazione di debug.

   ::: moniker range=">=vs-2019"
   Scegliere **Modifica** per modificare il profilo e quindi scegliere **Impostazioni**. Scegliere una **configurazione** di debug e quindi scegliere **Rimuovi file aggiuntivi nella destinazione** nelle opzioni Di **pubblicazione** file.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Nella finestra **Impostazioni** debug, abilitare il debug facendo  clic su **Avanti,** scegliere una configurazione di debug e quindi scegliere Rimuovi file aggiuntivi nella destinazione nelle **opzioni Di** pubblicazione file. 
   ::: moniker-end

   > [!IMPORTANT]
   > Se si sceglie una configurazione di versione, si disabilita il debug nel file *web.config* durante la pubblicazione.

1. Fare **clic su** Salva e quindi ripubblicare l'app.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Facoltativo) Eseguire la distribuzione pubblicando in una cartella locale

È possibile usare questa opzione per distribuire l'app se si vuole copiare l'app in IIS usando PowerShell, RoboCopy o copiare manualmente i file.

### <a name="configure-the-aspnet-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Configurare il ASP.NET Web nel computer Windows Server

1. Aprire Windows Explorer e creare una nuova cartella, **C:\Publish**, in cui in seguito si distribuirà il ASP.NET progetto.

2. Se non è già aperto, aprire gestione Internet Information Services **(IIS).** Nel riquadro sinistro della Server Manager selezionare **IIS.** Fare clic con il pulsante destro del mouse sul server e selezionare **Gestione Internet Information Services (IIS)**.

3. In **Connessioni** nel riquadro sinistro passare a **Siti**.

4. Selezionare il **sito Web predefinito,** scegliere **Impostazioni** di base e impostare **percorso fisico** **su C:\Publish**.

5. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

6. Impostare il **campo Alias** su **MyASPApp**, accettare il pool di applicazioni predefinito (**DefaultAppPool**) e impostare **il percorso fisico** su **C:\Publish**.

7. In **Connessioni** selezionare **Pool di applicazioni**. Aprire **DefaultAppPool** e impostare il campo Pool di applicazioni **su ASP.NET v4.0** (ASP.NET 4.5 non è un'opzione per il pool di applicazioni).

8. Con il sito selezionato in Gestione IIS, scegliere Modifica autorizzazioni e assicurarsi che IUSR, IIS_IUSRS o l'utente configurato per il pool di applicazioni sia un utente autorizzato con diritti di lettura & Execute. Se nessuno di questi utenti è presente, aggiungere IUSR come utente con diritti di & Execute.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Pubblicare e distribuire l'app pubblicando in una cartella locale da Visual Studio

È anche possibile pubblicare e distribuire l'app usando file system o altri strumenti.

1. (ASP.NET 4.5.2) Assicurarsi che nel file web.config sia elencata la versione corretta di .NET.  Ad esempio, se si ha come destinazione ASP.NET 4.5.2, assicurarsi che questa versione sia elencata in web.config.

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    Ad esempio, la versione deve essere 4.0 se si installa ASP.NET 4 anziché 4.5.2.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Scaricare e installare gli strumenti remoti in Windows Server

Scaricare la versione degli strumenti remoti che corrisponde alla versione di Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Configurare il debugger remoto in Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere autorizzazioni per altri utenti, modificare la modalità di autenticazione o il numero di porta per il debugger [remoto,](../debugger/remote-debugging.md#configure_msvsmon)vedere Configurare il debugger remoto .

Per informazioni sull'esecuzione del debugger remoto come servizio, vedere [Eseguire il debugger remoto come servizio](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Connettersi all'applicazione ASP.NET dal computer Visual Studio computer

1. Nel computer Visual Studio aprire la soluzione di cui si sta tentando di eseguire il debug (**MyASPApp** se si segue la procedura descritta in questo articolo).
2. In Visual Studio fare clic su **Debug > collega a processo** (CTRL+ALT+P).

    > [!TIP]
    > In Visual Studio 2017 e versioni successive, è possibile ricollegare allo stesso processo a cui è stato precedentemente collegato usando Debug > Ricollegare a **processo...** (MAIUSC+ALT+P).

3. Impostare il campo Qualificatore su **\<remote computer name>** e premere **INVIO.**

    Verificare che Visual Studio la porta necessaria al nome del computer, che viene visualizzato nel formato: **\<remote computer name> :p ort**

    ::: moniker range=">=vs-2022"
    In Visual Studio 2022 dovrebbe essere visualizzato **\<remote computer name> :4026**
    ::: moniker-end
    ::: moniker range="vs-2019"
    In Visual Studio 2019 dovrebbe essere visualizzato **\<remote computer name> :4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 dovrebbe essere visualizzato **\<remote computer name> :4022**
    ::: moniker-end
    La porta è obbligatoria. Se il numero di porta non viene visualizzato, aggiungerlo manualmente.

4. Fare clic su **Aggiorna**.
    Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.

    Se non viene visualizzato alcun processo, provare a usare l'indirizzo IP anziché il nome del computer remoto (la porta è obbligatoria). È possibile usare `ipconfig` in una riga di comando per ottenere l'indirizzo IPv4.

5. Selezionare  **Mostra i processi di tutti gli utenti**.

6. Digitare la prima lettera del nome di un processo per **trovare** rapidamentew3wp.exeper ASP.NET 4.5.

    Se sono presenti più processi che **w3wp.exe,** controllare la **colonna Nome** utente. In alcuni scenari la colonna **Nome utente** mostra il nome del pool di app, ad esempio **IIS APPPOOL\DefaultAppPool.** Se viene visualizzato il pool di app, un modo semplice per identificare il processo corretto è creare un nuovo pool di app denominato per l'istanza dell'app di cui si vuole eseguire il debug e quindi trovarlo facilmente nella colonna **Nome** utente.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Fare clic **su Allega**

8. Aprire il sito Web del computer remoto. In un browser passare a **http:// \<remote computer name>**.

    Verrà visualizzata la pagina Web ASP.NET.
9. Nell'applicazione ASP.NET in esecuzione fare clic sul collegamento alla **pagina** Informazioni su.

    Il punto di interruzione verrà raggiunto in Visual Studio.

## <a name="troubleshooting-iis-deployment"></a>Risoluzione dei problemi relativi alla distribuzione di IIS

- Se non è possibile connettersi all'host usando il nome host, provare l'indirizzo IP.
- Assicurarsi che le porte necessarie siano aperte nel server remoto.
- Verificare che la versione ASP.NET usata nell'app sia la stessa della versione installata nel server. Per l'app, è possibile visualizzare e impostare la versione nella **pagina** Proprietà. Per impostare l'app su una versione diversa, è necessario installare tale versione.
- Se l'app ha provato ad aprire, ma viene visualizzato un avviso relativo al certificato, scegliere di considerare attendibile il sito. Se l'avviso è già stato chiuso, è possibile modificare il profilo di pubblicazione, un file *.pubxml, nel progetto e aggiungere l'elemento seguente (solo per test): `<AllowUntrustedCertificate>true</AllowUntrustedCertificate>`
- Se l'app non viene avviata Visual Studio, avviare l'app in IIS per verificare che sia stata distribuita correttamente.
- Controllare la finestra Output in Visual Studio informazioni sullo stato e controllare i messaggi di errore.
- 
## <a name="open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Aprire le porte necessarie in Windows Server

Nella maggior parte delle configurazioni, le porte necessarie vengono aperte dall'installazione di ASP.NET e del debugger remoto. Tuttavia, potrebbe essere necessario verificare che le porte siano aperte.

> [!NOTE]
> In una macchina virtuale di Azure è necessario aprire le porte tramite il [gruppo di sicurezza di rete](/azure/virtual-machines/windows/nsg-quickstart-portal).

Porte necessarie:

* 80 - Obbligatorio per IIS
::: moniker range=">=vs-2022"
* 4026 - Obbligatorio per il debug remoto da Visual Studio 2022 (per altre informazioni, vedere [Assegnazioni](../debugger/remote-debugger-port-assignments.md) delle porte del debugger remoto).
::: moniker-end
::: moniker range=">=vs-2019"
* 4024 : obbligatorio per il debug remoto da Visual Studio 2019 (per altre informazioni, vedere [Assegnazioni](../debugger/remote-debugger-port-assignments.md) delle porte del debugger remoto).
::: moniker-end
::: moniker range="vs-2017"
* 4022 : obbligatorio per il debug remoto da Visual Studio 2017 (per altre informazioni, vedere [Assegnazioni](../debugger/remote-debugger-port-assignments.md) di porte del debugger remoto).
::: moniker-end
* UDP 3702- (facoltativo) Porta  di individuazione consente di fare clic sul pulsante Trova quando ci si connette al debugger remoto in Visual Studio.

1. Per aprire una porta in Windows Server, aprire il menu **Start,** cercare Windows **Firewall con sicurezza avanzata**.

2. Scegliere quindi **Regole in ingresso > nuova regola > porta**. Scegliere  Avanti e in Porte locali specifiche immettere il numero di porta, fare clic su Avanti **,** quindi su Consenti connessione **,** su Avanti e aggiungere il nome (**IIS,** **Distribuzione Web** o **msvsmon**) per la regola in ingresso.

    Per altri dettagli sulla configurazione di Windows Firewall, vedere Configurare il firewall Windows [per il debug remoto.](../debugger/configure-the-windows-firewall-for-remote-debugging.md)

3. Creare regole aggiuntive per le altre porte necessarie.