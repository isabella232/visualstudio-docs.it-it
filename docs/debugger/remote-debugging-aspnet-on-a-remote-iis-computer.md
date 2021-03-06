---
title: ASP.NET Core di debug remoto in un computer IIS remoto | Microsoft Docs
description: Eseguire il debug di un'applicazione ASP.NET Core distribuita in un computer Internet Information Services remoto (IIS) con Visual Studio Remote Debugger.
ms.custom: remotedebugging, SEO-VS-2020
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: a364289ded27879c74767f03e89b9ea7b9f604fc
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249908"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>ASP.NET Core di debug remoto in un computer IIS remoto in Visual Studio

Per eseguire il debug di un'applicazione ASP.NET Core distribuita in IIS, installare ed eseguire Remote Tools nel computer in cui è stata distribuita l'app e quindi connettersi all'app in esecuzione da Visual Studio.

![Componenti del debugger remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Questa guida illustra come configurare e configurare un ASP.NET Core di Visual Studio, distribuirlo in IIS e collegarlo da Visual Studio. Per eseguire il debug remoto di ASP.NET 4.5.2, vedere [Remote debug ASP.NET in un computer IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). È anche possibile distribuire ed eseguire il debug in IIS usando Azure. Per app Azure servizio, è possibile distribuire ed eseguire il debug in modo semplice in un'istanza preconfigurata di IIS e del debugger remoto usando il [snapshot debugger](../debugger/debug-live-azure-applications.md) o [connettendo il debugger da Esplora server](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"
Visual Studio 2019 è necessario per seguire i passaggi illustrati in questo articolo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 è necessario per seguire i passaggi illustrati in questo articolo.
::: moniker-end

Queste procedure sono state testate in queste configurazioni del server:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10
* Windows Server 2019 e IIS 10

## <a name="network-requirements"></a>Requisiti di rete

Il debug tra due computer connessi tramite un proxy non è supportato. Non è consigliabile eseguire il debug su una connessione ad alta latenza o larghezza di banda ridotta, ad esempio Internet remoto, o su Internet tra paesi, e potrebbe avere esito negativo o essere inaccettabile. Per un elenco completo dei requisiti, vedere [requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>L'app è già in esecuzione in IIS?

Questo articolo include i passaggi per configurare una configurazione di base di IIS in Windows Server e la distribuzione dell'app da Visual Studio. Questi passaggi sono inclusi per assicurarsi che nel server siano installati i componenti necessari, che l'app possa essere eseguita correttamente e che si è pronti per il debug remoto.

* Se l'app è in esecuzione in IIS e si vuole solo scaricare il debugger remoto e avviare il debug, vedere [scaricare e installare Remote Tools in Windows Server](#BKMK_msvsmon).

* Per assicurarsi che l'applicazione sia configurata, distribuita ed eseguita correttamente in IIS in modo che sia possibile eseguire il debug, seguire tutti i passaggi descritti in questo argomento.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Creare l'applicazione ASP.NET Core nel computer di Visual Studio

1. Creare una nuova applicazione Web ASP.NET Core.

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019, scegliere **Crea un nuovo progetto** nella finestra Start. Se la finestra di avvio non è aperta, scegliere  >  **finestra di avvio** file. Digitare **app Web**, scegliere **C#** come lingua, quindi scegliere **ASP.NET Core applicazione Web (Model-View-Controller)**, quindi scegliere **Avanti**. Nella schermata successiva denominare il progetto **MyASPApp**, quindi scegliere **Avanti**.

    Scegliere il Framework di destinazione consigliato (.NET Core 3,1) o .NET 5, quindi scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 scegliere **File > nuovo progetto >**, quindi selezionare **Visual C# > Web > ASP.NET Core applicazione Web**. Nella sezione modelli di ASP.NET Core selezionare **applicazione Web (Model-View-Controller)**. Assicurarsi che sia selezionata l'opzione ASP.NET Core 2,1, che **Abilita supporto Docker** non sia selezionata e che **l'autenticazione** sia impostata su **Nessuna autenticazione**. Denominare il progetto **MyASPApp**.
    ::: moniker-end

4. Aprire il file About.cshtml.cs e impostare un punto di interruzione nel `OnGet` Metodo (nei modelli precedenti, aprire HomeController.cs e impostare il punto di interruzione nel `About()` metodo).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a> Installare e configurare IIS in Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se in Internet Explorer è abilitata la configurazione della sicurezza avanzata (abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per consentire il download di alcuni componenti del server Web. Aggiungere i siti attendibili passando a **Opzioni Internet > sicurezza > siti attendibili > siti**. Aggiungere i seguenti domini.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Quando si Scarica il software, è possibile ottenere richieste per concedere l'autorizzazione per caricare varie risorse e script del sito Web. Alcune di queste risorse non sono necessarie, ma per semplificare il processo fare clic su **Aggiungi** quando richiesto.

## <a name="install-aspnet-core-on-windows-server"></a>Installare ASP.NET Core in Windows Server

1. Installare il bundle di hosting .NET Core nel sistema di hosting. L'aggregazione installa il runtime di .NET Core, la libreria di .NET Core e il modulo ASP.NET Core. Per istruzioni più dettagliate, vedere la pagina relativa [alla pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    Per .NET Core 3, installare il [bundle di hosting .NET Core](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer).
    Per .NET Core 2, installare l' [hosting di .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting).

    > [!NOTE]
    > Se nel sistema non è presente una connessione a Internet, ottenere e installare *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* prima di installare l'aggregazione di Hosting di .NET Core Windows Server.

2. Riavviare il sistema o eseguire **net stop was /y** seguito da **net start w3svc** da un prompt dei comandi per visualizzare una modifica al percorso di sistema.

## <a name="choose-a-deployment-option"></a>Scegliere un'opzione di distribuzione

Se è necessario assistenza per la distribuzione dell'app in IIS, prendere in considerazione le opzioni seguenti:

* Eseguire la distribuzione creando un file di impostazioni di pubblicazione in IIS e importando le impostazioni in Visual Studio. In alcuni scenari, si tratta di un modo rapido per distribuire l'app. Quando si crea il file delle impostazioni di pubblicazione, le autorizzazioni vengono configurate automaticamente in IIS.

* Eseguire la distribuzione pubblicando in una cartella locale e copiando l'output in base a un metodo preferito in una cartella dell'app preparata in IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Opzionale Eseguire la distribuzione usando un file di impostazioni di pubblicazione

È possibile usare questa opzione per creare un file di impostazioni di pubblicazione e importarlo in Visual Studio.

> [!NOTE]
> Questo metodo di distribuzione utilizza Distribuzione Web, che deve essere installato nel server. Se si desidera configurare Distribuzione Web manualmente anziché importare le impostazioni, è possibile installare Distribuzione Web 3,6 anziché Distribuzione Web 3,6 per i server di hosting. Tuttavia, se si configura Distribuzione Web manualmente, sarà necessario assicurarsi che una cartella dell'app nel server sia configurata con i valori e le autorizzazioni corretti (vedere [configurare il sito Web ASP.NET](#BKMK_deploy_asp_net)).

### <a name="configure-the-aspnet-core-web-site"></a>Configurare il sito Web di ASP.NET Core

1. In Gestione IIS fare clic su **pool di applicazioni** nel riquadro sinistro in **connessioni**. Aprire **DefaultAppPool** e impostare la **versione .NET CLR** su **nessun codice gestito**. Questa operazione è necessaria per ASP.NET Core. Il sito Web predefinito utilizza DefaultAppPool.

2. Arrestare e riavviare il DefaultAppPool.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installare e configurare Distribuzione Web per i server di hosting in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Creare il file delle impostazioni di pubblicazione in IIS in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Quando la distribuzione è completata, l'app viene avviata automaticamente. Se l'app non viene avviata da Visual Studio, avviare l'app in IIS per verificare che venga eseguita correttamente. Per ASP.NET Core, è anche necessario assicurarsi che il campo pool di applicazioni per **DefaultAppPool** sia impostato su **nessun codice gestito**.

1. Passa a una configurazione di debug.

   ::: moniker range=">=vs-2019"
   Scegliere **modifica** per modificare il profilo, quindi scegliere **Impostazioni**. Scegliere una configurazione di **debug** , quindi scegliere **Rimuovi file aggiuntivi nella destinazione** sotto le opzioni di **pubblicazione file** .
   ::: moniker-end
   ::: moniker range="vs-2017"
   Nella finestra di dialogo **Impostazioni** abilitare il debug facendo clic su **Avanti**, scegliere una configurazione di **debug** , quindi scegliere **Rimuovi file aggiuntivi nella destinazione** sotto le opzioni di **pubblicazione file** .
   ::: moniker-end

   > [!IMPORTANT]
   > Se si sceglie una configurazione di versione, si disabilita il debug nel file di *web.config* durante la pubblicazione.

1. Fare clic su **Save (Salva** ) e quindi pubblicare nuovamente l'app.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Opzionale Eseguire la distribuzione tramite la pubblicazione in una cartella locale

È possibile usare questa opzione per distribuire l'app se si vuole copiare l'app in IIS usando PowerShell, RoboCopy o si desidera copiare manualmente i file.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Configurare il sito Web di ASP.NET Core nel computer Windows Server

1. Aprire Esplora risorse e creare una nuova cartella, **C:\publish**, in cui in seguito si distribuirà il progetto ASP.NET Core.

2. Se non è già aperto, aprire **gestione Internet Information Services (IIS)**. Nel riquadro sinistro di Server Manager selezionare **IIS**. Fare clic con il pulsante destro del mouse sul server e selezionare **Gestione Internet Information Services (IIS)**.

3. In **connessioni** nel riquadro sinistro passare a **siti**.

4. Selezionare il **sito Web predefinito**, scegliere **impostazioni di base** e impostare il **percorso fisico** su **C:\publish**.

5. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

6. Impostare il campo **alias** su **MyASPApp**, accettare il pool di applicazioni predefinito (**DefaultAppPool**) e impostare il **percorso fisico** su **C:\publish**.

7. In **connessioni** selezionare **pool di applicazioni**. Aprire **DefaultAppPool** e impostare il campo pool di applicazioni su **nessun codice gestito**.

8. Fare clic con il pulsante destro del mouse sul nuovo sito in Gestione IIS, scegliere **modifica autorizzazioni** e assicurarsi che IUSR, IIS_IUSRS o l'utente configurato per l'accesso all'app Web sia un utente autorizzato con lettura & Esegui diritti.

    Se non viene visualizzato uno di questi utenti con accesso, seguire la procedura per aggiungere IUSR come utente con i diritti di esecuzione di lettura &.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Pubblicare e distribuire l'app pubblicando in una cartella locale da Visual Studio

È anche possibile pubblicare e distribuire l'app usando il file system o altri strumenti.

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

1. Nel computer di Visual Studio aprire la soluzione di cui si sta provando a eseguire il debug (**MyASPApp** se si seguono tutti i passaggi descritti in questo articolo).
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

    Se si vuole usare il pulsante **trova** , potrebbe essere necessario aprire la [porta UDP 3702](#bkmk_openports) sul server.

5. Selezionare  **Mostra i processi di tutti gli utenti**.

6. Digitare la prima lettera del nome del processo per trovare rapidamente l'app.

    * Se si usa il [modello di hosting in-process](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) in IIS, selezionare il processo di **w3wp.exe** corretto. A partire da .NET Core 3, si tratta dell'impostazione predefinita.

    * In caso contrario, selezionare il processo **dotnet.exe** . Si tratta del modello di hosting out-of-process.

    Se sono presenti più processi che mostrano *w3wp.exe* o *dotnet.exe*, controllare la colonna **nome utente** . In alcuni scenari, nella colonna **nome utente** viene visualizzato il nome del pool di applicazioni, ad esempio **IIS APPPOOL\DefaultAppPool**. Se viene visualizzato il pool di app, ma non è univoco, creare un nuovo pool di app denominato per l'istanza dell'app di cui si vuole eseguire il debug, quindi è possibile trovarlo facilmente nella colonna **nome utente** .

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Scegliere **Connetti**.

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

2. Scegliere quindi **regole in ingresso > nuova regola > porta**, quindi fare clic su **Avanti**. Per UDP 3702, scegliere invece **regole in uscita** .

3. In **porte locali specifiche** immettere il numero di porta, quindi fare clic su **Avanti**.

4. Fare clic su **Consenti la connessione**, quindi su **Avanti**.

5. Selezionare uno o più tipi di rete da abilitare per la porta e fare clic su **Avanti**.

    Il tipo selezionato deve includere la rete a cui è connesso il computer remoto.
6. Aggiungere il nome (ad esempio, **IIS**, **distribuzione Web** o **msvsmon**) per la regola in ingresso e fare clic su **fine**.

    La nuova regola dovrebbe comparire nell'elenco Regole in ingresso o Regole in uscita.

    Per altri dettagli sulla configurazione di Windows Firewall, vedere [configurare il Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Creare regole aggiuntive per le altre porte obbligatorie.
