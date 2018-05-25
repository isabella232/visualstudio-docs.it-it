---
title: Eseguire il Debug remoto Core ASP.NET in IIS e Azure | Documenti Microsoft
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 202e9ce6e0a53c6967ebe1bacaa6553a1241298e
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2018
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Eseguire il Debug remoto di ASP.NET Core in IIS in Azure in Visual Studio 2017

Questa guida viene illustrato come impostare e configurare un'applicazione ASP.NET Core 2017 di Visual Studio, distribuirlo in IIS utilizzando Azure e collegare il debugger remoto da Visual Studio.

Il metodo consigliato per eseguire il debug remoto in Azure dipende dallo scenario:

* Per eseguire il debug ASP.NET Core servizio App di Azure, vedere [App Azure Debug tramite il Debugger Snapshot](../debugger/debug-live-azure-applications.md). Questo è il metodo consigliato.
* Per eseguire il debug ASP.NET Core nel servizio App di Azure utilizzando le funzionalità di debug più tradizionale, attenersi alla procedura descritta in questo argomento (vedere la sezione [eseguire il debug remoto in Azure App Service](#remote_debug_azure_app_service)).

    In questo scenario, è necessario distribuire l'app da Visual Studio in Azure, ma non è necessario installare manualmente o configurare IIS o il debugger remoto (questi componenti sono rappresentati con linee tratteggiate), come illustrato nella figura seguente.

    ![I componenti del debugger remoto](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Per eseguire il debug di IIS su una macchina virtuale di Azure, attenersi alla procedura descritta in questo argomento (vedere la sezione [eseguire il Debug remoto in una macchina virtuale di Azure](#remote_debug_azure_vm)). In questo modo è possibile utilizzare una configurazione personalizzata di IIS, ma i passaggi di installazione e distribuzione sono più complessi.

    Per una macchina virtuale di Azure, è necessario distribuire l'app da Visual Studio in Azure ed è inoltre necessario installare manualmente il ruolo IIS e il debugger remoto, come illustrato nella figura seguente.

    ![I componenti del debugger remoto](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Per eseguire il debug ASP.NET Core in Azure Service Fabric, vedere [Debug di un'applicazione di Service Fabric remota](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Assicurarsi di eliminare le risorse di Azure che crei dopo aver completato i passaggi in questa esercitazione. In questo modo che è possibile evitare di incorrere in costi non necessari.


### <a name="requirements"></a>Requisiti

Il debug tra due computer connessi tramite un proxy non è supportato. Il debug tramite una connessione di larghezza di banda ridotta, ad esempio di connessione remota a Internet, ad alta latenza o tramite Internet tra paesi non è consigliato e potrebbe non funzionare oppure essere inaccettabile. Per un elenco completo dei requisiti, vedere [requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Creare l'applicazione ASP.NET Core nel computer di Visual Studio 2017 

1. Creare una nuova applicazione ASP.NET Core. (Scegliere **File > Nuovo > progetto**, quindi selezionare **Visual c# > Web > applicazione Web di ASP.NET Core**).

    Nel **ASP.NET Core** sezione modelli, selezionare **applicazione Web**.

2. Assicurarsi che **ASP.NET Core 2.0** è selezionata, che **Attiva supporto Docker** è **non** selezionata e che **autenticazione** è impostato su **Nessuna autenticazione**.

3. Denominare il progetto **MyASPApp** e fare clic su **OK** per creare la nuova soluzione.

4. Aprire il file About.cshtml.cs e impostare un punto di interruzione nella `OnGet` (metodo) (nei modelli meno recenti, aprire HomeController.cs invece e impostare il punto di interruzione nel `About()` (metodo)).

## <a name="remote_debug_azure_app_service"></a> Eseguire il Debug remoto di ASP.NET Core in un servizio App di Azure

Da Visual Studio, è possibile pubblicare rapidamente e debug dell'app a un'istanza di IIS completo. Tuttavia, la configurazione di IIS è preimpostata e non è possibile personalizzare. Per istruzioni dettagliate, vedere [distribuire un'app web ASP.NET Core in Azure utilizzando Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Se è necessario il possibilità di personalizzare IIS, provare a debug un [macchina virtuale di Azure](#BKMK_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Per distribuire l'app ed eseguire il debug remoto tramite Esplora Server

1. In Visual Studio, fare doppio clic sul nodo del progetto e scegliere **pubblica**.

    Se in precedenza è stato configurato alcun profilo di pubblicazione, il **pubblica** viene visualizzato il riquadro. Fare clic su **nuovo profilo**.

1. Scegliere **Azure App Service** dal **pubblica** finestra di dialogo **Crea nuovo**e seguire le istruzioni per la pubblicazione.

    Per istruzioni dettagliate, vedere [distribuire un'app web ASP.NET Core in Azure utilizzando Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Eseguire la pubblicazione nel servizio app di Azure](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Aprire **Esplora Server** (**vista** > **Esplora Server**), fare doppio clic sull'istanza del servizio App e scegliere **collega Debugger**.

1. Nell'applicazione ASP.NET in esecuzione, fare clic sul collegamento per il **su** pagina.

    Il punto di interruzione verrà raggiunto in Visual Studio.

    La procedura è terminata. Il resto dei passaggi in questo argomento si applicano al debug remoto in una macchina virtuale di Azure.

## <a name="remote_debug_azure_vm"></a> Eseguire il Debug remoto ASP.NET Core in una macchina virtuale di Azure

È possibile creare una macchina virtuale di Azure per Windows Server e quindi installare e configurare IIS e gli altri componenti software necessari. Questo richiede più tempo rispetto alla distribuzione a un servizio App di Azure è necessario seguire i passaggi rimanenti in questa esercitazione.

In primo luogo, seguire i passaggi descritti [installazione e l'esecuzione di IIS](/azure/virtual-machines/windows/quick-create-portal).

Anche quando si apre la porta 80 nel gruppo di sicurezza di rete, aprire la porta 4022 per il Debugger remoto. In questo modo, non è necessario aprirlo in un secondo momento.

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>App già in esecuzione in IIS sulla macchina virtuale Azure?

In questo articolo include i passaggi per la configurazione di una configurazione di base di IIS in Windows server e distribuzione dell'app da Visual Studio. Questi passaggi sono inclusi per assicurarsi che il server disponga dei componenti necessari installati, che l'app può essere eseguito correttamente e che si è pronti per eseguire il debug remoto.

* Se l'app è in esecuzione in IIS e si desidera scaricare il debugger remoto, avviare il debug, visitare [scaricare e installare remote tools in Windows Server](#BKMK_msvsmon).

* Se si desidera visualizzare la Guida per assicurarsi che l'app è configurato, distribuito e in esecuzione correttamente in IIS in modo che è possibile eseguire il debug, seguono tutti i passaggi descritti in questo argomento.

### <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se sicurezza avanzata è abilitata in Internet Explorer (è abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per consentire il download alcuni dei componenti server web. Aggiungere siti attendibili, passare a **Opzioni Internet > sicurezza > siti attendibili > siti**. Aggiungere i seguenti domini.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Quando si scarica il software, è possibile ricevere le richieste per concedere autorizzazioni per caricare vari script del sito web e risorse. Alcune di queste risorse non sono necessarie, ma per semplificare il processo, fare clic su **Aggiungi** quando richiesto.

### <a name="install-aspnet-core-on-windows-server"></a>Installare ASP.NET Core in Windows Server

1. Installare il [.NET Core Windows Server che ospita](https://aka.ms/dotnetcore-2-windowshosting) bundle nel sistema host. Il pacchetto verrà installato il Runtime di .NET Core, libreria di base .NET e il modulo di base di ASP.NET. Per altre istruzioni dettagliate, vedere [la pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Se il sistema non dispone di una connessione a Internet, ottenere e installare il *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* prima di installare il bundle di Hosting di .NET Core Windows Server.

3. Riavviare il sistema (o eseguire **net stop stato /y** seguito da **net start w3svc** da un prompt dei comandi per visualizzare una modifica al percorso di sistema).

## <a name="choose-a-deployment-option"></a>Scegliere un'opzione di distribuzione

Se è necessario consentono di distribuire l'app a IIS, prendere in considerazione queste opzioni:

* Distribuire mediante la creazione di un file di impostazioni di pubblicazione in IIS e importazione delle impostazioni di Visual Studio. In alcuni scenari, questo è un modo rapido per distribuire l'app. Quando si crea il file di impostazioni di pubblicazione, le autorizzazioni vengono impostate automaticamente in IIS.

* Distribuire la pubblicazione in una cartella locale e copiando l'output da un metodo preferito in una cartella di app preparata in IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Facoltativo) Distribuire mediante un file di impostazioni di pubblicazione

È possibile utilizzare questa opzione Crea un file di impostazioni di pubblicazione e importarlo in Visual Studio.

> [!NOTE]
> Questo metodo di distribuzione utilizza distribuzione Web. Se si desidera configurare distribuzione Web manualmente in Visual Studio invece di importare le impostazioni, è possibile installare Web distribuire 3.6 anziché 3.6 distribuzione Web per i server di Hosting. Tuttavia, se si configura distribuzione Web manualmente, è necessario assicurarsi che una cartella di app nel server è configurata con i valori corretti e le autorizzazioni (vedere [sito Web ASP.NET configurare](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installare e configurare distribuzione Web per i server di Hosting in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Creare il file di impostazioni di pubblicazione in IIS in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Dopo che l'app viene distribuito correttamente, verrà avviato automaticamente. Se non si avvia l'app da Visual Studio, avviare l'app in IIS. Per ASP.NET Core, è necessario assicurarsi che il pool di applicazioni di campo per il **DefaultAppPool** è impostata su **nessun codice gestito**.

1. Nel **impostazioni** della finestra di dialogo Abilita debug facendo **successivo**, scegliere un **Debug** configurazione e quindi scegliere **Rimuovi file aggiuntivi nella destinazione** sotto la **pubblicare File** opzioni.

    > [!NOTE]
    > Se si sceglie una configurazione di rilascio, disabilitare il debug nel *Web. config* file quando si esegue la pubblicazione.

1. Fare clic su **salvare** e quindi pubblicare di nuovo l'app.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Facoltativo) Distribuire mediante la pubblicazione in una cartella locale

È possibile utilizzare questa opzione per distribuire l'app se si desidera copiare l'app a IIS tramite Powershell, RoboCopy, o si desidera copiare manualmente i file.

### <a name="BKMK_deploy_asp_net"></a> Configurare il sito Web di ASP.NET sul computer del Server di Windows

Se si sta importando le impostazioni di pubblicazione, è possibile ignorare questa sezione.

1. Aprire **Gestione Internet Information Services (IIS)** e andare in **Siti**.

2. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

3. Impostare il **Alias** campo **MyASPApp** e il campo pool di applicazioni per **nessun codice gestito**. Impostare il **percorso fisico** a **C:\Publish** (in cui in un secondo momento verrà distribuito il progetto ASP.NET).

4. Con il sito selezionato in Gestione IIS, scegliere **Modifica autorizzazioni**e assicurarsi che tale account IUSR, IIS_IUSRS o l'utente configurato per il Pool di applicazioni è un utente autorizzato con diritti di lettura ed esecuzione.

    Se non viene visualizzato uno di questi utenti con accesso, eseguire passaggi per aggiungere IUSR come utente con diritti di lettura ed esecuzione.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Facoltativo) Pubblicare e distribuire l'app mediante la pubblicazione in una cartella locale da Visual Studio

Se non si utilizza distribuzione Web, è necessario pubblicare e distribuire l'app utilizzando il file system o altri strumenti. È possibile iniziare creando un pacchetto utilizzando il file system e quindi distribuirlo manualmente o utilizzare altri strumenti come XCopy, RoboCopy o PowerShell. In questa sezione si presuppone che si sta copiando manualmente il pacchetto se non si utilizza distribuzione Web.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Scaricare e installare remote tools in Windows Server

In questa esercitazione, si utilizza Visual Studio 2017.

Nel caso di problemi durante l'apertura della pagina con il download del debugger remoto, vedere [sbloccare il download del file](../debugger/remote-debugging.md#unblock_msvsmon) per assistenza.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Impostare il debugger remoto in Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere le autorizzazioni per altri utenti, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [configurare il debugger remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Connettersi all'applicazione ASP.NET dal computer di Visual Studio

1. Nel computer di Visual Studio, aprire il **MyASPApp** soluzione.
2. In Visual Studio, fare clic su **Debug > Connetti a processo** (Ctrl + Alt + P).

    > [!TIP]
    > In Visual Studio 2017, è possibile ricollegare allo stesso processo in precedenza associato a tramite **Debug > riconnettersi al processo...** (Maiusc + Alt + P). 

3. Impostare il campo qualificatore su  **\<nome del computer remoto >: 4022**.
4. Fare clic su **Aggiorna**.
    Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.

    Se eventuali processi non viene visualizzato, provare a usare l'indirizzo IP anziché il nome del computer remoto (la porta è obbligatoria). È possibile utilizzare `ipconfig` in una riga di comando per ottenere l'indirizzo IPv4.

    Se si desidera utilizzare il **trovare** pulsante, potrebbe essere necessario [aprire la porta UDP 3702](#bkmk_openports) sul server.

5. Selezionare  **Mostra i processi di tutti gli utenti**.

6. Digitare la prima lettera del nome di un processo per trovare rapidamente *dotnet.exe* (per ASP.NET Core).
   
   Per un'app di ASP.NET Core, il nome del processo precedente è stata *dnx.exe*.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Scegliere **Connetti**.

8. Aprire il sito Web del computer remoto. In un browser, passare a **http://\<nome del computer remoto >**.
    
    Verrà visualizzata la pagina Web ASP.NET.
9. Nell'applicazione ASP.NET in esecuzione, fare clic sul collegamento per il **su** pagina.

    Il punto di interruzione verrà raggiunto in Visual Studio.

### <a name="bkmk_openports"></a> Risoluzione dei problemi: Aprire le porte necessarie in Windows Server

Nella maggior parte delle installazioni, vengono aperte le porte richieste dall'installazione di ASP.NET e il debugger remoto. Tuttavia, se si siano risolvendo i problemi di distribuzione e l'app si trova dietro un firewall, potrebbe essere necessario verificare che le porte appropriate siano aperte.

In una macchina virtuale di Azure, è necessario aprire porte tramite il [il gruppo di sicurezza di rete](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Porte richieste:

- 80 - necessari per IIS
- 4022 - necessari per il debug remoto da Visual Studio 2017 (vedere [assegnazioni di porta del Debugger remoto](../debugger/remote-debugger-port-assignments.md) per altre informazioni).
- UDP 3702 - Discovery (facoltativo) porta consente del **trovare** pulsante quando ci si connette al debugger remoto in Visual Studio.

Inoltre, queste porte devono già essere aperti dall'installazione di ASP.NET:
- 8172 - (facoltativo) necessarie per la distribuzione Web distribuire l'app da Visual Studio

