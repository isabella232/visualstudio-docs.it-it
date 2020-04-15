---
title: ASP.NET di debug remoto in IIS e Azure . Documenti Microsoft
ms.custom: remotedebugging
ms.date: 04/14/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 079e324f2304118c9041118c13e8ebc0cce2015c
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385503"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>ASP.NET base di Debug remoto in IIS in Azure in Visual StudioRemote Debug ASP.NET Core on IIS in Azure in Visual Studio

Questa guida spiega come configurare e configurare un'app Visual Studio ASP.NET Core, distribuirla a IIS tramite Azure e collegare il debugger remoto da Visual Studio.This guide explains how to set up and configure a Visual Studio ASP.NET Core app, deploy it to IIS using Azure, and attach the remote debugger from Visual Studio.

Il modo consigliato per eseguire il debug remoto in Azure dipende dallo scenario:The recommended way to remote debug on Azure depends on your scenario:

* Per eseguire il debug di ASP.NET core nel servizio dell'app di Azure, vedere Debug di app di [Azure tramite il debugger snapshot.](../debugger/debug-live-azure-applications.md) Questo è il metodo consigliato.
* Per eseguire il debug di ASP.NET core nel servizio app di Azure usando funzionalità di debug più tradizionali, seguire i passaggi descritti in questo argomento (vedere la sezione Debug remoto nel servizio app di [Azure).](#remote_debug_azure_app_service)

    In questo scenario, è necessario distribuire l'app da Visual Studio ad Azure, ma non è necessario installare o configurare manualmente IIS o il debugger remoto (questi componenti sono rappresentati con linee tratteggiate), come illustrato nella figura seguente.

    ![Componenti del debugger remoto](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Per eseguire il debug di IIS in una macchina virtuale di Azure, seguire i passaggi descritti in questo argomento (vedere la sezione Debug remoto in una macchina virtuale di [Azure).](#remote_debug_azure_vm) In questo modo è possibile utilizzare una configurazione personalizzata di IIS, ma i passaggi di installazione e distribuzione sono più complessi.

    Per una macchina virtuale di Azure, è necessario distribuire l'app da Visual Studio ad Azure ed è inoltre necessario installare manualmente il ruolo IIS e il debugger remoto, come illustrato nella figura seguente.

    ![Componenti del debugger remoto](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Per eseguire il debug di ASP.NET Core in Azure Service Fabric, vedere [Debug di un'applicazione di Service Fabric remota.](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)

> [!WARNING]
> Assicurarsi di eliminare le risorse di Azure create dopo aver completato i passaggi di questa esercitazione. In questo modo è possibile evitare di incorrere in addebiti inutili.

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"
Visual Studio 2019 è necessario per seguire i passaggi illustrati in questo articolo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 è necessario per seguire i passaggi illustrati in questo articolo.
::: moniker-end

### <a name="network-requirements"></a>Requisiti di rete

Il debug tra due computer connessi tramite un proxy non è supportato. Il debug su una connessione a latenza elevata o a larghezza di banda ridotta, ad esempio Internet con connessione remota o tramite Internet in più paesi, non è consigliabile e potrebbe non riuscire o essere inaccettabilmente lento. Per un elenco completo dei requisiti, vedere [Requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Creare l'applicazione ASP.NET Core nel computer Visual StudioCreate the ASP.NET Core application on the Visual Studio computer

1. Creare una nuova applicazione ASP.NET Core.Create a new ASP.NET Core application.

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019, digitare **Ctrl e Q** per aprire la casella di ricerca, digitare **asp.net**, scegliere **Modelli**, quindi scegliere Crea nuova ASP.NET applicazione **Web principale**. Nella finestra di dialogo visualizzata assegnare al progetto il nome **MyASPApp**, quindi scegliere **Crea**. Scegliere quindi **Applicazione Web (Model-View-Controller)**, quindi **scegliere Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 scegliere **File > nuovo > progetto**, quindi selezionare Visual **C, > Web > ASP.NET applicazione Web di base**. Nella sezione modelli ASP.NET Core selezionare **Applicazione Web (Model-View-Controller)**. Assicurarsi che ASP.NET Core 2.1 sia selezionata, che **Abilita supporto Docker** non sia selezionato e che **Autenticazione** sia impostata su **Nessuna autenticazione**. Assegnare al progetto il nome **MyASPApp**.
    ::: moniker-end

1. Aprire il file di About.cshtml.cs `OnGet` e impostare un punto di interruzione nel `About()` metodo (nei modelli meno recenti aprire invece HomeController.cs e impostare il punto di interruzione nel metodo).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a>base del debug remoto in un servizio app di AzureRemote Debug ASP.NET Core on an Azure App Service

Da Visual Studio puoi pubblicare ed eseguire rapidamente il debug dell'app in un'istanza di IIS con provisioning completo. Tuttavia, la configurazione di IIS è preimpostata e non è possibile personalizzarla. Per istruzioni più dettagliate, vedere [Distribuire un'app Web ASP.NET Core in Azure con Visual Studio.](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs) Se è necessaria la possibilità di personalizzare IIS, provare a eseguire il debug in una macchina virtuale di [Azure.](#remote_debug_azure_vm)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Per distribuire l'app e il debug remoto con Cloud Explorer

1. In Visual Studio fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Pubblica**.

    Se sono stati configurati dei profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. Fare clic su **Nuovo profilo**.

1. Scegliere **Servizio app di Azure** nella finestra di dialogo **Pubblica** selezionare Crea **nuovo**e seguire le istruzioni visualizzate per creare un profilo.

    Per istruzioni dettagliate, vedere [Distribuire un'app Web ASP.NET Core in Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Pubblicare in Servizio app di Azure](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Nella finestra Pubblica scegliere **Modifica configurazione** e passare a una configurazione di debug, quindi **scegliere Pubblica**.

   Per eseguire il debug dell'app è necessaria una configurazione di debug.

1. Aprire **Cloud Explorer** (**Visualizza** > Cloud**Explorer**), fare clic con il pulsante destro del mouse sull'istanza del servizio app e scegliere Connetti **debugger**.

   Se Cloud Explorer non è disponibile, aprire Esplora server. Fare quindi clic con il pulsante destro del mouse sull'istanza del servizio app in Esplora server e scegliere **Connetti debugger**.

1. Nell'applicazione ASP.NET in esecuzione fare clic sul collegamento alla pagina **Informazioni su.**

    Il punto di interruzione verrà raggiunto in Visual Studio.

    L'operazione è terminata. The rest of the steps in this topic apply to remote debugging on an Azure VM.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a>Debug remoto ASP.NET Core in una macchina virtuale di AzureRemote Debug ASP.NET Core on an Azure VM

È possibile creare una macchina virtuale di Azure per Windows Server e quindi installare e configurare IIS e gli altri componenti software necessari. Questa operazione richiede più tempo rispetto alla distribuzione in un servizio app di Azure e richiede di seguire i passaggi rimanenti in questa esercitazione.

Queste procedure sono state testate su queste configurazioni server:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>App già in esecuzione in IIS nella macchina virtuale di Azure?

Questo articolo include la procedura per configurare una configurazione di base di IIS in Windows Server e distribuire l'app da Visual Studio. Questi passaggi sono inclusi per assicurarsi che nel server siano installati i componenti necessari, che l'app possa essere eseguita correttamente e che si sia pronti per il debug remoto.

* Se l'app è in esecuzione in IIS e si desidera solo scaricare il debugger remoto e avviare il debug, passare a [Scaricare e installare gli strumenti remoti in Windows Server](#BKMK_msvsmon).

* Se vuoi assistenza per assicurarti che l'app sia configurata, distribuita e in esecuzione correttamente in IIS in modo da poter eseguire il debug, segui tutti i passaggi in questo argomento.

  * Prima di iniziare, seguire tutti i passaggi descritti in [Installare ed eseguire IIS](/azure/virtual-machines/windows/quick-create-portal).

  * Quando si apre la porta 80 nel gruppo di sicurezza di rete, aprire anche la [porta corretta](#bkmk_openports) per il debugger remoto (4024 o 4022). In questo modo, non dovrai aprirlo più tardi.

### <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se Protezione avanzata è abilitata in Internet Explorer (è abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per consentire il download di alcuni dei componenti del server Web. Aggiungere i siti attendibili accedendo a **Opzioni Internet > Protezione > siti attendibili > siti**attendibili . Aggiungere i domini seguenti.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Quando si scarica il software, è possibile ottenere richieste di concedere l'autorizzazione per caricare vari script e risorse del sito web. Alcune di queste risorse non sono necessarie, ma per semplificare il processo, fare clic su **Aggiungi** quando richiesto.

### <a name="install-aspnet-core-on-windows-server"></a>Installare ASP.NET Core in Windows Server

1. Installare l'[aggregazione di Hosting di.NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) nel sistema di hosting. L'aggregazione installerà il Runtime di .NET Core, la libreria di .NET Core e il modulo di ASP.NET Core. Per istruzioni più approfondite, vedere [Pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Se nel sistema non è presente una connessione a Internet, ottenere e installare *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* prima di installare l'aggregazione di Hosting di .NET Core Windows Server.

3. Riavviare il sistema o eseguire **net stop was /y** seguito da **net start w3svc** da un prompt dei comandi per visualizzare una modifica al percorso di sistema.

## <a name="choose-a-deployment-option"></a>Scegliere un'opzione di distribuzione

Se hai bisogno di aiuto per distribuire l'app in IIS, prendi in considerazione le seguenti opzioni:

* Distribuire creando un file di impostazioni di pubblicazione in IIS e importando le impostazioni in Visual Studio.Deploy by creating a publish settings file in IIS and importing the settings in Visual Studio. In alcuni scenari, questo è un modo veloce per distribuire l'app. Quando si crea il file delle impostazioni di pubblicazione, le autorizzazioni vengono configurate automaticamente in IIS.

* Distribuire pubblicando in una cartella locale e copiando l'output tramite un metodo preferito in una cartella di app preparata in IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Facoltativo) Eseguire la distribuzione usando un file delle impostazioni di pubblicazioneDeploy using a publish settings file

È possibile utilizzare questa opzione per creare un file di impostazioni di pubblicazione e importarlo in Visual Studio.You can use this option create a publish settings file and import it into Visual Studio.

> [!NOTE]
> Questo metodo di distribuzione utilizza la distribuzione Web.This deployment method uses Web Deploy. Se si desidera configurare manualmente distribuzione Web in Visual Studio anziché importare le impostazioni, è possibile installare Distribuzione Web 3.6 anziché Distribuzione Web 3.6 per i server di hosting. Tuttavia, se si configura la distribuzione Web manualmente, sarà necessario assicurarsi che una cartella dell'app sul server sia configurata con i valori e le autorizzazioni corretti (vedere [Configurare ASP.NET sito Web](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installare e configurare La distribuzione Web per i server di hosting in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Creare il file delle impostazioni di pubblicazione in IIS in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Quando la distribuzione è completata, l'app viene avviata automaticamente. Se l'app non viene avviata da Visual Studio, avviarla in IIS. Per ASP.NET Core, è necessario assicurarsi che il campo Pool di applicazioni per **DefaultAppPool** sia impostato su **Nessun codice gestito**.

1. Nella finestra di dialogo **Impostazioni** abilitare il debug facendo clic su **Avanti**, scegliere una configurazione **di debug** e quindi scegliere Rimuovi file aggiuntivi **nella destinazione** nelle opzioni di **pubblicazione file.**

    > [!NOTE]
    > Se si sceglie una configurazione di rilascio, si disabilita il debug nel file *web.config* durante la pubblicazione.

1. Fare clic su **Salva** e quindi ripubblicare l'app.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Facoltativo) Distribuire mediante la pubblicazione in una cartella locale

È possibile usare questa opzione per distribuire l'app se si vuole copiare l'app in IIS usando PowerShell, RoboCopy o copiare manualmente i file.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Configurare il sito Web ASP.NET Core nel computer Windows Server

Se si importano le impostazioni di pubblicazione, è possibile ignorare questa sezione.

1. Aprire **Gestione Internet Information Services (IIS)** e andare in **Siti**.

2. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

3. Impostare il campo **Alias** su **MyASPApp** e il campo Pool di applicazioni su **Nessun codice gestito**. Impostare il **percorso fisico** su **C:: ,** in cui in seguito si distribuirà il progetto ASP.NET Core).

4. Con il sito selezionato in Gestione IIS, scegliere **Modifica autorizzazioni**e assicurarsi che IUSR, IIS_IUSRS o l'utente configurato per il pool di applicazioni sia un utente autorizzato con diritti di lettura & esecuzione.

    Se uno di questi utenti non è presente con accesso, eseguire i passaggi per aggiungere IUSR come utente con diritti di lettura & esecuzione.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Facoltativo) Pubblicare e distribuire l'app pubblicando in una cartella locale da Visual StudioPublish and Deploy the app by publishing to a local folder from Visual Studio

Se non si usa Distribuzione Web, è necessario pubblicare e distribuire l'app usando il file system o altri strumenti. È possibile iniziare creando un pacchetto usando il file system e quindi distribuire il pacchetto manualmente o usare altri strumenti come PowerShell, RoboCopy o XCopy.You can start by creating a package using the file system, and then either deploy the package manually or use other tools like PowerShell, RoboCopy, or XCopy. In questa sezione si presuppone che il pacchetto venga copiato manualmente se non si utilizza distribuzione Web.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Scaricare e installare gli strumenti remoti in Windows Server

Scaricare la versione degli strumenti remoti corrispondente alla versione di Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Configurare il debugger remoto in Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere autorizzazioni per altri utenti, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [Configurare il debugger remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Connettersi all'applicazione ASP.NET dal computer Visual Studio

1. Nel computer Visual Studio aprire la soluzione di cui si sta tentando di eseguire il debug (**MyASPApp** se si esegue la procedura descritta in questo articolo).
2. In Visual Studio, fare clic su **Debug > Connetti a processo** (CTRL e ALT ) .

    > [!TIP]
    > In Visual Studio 2017 e versioni successive, è possibile riconnettersi allo stesso processo a cui ci si è connessi in precedenza utilizzando **Debug > Ricollega a processo...** (MAIUSC .

3. Impostare il campo Qualificatore ** \<su nome computer remoto>** e premere **INVIO**.

    Verificare che Visual Studio aggiunga la porta richiesta al nome del computer, che viene visualizzato nel formato: ** \<nome computer remoto>:porta**

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019, si dovrebbe vedere ** \<il nome del computer remoto>:4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 dovrebbe essere visualizzato il nome del computer remoto>:4022On Visual Studio 2017, you should see ** \<remote computer name>:4022**
    ::: moniker-end
    La porta è obbligatoria. Se il numero di porta non viene visualizzato, aggiungerlo manualmente.

4. Fare clic su **Aggiorna**.
    Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.

    Se non viene visualizzato alcun processo, provare a utilizzare l'indirizzo IP anziché il nome del computer remoto (la porta è obbligatoria). È possibile `ipconfig` utilizzare in una riga di comando per ottenere l'indirizzo IPv4.

    Se si desidera utilizzare il pulsante **Trova,** potrebbe essere necessario aprire la [porta UDP 3702](#bkmk_openports) sul server.

5. Selezionare  **Mostra i processi di tutti gli utenti**.

6. Digita la prima lettera del nome del processo per trovare rapidamente la tua app.

    * Selezionare **dotnet.exe** (per .NET Core)

      Se si dispone di più processi che mostrano **dotnet.exe**, controllare la colonna **Nome utente** . In alcuni scenari, nella colonna **Nome utente** viene visualizzato il nome del pool di applicazioni, ad esempio **IIS APPPOOL, DefaultAppPool**. Se viene visualizzato il pool di applicazioni, un modo semplice per identificare il processo corretto consiste nel creare un nuovo pool di applicazioni denominato per l'istanza dell'app di cui si vuole eseguire il debug e quindi è possibile trovarlo facilmente nella colonna **Nome utente.**

    * In alcuni scenari IIS, è possibile trovare il nome dell'app nell'elenco dei processi, ad esempio **MyASPApp.exe**. È invece possibile connettersi a questo processo.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Scegliere **Connetti**.

8. Aprire il sito Web del computer remoto. In un browser passare a **http://\<nome computer remoto>**.

    Verrà visualizzata la pagina Web ASP.NET.
9. Nell'applicazione ASP.NET in esecuzione fare clic sul collegamento alla pagina **Informazioni su.**

    Il punto di interruzione verrà raggiunto in Visual Studio.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Risoluzione dei problemi Aprire le porte necessarie in Windows Server

Nella maggior parte delle configurazioni, le porte necessarie vengono aperte dall'installazione di ASP.NET e dal debugger remoto. Tuttavia, se si risolvi i problemi di distribuzione e l'app è ospitata dietro un firewall, potrebbe essere necessario verificare che le porte corrette siano aperte.

In una macchina virtuale di Azure è necessario aprire le porte tramite il [gruppo di sicurezza di rete.](/azure/virtual-machines/windows/nsg-quickstart-portal)

Porte richieste:

* 80 - Obbligatorio per IIS
::: moniker range=">=vs-2019"
* 4024 - Necessario per il debug remoto da Visual Studio 2019 (vedere [Assegnazioni di porte](../debugger/remote-debugger-port-assignments.md) del debugger remoto per ulteriori informazioni).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Necessario per il debug remoto da Visual Studio 2017 (vedere [Assegnazioni di porte](../debugger/remote-debugger-port-assignments.md) del debugger remoto per ulteriori informazioni).
::: moniker-end
* UDP 3702 - (porta di individuazione facoltativa) consente di fare clic sul pulsante **Trova** quando ci si connette al debugger remoto in Visual Studio.

Inoltre, queste porte dovrebbero già essere aperte dal ASP.NET installazione:
- 8172 - (Facoltativo) Obbligatorio per la distribuzione Web per distribuire l'app da Visual Studio
