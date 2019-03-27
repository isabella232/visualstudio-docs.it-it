---
title: Eseguire il Debug remoto di ASP.NET Core in IIS e Azure | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 694a9f7ba6bd5870a54b6b10e028c463d47ababf
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355802"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Eseguire il Debug remoto di ASP.NET Core in IIS in Azure in Visual Studio

Questa guida illustra come impostare e configurare un'app ASP.NET Core di Visual Studio e distribuirla in IIS usando Azure collega il debugger remoto da Visual Studio.

Il metodo consigliato per eseguire il debug remoto in Azure dipende dallo scenario:

* Per eseguire il debug di ASP.NET Core in servizio App di Azure, vedere [app di Azure di eseguire il Debug con il Debugger di Snapshot](../debugger/debug-live-azure-applications.md). Questo è il metodo consigliato.
* Per eseguire il debug di ASP.NET Core in servizio App di Azure con funzionalità di debug più tradizionale, attenersi alla procedura descritta in questo argomento (vedere la sezione [eseguire il debug remoto nel servizio App di Azure](#remote_debug_azure_app_service)).

    In questo scenario, è necessario distribuire l'app da Visual Studio in Azure ma non è necessario installare manualmente o configurare IIS o il debugger remoto (questi componenti sono rappresentati con le linee punteggiate), come illustrato nella figura seguente.

    ![Componenti del debugger remoto](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Per eseguire il debug di IIS in una VM di Azure, seguire questa procedura in questo argomento (vedere la sezione [eseguire il Debug remoto in una VM Azure](#remote_debug_azure_vm)). In questo modo è possibile usare una configurazione personalizzata di IIS, ma i passaggi di installazione e distribuzione sono più complessi.

    Per una macchina virtuale di Azure, è necessario distribuire l'app da Visual Studio in Azure ed è anche necessario installare manualmente il ruolo IIS e il debugger remoto, come illustrato nella figura seguente.

    ![Componenti del debugger remoto](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Per eseguire il debug di ASP.NET Core in Azure Service Fabric, vedere [eseguire il Debug di un'applicazione di Service Fabric remota](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Assicurarsi di eliminare le risorse di Azure creato dopo aver completato i passaggi descritti in questa esercitazione. In questo modo che è possibile evitare di incorrere in addebiti non necessari.

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"
Per seguire i passaggi illustrati in questo articolo è necessario Visual Studio 2019.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 è necessario attenersi alla procedura illustrata in questo articolo.
::: moniker-end

### <a name="network-requirements"></a>Requisiti di rete

Non è supportato tra due computer connessi tramite un proxy di debug. Debug tramite una latenza elevata o una connessione di larghezza di banda ridotta, ad esempio Internet, accesso remoto o la rete Internet tra paesi non è consigliabile e può avere esito negativo o essere inaccettabile. Per un elenco completo dei requisiti, vedere [requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Creare l'applicazione ASP.NET Core nel computer di Visual Studio

1. Creare una nuova applicazione ASP.NET Core.

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019, digitare **Ctrl + Q** per aprire la casella di ricerca, digitare **asp.net**, scegliere **modelli**, quindi scegliere **Crea nuova applicazione Web di ASP.NET Core** . Nella finestra di dialogo visualizzata, denominare il progetto **MyASPApp**, quindi scegliere **crea**. Scegliere quindi **applicazione Web (Model-View-Controller)**, quindi scegliere **crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017, scegliere **File > Nuovo > progetto**, quindi selezionare **Visual C# > Web > applicazione Web ASP.NET Core**. Nella sezione modelli ASP.NET Core, selezionare **applicazione Web (Model-View-Controller)**. Assicurarsi che sia selezionato ASP.NET Core 2.1, che **Abilita supporto Docker** non è selezionata e che **Authentication** è impostata su **Nessuna autenticazione**. Denominare il progetto **MyASPApp**.
    ::: moniker-end

1. Aprire il file About.cshtml.cs e impostare un punto di interruzione il `OnGet` (metodo) (in modelli precedenti, aprire HomeController.cs invece e impostare il punto di interruzione il `About()` (metodo)).

## <a name="remote_debug_azure_app_service"></a> Eseguire il Debug remoto di ASP.NET Core in servizio App di Azure

Da Visual Studio, è possibile pubblicare rapidamente e il debug dell'app a un'istanza di IIS con provisioning completo. Tuttavia, la configurazione di IIS è preimpostata e non è possibile personalizzare. Per istruzioni più dettagliate, vedere [distribuire un'app web ASP.NET Core in Azure usando Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Se è necessario avere la possibilità di personalizzare IIS, provare il debug in un' [macchina virtuale di Azure](#remote_debug_azure_vm).)

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Per distribuire l'app e il debug remoto tramite Esplora Server

1. In Visual Studio, fare doppio clic sul nodo del progetto e scegliere **pubblica**.

    Se sono stati configurati dei profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. Fare clic su **nuovo profilo**.

1. Scegliere **servizio App di Azure** dalle **Publish** nella finestra di dialogo **Crea nuovo**e seguire le istruzioni per la pubblicazione.

    Per istruzioni dettagliate, vedere [Distribuire un'app Web ASP.NET Core in Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Eseguire la pubblicazione nel servizio app di Azure](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Aprire **Esplora Server** (**View** > **Esplora Server**), fare doppio clic sull'istanza del servizio App e scegli **collega Debugger**.

1. Nell'applicazione ASP.NET in esecuzione, fare clic sul collegamento per il **sulle** pagina.

    Il punto di interruzione verrà raggiunto in Visual Studio.

    La procedura è terminata. Il resto dei passaggi in questo argomento si applicano al debug remoto in una VM di Azure.

## <a name="remote_debug_azure_vm"></a> Eseguire il Debug remoto di ASP.NET Core in una macchina virtuale di Azure

È possibile creare una macchina virtuale di Azure per Windows Server e quindi installare e configurare IIS e gli altri componenti software necessari. Questo richiede più tempo rispetto alla distribuzione di un servizio App di Azure e si è necessario seguire i passaggi rimanenti in questa esercitazione.

Queste procedure sono state testate in queste configurazioni di server:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Creare un'App già in esecuzione in IIS nella VM di Azure?

Questo articolo include i passaggi di configurazione di una configurazione di base di IIS in Windows server e la distribuzione dell'app da Visual Studio. Questi passaggi sono, per assicurarsi che il server ha i componenti richiesti installati, che l'app può essere eseguito correttamente e che si è pronti per eseguire il debug remoto.

* Se l'app è in esecuzione in IIS ed è sufficiente scaricare il debugger remoto e avviare il debug, passare a [scaricare e installare remote tools in Windows Server](#BKMK_msvsmon).

* Se si desidera visualizzare la Guida per assicurarsi che l'app è configurata, distribuzione e in esecuzione correttamente in IIS in modo che è possibile eseguire il debug, seguire tutti i passaggi descritti in questo argomento.

    * Prima di iniziare, seguire i passaggi descritti [installare e eseguire IIS](/azure/virtual-machines/windows/quick-create-portal).

    * Quando si apre la porta 80 nel gruppo di sicurezza di rete, anche aprire il [correggere porta](#bkmk_openports) per il debugger remoto (4024 o 4022). In questo modo, non è necessario aprirlo in un secondo momento.

### <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se sicurezza avanzata è abilitata in Internet Explorer (è abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per poter scaricare alcuni dei componenti server web. Aggiungere i siti attendibili scegliendo **Opzioni Internet > sicurezza > siti attendibili > siti**. Aggiungere i domini seguenti.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Quando si scarica il software, è possibile ricevere le richieste di concedere l'autorizzazione per caricare vari script del sito web e risorse. Alcune di queste risorse non sono necessarie, ma per semplificare il processo, fare clic su **Add** quando richiesto.

### <a name="install-aspnet-core-on-windows-server"></a>Installare ASP.NET Core in Windows Server

1. Installare l'[aggregazione di Hosting di.NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) nel sistema di hosting. L'aggregazione installerà il Runtime di .NET Core, la libreria di .NET Core e il modulo di ASP.NET Core. Per altre istruzioni dettagliate, vedere [pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Se nel sistema non è presente una connessione a Internet, ottenere e installare *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* prima di installare l'aggregazione di Hosting di .NET Core Windows Server.

3. Riavviare il sistema o eseguire **net stop was /y** seguito da **net start w3svc** da un prompt dei comandi per visualizzare una modifica al percorso di sistema.

## <a name="choose-a-deployment-option"></a>Scegliere un'opzione di distribuzione

Se si serve aiuto per distribuire l'app in IIS, prendere in considerazione queste opzioni:

* Distribuire mediante la creazione di un file di impostazioni di pubblicazione in IIS e importare le impostazioni in Visual Studio. In alcuni scenari, questo è un modo rapido per distribuire l'app. Quando si crea il file di impostazioni di pubblicazione, le autorizzazioni vengono impostate automaticamente in IIS.

* Distribuire la pubblicazione in una cartella locale e copiando l'output da un metodo preferito per una cartella preparata app in IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Facoltativo) Eseguire la distribuzione usando un file di impostazioni di pubblicazione

È possibile usare questa opzione Crea un file di impostazioni di pubblicazione e importarlo in Visual Studio.

> [!NOTE]
> Questo metodo di distribuzione Usa distribuzione Web. Se si desidera configurare distribuzione Web manualmente in Visual Studio invece di importare le impostazioni, è possibile installare Web distribuire 3.6 anziché 3.6 di distribuzione Web per i server di Hosting. Tuttavia, se si configura distribuzione Web manualmente, è necessario assicurarsi che una cartella dell'app nel server sia configurata con i valori corretti e le autorizzazioni (vedere [sito Web ASP.NET configurare](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installare e configurare distribuzione Web per i server di Hosting in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Creare il file delle impostazioni di pubblicazione in IIS in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Quando la distribuzione è completata, l'app viene avviata automaticamente. Se non si avvia l'app da Visual Studio, avviare l'app in IIS. Per ASP.NET Core, è necessario assicurarsi che il campo Pool di applicazioni per **DefaultAppPool** sia impostato su **Nessun codice gestito**.

1. Nel **le impostazioni** della finestra di dialogo Abilita il debug facendo clic **successivo**, scegliere un **Debug** configurazione e quindi scegliere **Rimuovi file aggiuntivi nella destinazione** sotto la **pubblicare File** opzioni.

    > [!NOTE]
    > Se si sceglie una configurazione di rilascio, si disabilita il debug nel *Web. config* file durante la pubblicazione.

1. Fare clic su **salvare** e quindi ripubblicare l'app.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Facoltativo) Distribuire mediante la pubblicazione in una cartella locale

È possibile usare questa opzione per distribuire l'app se si desidera copiare l'app a IIS tramite Powershell, RoboCopy o si desidera copiare manualmente i file.

### <a name="BKMK_deploy_asp_net"></a> Configurare il sito Web ASP.NET nel computer Windows Server

Se si sta importando le impostazioni di pubblicazione, è possibile ignorare questa sezione.

1. Aprire **Gestione Internet Information Services (IIS)** e andare in **Siti**.

2. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

3. Impostare il **Alias** campo **MyASPApp** e il campo di pool di applicazioni a **nessun codice gestito**. Impostare il **percorso fisico** al **C:\Publish** (in cui è in un secondo momento distribuirà il progetto ASP.NET).

4. Il sito selezionato in Gestione IIS, scegliere **Edit Permissions**e assicurarsi che tale account IUSR, IIS_IUSRS o l'utente sia configurato per il Pool di applicazioni è un utente autorizzato con diritti di lettura ed esecuzione.

    Se non viene visualizzato uno di questi utenti con accesso, eseguono passaggi per aggiungere IUSR come utente con diritti di lettura ed esecuzione.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Facoltativo) Pubblicare e distribuire l'app tramite la pubblicazione in una cartella locale da Visual Studio

Se non si usa distribuzione Web, è necessario pubblicare e distribuire l'app usando il file system o altri strumenti. È possibile iniziare creando un pacchetto con file system e quindi distribuire il pacchetto manualmente o usare altri strumenti, ad esempio XCopy, RoboCopy o PowerShell. In questa sezione si presuppone che si sta copiando manualmente il pacchetto se non si utilizza distribuzione Web.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Scaricare e installare remote tools in Windows Server

Scaricare la versione di remote tools corrispondente alla versione di Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a> Configurare il debugger remoto in Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere le autorizzazioni per altri utenti, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [configurare il debugger remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Connettersi all'applicazione ASP.NET dal computer di Visual Studio

1. Nel computer di Visual Studio, aprire la soluzione che si sta tentando di eseguire il debug (**MyASPApp** se si sta seguendo la procedura descritta in questo articolo).
2. In Visual Studio, fare clic su **Debug > Connetti a processo** (Ctrl + Alt + P).

    > [!TIP]
    > In Visual Studio 2017 e versioni successive, è possibile collegare nuovamente allo stesso processo è associato in precedenza usando **Debug > riassocia a processo...** MAIUSC+ALT+P

3. Impostare il campo qualificatore  **\<nome del computer remoto >: porta**.

    ::: moniker range=">=vs-2019"
    **\<nome del computer remoto >: 4024** Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **\<nome del computer remoto >: 4022** in Visual Studio 2017
    ::: moniker-end

4. Fare clic su **Aggiorna**.
    Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.

    Non vengono visualizzati tutti i processi, provare a usare l'indirizzo IP anziché il nome del computer remoto (la porta è obbligatoria). È possibile usare `ipconfig` in una riga di comando per ottenere l'indirizzo IPv4.

    Se si desidera utilizzare il **trovare** pulsante, potrebbe essere necessario [aprire la porta UDP 3702](#bkmk_openports) nel server.

5. Selezionare  **Mostra i processi di tutti gli utenti**.

6. Digitare la prima lettera del nome di un processo per trovare rapidamente *dotnet.exe* (per ASP.NET Core).

   Per un'app ASP.NET Core, il nome del processo precedente è stata *dnx.exe*.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Scegliere **Connetti**.

8. Aprire il sito Web del computer remoto. In un browser passare a **http://\<nome computer remoto>**.

    Verrà visualizzata la pagina Web ASP.NET.
9. Nell'applicazione ASP.NET in esecuzione, fare clic sul collegamento per il **sulle** pagina.

    Il punto di interruzione verrà raggiunto in Visual Studio.

### <a name="bkmk_openports"></a> Risoluzione dei problemi Aprire le porte necessarie in Windows Server

Nella maggior parte delle configurazioni, vengono aperte le porte richieste dall'installazione di ASP.NET e il debugger remoto. Tuttavia, se la risoluzione dei problemi di distribuzione e l'app è ospitata dietro un firewall, potrebbe essere necessario verificare che le porte appropriate siano aperte.

In una VM di Azure, è necessario aprire le porte attraverso il [gruppo di sicurezza di rete](/azure/virtual-machines/windows/nsg-quickstart-portal).

Porte necessarie:

* 80 - required per IIS
::: moniker range=">=vs-2019"
* 4024 - richiesto per il debug remoto da Visual Studio 2019 (vedere [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) per altre informazioni).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - richiesto per il debug remoto da Visual Studio 2017 (vedere [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) per altre informazioni).
::: moniker-end
* UDP 3702, porta di individuazione (facoltativo) consente il **trovare** pulsante quando ci si collega al debugger remoto in Visual Studio.

Inoltre, queste porte devono essere già aperta per l'installazione di ASP.NET:
- 8172 - (facoltativa) richiesta per la distribuzione Web per distribuire l'app da Visual Studio
