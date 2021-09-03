---
title: Debug remoto ASP.NET Core in IIS e Azure | Microsoft Docs
description: Informazioni su come configurare un'app Visual Studio ASP.NET Core, distribuirla in IIS usando Azure e collegare il debugger remoto da Visual Studio.
ms.custom: remotedebugging
ms.date: 08/27/2021
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: d4b33cb34472ddcec6869075bdb055e3551ec0fe
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398691"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Debug remoto ASP.NET Core in IIS in Azure in Visual Studio

Questa guida illustra come configurare e configurare un'app Visual Studio ASP.NET Core, distribuirla in IIS usando Azure e collegare il debugger remoto da Visual Studio.

Il modo consigliato per eseguire il debug remoto in Azure dipende dallo scenario:

* Per eseguire il debug ASP.NET Core in Servizio app di Azure, vedere [Eseguire il debug di app di Azure usando il Snapshot Debugger](../debugger/debug-live-azure-applications.md). Questo è il metodo consigliato.
* Per eseguire il debug ASP.NET Core in Servizio app di Azure usando funzionalità di debug più tradizionali, seguire i passaggi descritti in questo argomento (vedere la sezione Debug remoto [in Servizio app di Azure](#remote_debug_azure_app_service)).

    In questo scenario è necessario distribuire l'app da Visual Studio ad Azure, ma non è necessario installare o configurare manualmente IIS o il debugger remoto (questi componenti sono rappresentati da linee tratteggiate), come illustrato nella figura seguente.

    ![Diagramma che illustra la relazione tra Visual Studio, Servizio app di Azure e un'app ASP.NET app. IIS e Il debugger remoto sono rappresentati da linee tratteggiate.](../debugger/media/remote-debugger-azure-app-service.png)

* Per eseguire il debug di IIS in una macchina virtuale di Azure, seguire la procedura descritta in questo argomento (vedere la sezione [Debug remoto in una macchina virtuale di Azure).](#remote_debug_azure_vm) In questo modo è possibile usare una configurazione personalizzata di IIS, ma i passaggi di installazione e distribuzione sono più complessi.

    Per una macchina virtuale di Azure, è necessario distribuire l'app da Visual Studio ad Azure ed è anche necessario installare manualmente il ruolo IIS e il debugger remoto, come illustrato nella figura seguente.

    ![Diagramma che illustra la relazione tra Visual Studio, una macchina virtuale di Azure e un ASP.NET app. IIS e Remote Debugger sono rappresentati con linee a tinta unita.](../debugger/media/remote-debugger-azure-vm.png)

* Per eseguire il debug ASP.NET Core in Azure Service Fabric, vedere [Eseguire il debug di un'Service Fabric remota](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Assicurarsi di eliminare le risorse di Azure create dopo aver completato i passaggi di questa esercitazione. In questo modo è possibile evitare di incorrere in addebiti non necessari.

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"
Visual Studio 2019 è necessario per seguire la procedura illustrata in questo articolo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 è necessario per seguire la procedura illustrata in questo articolo.
::: moniker-end

### <a name="network-requirements"></a>Requisiti di rete

Il debug tra due computer connessi tramite un proxy non è supportato. Non è consigliabile eseguire il debug su una connessione a latenza elevata o a larghezza di banda ridotta, ad esempio una connessione remota a Internet o su Internet tra paesi diversi, che potrebbe avere esito negativo o essere inaccettabilmente lenta. Per un elenco completo dei requisiti, vedere [Requisiti.](../debugger/remote-debugging.md#requirements_msvsmon)

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Creare l ASP.NET Core app applicazione nel computer Visual Studio

1. Creare una nuova applicazione Web ASP.NET Core.

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 scegliere **Crea un nuovo progetto** nella finestra iniziale. Se la finestra iniziale non è aperta, scegliere **Finestra**  >  **iniziale file**. Digitare **app Web,** scegliere **C#** come linguaggio, quindi ASP.NET Core **Applicazione Web (Model-View-Controller)** e infine **scegliere Avanti.** Nella schermata successiva assegnare al progetto il **nome MyASPApp** e quindi scegliere **Avanti.**

    Scegliere il framework di destinazione consigliato (.NET Core 3.1) o .NET 5 e quindi scegliere **Crea.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 scegliere **File > Nuovo > Project**, quindi selezionare **Visual C# > Web > ASP.NET Core Web Application**. Nella sezione ASP.NET Core modelli selezionare **Applicazione Web (Model-View-Controller).** Assicurarsi che sia ASP.NET Core 2.1, che l'opzione Abilita supporto  **Docker** non sia selezionata e che l'opzione Autenticazione sia impostata su **Nessuna autenticazione**. Assegnare al progetto **il nome MyASPApp**.
    ::: moniker-end

1. Aprire il file About.cshtml.cs e impostare un punto di interruzione nel metodo . Nei modelli precedenti aprire invece HomeController.cs e impostare il punto di `OnGet` interruzione nel `About()` metodo .

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a>Debug remoto ASP.NET Core in un Servizio app di Azure

Da Visual Studio è possibile pubblicare rapidamente l'app ed eseguirne il debug in un'istanza di IIS con provisioning completo. Tuttavia, la configurazione di IIS è preimpostato e non è possibile personalizzarla. Per istruzioni più dettagliate, vedere [Distribuire un'app Web ASP.NET Core in Azure usando Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Se è necessario personalizzare IIS, provare a eseguire il debug in una macchina [virtuale di Azure.](#remote_debug_azure_vm)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Per distribuire l'app e il debug remoto usando Cloud Explorer

1. In Visual Studio fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Pubblica.**

    Se sono stati configurati dei profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. Selezionare Nuovo **o** **Nuovo profilo.**

1. Creare un nuovo profilo di pubblicazione.

    ::: moniker range=">=vs-2019"
    Scegliere **Azure** nella finestra **di dialogo** Pubblica e selezionare **Avanti.** Scegliere quindi **Servizio app di Azure (Windows)**, selezionare **Avanti** e seguire le istruzioni per creare un profilo.

    :::image type="content" source="../debugger/media/vs-2019/remotedbg-azure-app-service-profile.png" alt-text="Distribuire un'app Web ASP.NET Core in Azure con Visual Studio":::
    ::: moniker-end
    ::: moniker range="vs-2017"

    Scegliere **Servizio app di Azure** nella **finestra di dialogo** Pubblica, selezionare **Crea** nuovo e seguire le istruzioni per creare un profilo.

    ![Eseguire la pubblicazione nel servizio app di Azure](../debugger/media/remotedbg_azure_app_service_profile.png)
    ::: moniker-end

    Per istruzioni più dettagliate, vedere [Distribuire un'app Web ASP.NET Core in Azure usando Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

1. Nella finestra Pubblica scegliere **Modifica** configurazione e passare a una configurazione di debug e quindi scegliere **Pubblica.**

   Per eseguire il debug dell'app è necessaria una configurazione di debug.

1. Aprire **Cloud Explorer** (**Visualizza Cloud Explorer**), fare clic con il pulsante destro del mouse sull'istanza del servizio app e scegliere Collega  >   **debugger**.

   Se Cloud Explorer non è disponibile, aprire Esplora server. Fare quindi clic con il pulsante destro del mouse sull'istanza del servizio app in Esplora server scegliere **Collega debugger**.

1. Nell'applicazione ASP.NET in esecuzione fare clic sul collegamento alla **pagina** Informazioni su .

    Il punto di interruzione verrà raggiunto in Visual Studio.

    Questo è tutto. I passaggi rimanenti di questo argomento si applicano al debug remoto in una macchina virtuale di Azure.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a>Eseguire il debug ASP.NET Core remoto in una macchina virtuale di Azure

È possibile creare una macchina virtuale di Azure per Windows Server e quindi installare e configurare IIS e gli altri componenti software necessari. Questa operazione richiede più tempo rispetto alla distribuzione in un Servizio app di Azure e richiede di seguire i passaggi rimanenti di questa esercitazione.

Queste procedure sono state testate in queste configurazioni del server:

* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10
* Windows Server 2019 e IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>App già in esecuzione in IIS nella macchina virtuale di Azure?

Questo articolo include i passaggi per configurare una configurazione di base di IIS Windows server e distribuire l'app da Visual Studio. Questi passaggi sono inclusi per assicurarsi che nel server siano installati i componenti necessari, che l'app possa essere eseguita correttamente e che si sia pronti per il debug remoto.

* Se l'app è in esecuzione in IIS e si vuole solo scaricare il debugger remoto e avviare il debug, passare a Scaricare e installare gli strumenti remoti [in Windows Server.](#BKMK_msvsmon)

* Per assicurarsi che l'app sia configurata, distribuita ed eseguita correttamente in IIS in modo da poter eseguire il debug, seguire tutti i passaggi descritti in questo argomento.

  * Prima di iniziare, seguire tutti i passaggi descritti [in](/azure/virtual-machines/windows/quick-create-portal)Creare una Windows virtuale, che include i passaggi per installare il server Web IIS.

  * Assicurarsi di aprire la porta 80 nel gruppo di sicurezza [di rete di](/azure/virtual-machines/windows/nsg-quickstart-portal)Azure . Quando si verifica che la porta 80 sia aperta, aprire anche la porta [corretta](#bkmk_openports) per il debugger remoto (4024 o 4022). In questo modo, non sarà necessario aprirlo in un secondo momento. Se si usa la Distribuzione Web, aprire anche la porta 8172.

### <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser Windows Server

Se la configurazione della sicurezza avanzata è abilitata in Internet Explorer (abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per consentire il download di alcuni componenti del server Web. Aggiungere i siti attendibili selezionando Opzioni **Internet > Sicurezza > siti > attendibili**. Aggiungere i domini seguenti.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Quando si scarica il software, è possibile che si otterrà una richiesta di concessione dell'autorizzazione per caricare vari script e risorse del sito Web. Alcune di queste risorse non sono necessarie, ma per semplificare il processo, fare clic **su Aggiungi** quando richiesto.

### <a name="install-aspnet-core-on-windows-server"></a>Installare ASP.NET Core in Windows Server

1. Installare il bundle di hosting .NET Core nel sistema di hosting. L'aggregazione installa il runtime di .NET Core, la libreria di .NET Core e il modulo ASP.NET Core. Per istruzioni più dettagliate, vedere [Pubblicazione in IIS.](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)

    Per il bundle di hosting .NET Core corrente, installare il bundle [di hosting ASP.NET Core.](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer)
    Per .NET Core 2, installare [.NET Core Windows Server che ospita](https://aka.ms/dotnetcore-2-windowshosting).

    > [!NOTE]
    > Se nel sistema non è presente una connessione a Internet, ottenere e installare *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* prima di installare l'aggregazione di Hosting di .NET Core Windows Server.

2. Riavviare il sistema o eseguire **net stop was /y** seguito da **net start w3svc** da un prompt dei comandi per visualizzare una modifica al percorso di sistema.

## <a name="choose-a-deployment-option"></a>Scegliere un'opzione di distribuzione

Se è necessaria assistenza per distribuire l'app in IIS, prendere in considerazione queste opzioni:

* Distribuire creando un file di impostazioni di pubblicazione in IIS e importando le impostazioni in Visual Studio. In alcuni scenari si tratta di un modo rapido per distribuire l'app. Quando si crea il file di impostazioni di pubblicazione, le autorizzazioni vengono impostate automaticamente in IIS.

* Eseguire la distribuzione pubblicando in una cartella locale e copiando l'output con un metodo preferito in una cartella dell'app preparata in IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Facoltativo) Eseguire la distribuzione usando un file di impostazioni di pubblicazione

È possibile usare questa opzione per creare un file di impostazioni di pubblicazione e importarlo Visual Studio.

> [!NOTE]
> Questo metodo di distribuzione Distribuzione Web, che deve essere installato nel server. Se si vuole configurare manualmente Distribuzione Web anziché importare le impostazioni, è possibile installare Distribuzione Web 3.6 anziché Distribuzione Web 3.6 per i server di hosting. Tuttavia, se si configura Distribuzione Web manualmente, è necessario assicurarsi che una cartella dell'app nel server sia configurata con i valori e le autorizzazioni corretti (vedere Configurare un sito Web di [ASP.NET](#BKMK_deploy_asp_net)).

### <a name="configure-the-aspnet-core-web-site"></a>Configurare il ASP.NET Core Web

1. In Gestione IIS, nel riquadro sinistro in **Connessioni** selezionare **Pool di applicazioni.** Aprire **DefaultAppPool** e impostare la **versione clr di .NET** su Nessun codice **gestito.** Questa operazione è necessaria per ASP.NET Core. Il sito Web predefinito usa DefaultAppPool.

2. Arrestare e riavviare DefaultAppPool.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installare e configurare i Distribuzione Web per l'hosting di server in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Creare il file delle impostazioni di pubblicazione in IIS in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

> [!NOTE]
> Se si riavvia una macchina virtuale di Azure, l'indirizzo IP potrebbe cambiare.

Quando la distribuzione è completata, l'app viene avviata automaticamente. Se l'app non viene avviata da Visual Studio, avviare l'app in IIS per verificare che venga eseguita correttamente. Per ASP.NET Core, è anche necessario assicurarsi che il campo Pool di applicazioni per **DefaultAppPool** sia impostato su **Nessun codice gestito.**

1. Nella  finestra **Impostazioni** debug, abilitare il debug facendo clic su Avanti , scegliere una configurazione di **debug** e quindi scegliere Rimuovi file aggiuntivi nella destinazione nelle **opzioni Pubblicazione** file. 

    > [!IMPORTANT]
    > Se si sceglie una configurazione versione, il debug viene disabilitato nel file *web.config* quando si esegue la pubblicazione.

1. Fare **clic su Salva** e quindi ripubblicare l'app.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Facoltativo) Eseguire la distribuzione pubblicando in una cartella locale

È possibile usare questa opzione per distribuire l'app se si vuole copiare l'app in IIS usando PowerShell, RoboCopy o copiare manualmente i file.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Configurare il ASP.NET Core Web nel computer Windows Server

Se si importano le impostazioni di pubblicazione, è possibile ignorare questa sezione.

1. Aprire **Gestione Internet Information Services (IIS)** e andare in **Siti**.

2. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

3. Impostare il **campo Alias** su **MyASPApp** e il campo Pool di applicazioni su **Nessun codice gestito.** Impostare **Percorso fisico su** **C:\Publish** (dove in seguito si distribuirà il ASP.NET Core progetto).

4. Con il sito selezionato in Gestione IIS, scegliere Modifica autorizzazioni e assicurarsi che IUSR, IIS_IUSRS o l'utente configurato per il pool di applicazioni sia un utente autorizzato con diritti di lettura & Esecuzione.

    Se uno di questi utenti non viene visualizzato con accesso, seguire la procedura per aggiungere IUSR come utente con diritti di lettura & Esecuzione.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Facoltativo) Pubblicare e distribuire l'app pubblicando in una cartella locale da Visual Studio

Se non si usa un Distribuzione Web, è necessario pubblicare e distribuire l'app usando il file system o altri strumenti. È possibile iniziare creando un pacchetto usando il file system e quindi distribuire il pacchetto manualmente o usare altri strumenti come PowerShell, Robocopy o XCopy. In questa sezione si presuppone che si sta copiando manualmente il pacchetto se non si usa Distribuzione Web.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Scaricare e installare gli strumenti remoti in Windows Server

Scaricare la versione degli strumenti remoti corrispondente alla versione di Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Configurare il debugger remoto in Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere autorizzazioni per altri utenti, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [Configurare il debugger remoto.](../debugger/remote-debugging.md#configure_msvsmon)

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Connettersi all ASP.NET app applicazione dal computer Visual Studio

1. Nel computer Visual Studio aprire la soluzione di cui si sta tentando di eseguire il debug (**MyASPApp** se si stanno seguendo i passaggi descritti in questo articolo).
2. In Visual Studio fare clic su **Debug > Collega a processo** (CTRL+ALT+P).

    > [!TIP]
    > In Visual Studio 2017 e versioni successive è possibile riconllegare lo stesso processo a cui è stato precedentemente collegato usando Debug > Ricollegare a **processo...** (MAIUSC+ALT+P).

3. Impostare il campo Qualificatore **\<remote computer name>** su e premere **INVIO.**

    Verificare che Visual Studio la porta necessaria al nome del computer, visualizzato nel formato: **\<remote computer name> :p ort**

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 dovrebbe essere visualizzato **\<remote computer name> :4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 dovrebbe essere visualizzato **\<remote computer name> :4022**
    ::: moniker-end
    La porta è obbligatoria. Se il numero di porta non è visualizzato, aggiungerlo manualmente.

4. Fare clic su **Aggiorna**.
    Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.

    Se non viene visualizzato alcun processo, provare a usare l'indirizzo IP anziché il nome del computer remoto (la porta è obbligatoria). È possibile usare `ipconfig` in una riga di comando per ottenere l'indirizzo IPv4.

    Se si vuole usare il **pulsante** Trova, potrebbe essere necessario aprire la porta [UDP 3702](#bkmk_openports) nel server.

5. Selezionare  **Mostra i processi di tutti gli utenti**.

6. Digitare la prima lettera del nome del processo per trovare rapidamente l'app.

    * Se si usa il modello [di hosting in-process](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) in IIS, selezionare il **processo** diw3wp.execorretto. A partire da .NET Core 3, questa è l'impostazione predefinita.

    * In caso contrario, selezionare **dotnet.exe** processo. Questo è il modello di hosting out-of-process.

    Se sono presenti più processi che *w3wp.exe* o *dotnet.exe,* controllare la **colonna Nome** utente. In alcuni scenari la colonna **Nome utente mostra** il nome del pool di app, ad esempio IIS **APPPOOL\DefaultAppPool**. Se viene visualizzato il pool di app, ma non è univoco, creare un nuovo pool di app denominato per l'istanza dell'app di cui si vuole eseguire il debug e quindi è possibile trovarlo facilmente nella colonna Nome **utente.**

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Scegliere **Connetti**.

8. Aprire il sito Web del computer remoto. In un browser passare a **http:// \<remote computer name>**.

    Verrà visualizzata la pagina Web ASP.NET.
9. Nell'applicazione ASP.NET in esecuzione fare clic sul collegamento alla **pagina** Informazioni su .

    Il punto di interruzione verrà raggiunto in Visual Studio.

## <a name="troubleshooting-iis-deployment"></a>Risoluzione dei problemi relativi alla distribuzione di IIS

- Se non è possibile connettersi all'host usando il nome host, provare l'indirizzo IP.
- Assicurarsi che le porte necessarie siano aperte nel server remoto.
- Per ASP.NET Core, è necessario assicurarsi che il campo Pool di applicazioni per **DefaultAppPool** sia impostato su **Nessun codice gestito**.
- Verificare che la versione ASP.NET usata nell'app sia uguale a quella installata nel server. Per l'app, è possibile visualizzare e impostare la versione nella **pagina** Proprietà. Per impostare l'app su una versione diversa, è necessario installare tale versione.
- Se l'app ha tentato di aprire, ma viene visualizzato un avviso relativo al certificato, scegliere di considerare attendibile il sito. Se l'avviso è già stato chiuso, è possibile modificare il profilo di pubblicazione, un file *.pubxml, nel progetto e aggiungere l'elemento seguente (solo per test): `<AllowUntrustedCertificate>true</AllowUntrustedCertificate>`
- Se l'app non viene avviata da Visual Studio, avviare l'app in IIS per verificare che sia stata distribuita correttamente.
- Controllare la finestra Output in Visual Studio informazioni sullo stato e controllare i messaggi di errore.

### <a name="open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Aprire le porte necessarie in Windows Server

Nella maggior parte delle installazioni, le porte necessarie vengono aperte dall'installazione ASP.NET e dal debugger remoto. Tuttavia, se si stanno risoluzione dei problemi di distribuzione e l'app è ospitata dietro un firewall, potrebbe essere necessario verificare che le porte corrette siano aperte.

In una macchina virtuale di Azure è necessario aprire le porte tramite il [gruppo di sicurezza di rete](/azure/virtual-machines/windows/nsg-quickstart-portal).

Porte necessarie:

* 80 - Obbligatorio per IIS
::: moniker range=">=vs-2019"
* 4024 : obbligatorio per il debug remoto da Visual Studio 2019. Per altre informazioni, vedere Assegnazioni delle porte del [debugger](../debugger/remote-debugger-port-assignments.md) remoto.
::: moniker-end
::: moniker range="vs-2017"
* 4022 : obbligatorio per il debug remoto da Visual Studio 2017. Per altre informazioni, vedere Assegnazioni delle porte del [debugger](../debugger/remote-debugger-port-assignments.md) remoto.
::: moniker-end
* UDP 3702 : porta di individuazione  (facoltativa) consente di accedere al pulsante Trova quando ci si connette al debugger remoto in Visual Studio.

Inoltre, queste porte dovrebbero essere già aperte dal ASP.NET installazione:
- 8172 - (Facoltativo) Obbligatorio per Distribuzione Web distribuire l'app da Visual Studio
