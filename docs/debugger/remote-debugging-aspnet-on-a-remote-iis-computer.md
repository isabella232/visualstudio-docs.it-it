---
title: Core di debug ASP.NET remoto in un computer IIS remoto Documenti Microsoft
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: b33ead969456935dab54c042ba4fbaf1f5ff44f4
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385473"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Remote Debug ASP.NET Core on a Remote IIS Computer in Visual Studio

Per eseguire il debug di un'applicazione ASP.NET Core distribuita in IIS, installare ed eseguire gli strumenti remoti nel computer in cui è stata distribuita l'app, quindi connettersi all'app in esecuzione da Visual Studio.

![Componenti del debugger remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

In questa guida viene illustrato come impostare e configurare un oggetto Visual Studio ASP.NET Core, distribuirlo in IIS e collegare il debugger remoto da Visual Studio. Per eseguire il debug remoto ASP.NET 4.5.2, vedere ASP.NET di [debug remoto in un computer IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). È anche possibile distribuire ed eseguire il debug in IIS usando Azure.You can also deploy and debug on IIS using Azure. Per il servizio app di Azure, è possibile distribuire ed eseguire facilmente il debug in un'istanza preconfigurata di IIS e del debugger remoto utilizzando il [debugger snapshot](../debugger/debug-live-azure-applications.md) o [collegando il debugger da Esplora server](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"
Visual Studio 2019 è necessario per seguire i passaggi illustrati in questo articolo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 è necessario per seguire i passaggi illustrati in questo articolo.
::: moniker-end

Queste procedure sono state testate su queste configurazioni server:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10

## <a name="network-requirements"></a>Requisiti di rete

Il debug tra due computer connessi tramite un proxy non è supportato. Il debug su una connessione ad alta latenza o a larghezza di banda ridotta, ad esempio Internet di connessione remota o tramite Internet in più paesi, non è consigliabile e potrebbe non riuscire o essere inaccettabilmente lento. Per un elenco completo dei requisiti, vedere [Requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>App già in esecuzione in IIS?

Questo articolo include la procedura per configurare una configurazione di base di IIS in Windows Server e distribuire l'app da Visual Studio. Questi passaggi sono inclusi per assicurarsi che nel server siano stati installati componenti necessari, che l'app possa essere eseguita correttamente e che si sia pronti per il debug remoto.

* Se l'app è in esecuzione in IIS e si desidera solo scaricare il debugger remoto e avviare il debug, passare a [Scaricare e installare gli strumenti remoti in Windows Server](#BKMK_msvsmon).

* Se vuoi assistenza per assicurarti che l'app sia configurata, distribuita e in esecuzione correttamente in IIS in modo da poter eseguire il debug, segui tutti i passaggi in questo argomento.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Creare l'applicazione ASP.NET Core nel computer Visual StudioCreate the ASP.NET Core application on the Visual Studio computer

1. Creare una nuova applicazione Web ASP.NET Core. 

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019, digitare **Ctrl e Q** per aprire la casella di ricerca, digitare **asp.net**, scegliere **Modelli**, quindi scegliere Crea nuova ASP.NET applicazione **Web principale**. Nella finestra di dialogo visualizzata assegnare al progetto il nome **MyASPApp**, quindi scegliere **Crea**. Scegliere quindi **Applicazione Web (Model-View-Controller)**, quindi **scegliere Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 scegliere **File > nuovo > progetto**, quindi selezionare Visual **C, > Web > ASP.NET applicazione Web di base**. Nella sezione modelli ASP.NET Core selezionare **Applicazione Web (Model-View-Controller)**. Assicurarsi che ASP.NET Core 2.1 sia selezionata, che **Abilita supporto Docker** non sia selezionato e che **Autenticazione** sia impostata su **Nessuna autenticazione**. Assegnare al progetto il nome **MyASPApp**.
    ::: moniker-end

4. Aprire il file di About.cshtml.cs `OnGet` e impostare un punto di interruzione nel `About()` metodo (nei modelli meno recenti aprire invece HomeController.cs e impostare il punto di interruzione nel metodo).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Installare e configurare IIS in Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se Protezione avanzata è abilitata in Internet Explorer (è abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per consentire il download di alcuni dei componenti del server Web. Aggiungere i siti attendibili accedendo a **Opzioni Internet > Protezione > siti attendibili > siti**attendibili . Aggiungere i domini seguenti.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Quando si scarica il software, è possibile ottenere richieste di concedere l'autorizzazione per caricare vari script e risorse del sito web. Alcune di queste risorse non sono necessarie, ma per semplificare il processo, fare clic su **Aggiungi** quando richiesto.

## <a name="install-aspnet-core-on-windows-server"></a>Installare ASP.NET Core in Windows Server

1. Installare l'[aggregazione di Hosting di.NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) nel sistema di hosting. L'aggregazione installa il runtime di .NET Core, la libreria di .NET Core e il modulo ASP.NET Core. Per istruzioni più approfondite, vedere [Pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

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

1. Aprire Esplora risorse e creare una nuova cartella, **C:,** in cui distribuire successivamente il progetto ASP.NET Core.

2. Se non è già aperto, aprire **Gestione Internet Information Services (IIS).** Nel riquadro sinistro di Server Manager selezionare **IIS.** Fare clic con il pulsante destro del mouse sul server e selezionare **Gestione Internet Information Services (IIS)**.

3. In **Connessioni** nel riquadro sinistro passare a **Siti**.

4. Selezionare il **sito Web predefinito**, scegliere Impostazioni di **base**e impostare il **percorso fisico** su **C:.**

4. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

5. Impostare il campo **Alias su** **MyASPApp**, accettare il pool di applicazioni predefinito (**DefaultAppPool**) e impostare il **percorso fisico su** **C:.**

6. In **Connessioni**selezionare **Pool di applicazioni**. Aprire **DefaultAppPool** e impostare il campo Pool di applicazioni **su Nessun codice gestito**.

7. Fare clic con il pulsante destro del mouse sul nuovo sito in Gestione IIS, scegliere **Modifica autorizzazioni**e verificare che IUSR, IIS_IUSRS o l'utente configurato per l'accesso all'app Web sia un utente autorizzato con diritti di lettura & esecuzione.

    Se uno di questi utenti non è presente con accesso, eseguire i passaggi per aggiungere IUSR come utente con diritti di lettura & esecuzione.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Pubblicare e distribuire l'app pubblicando in una cartella locale da Visual StudioPublish and Deploy the app by publishing to a local folder from Visual Studio

È inoltre possibile pubblicare e distribuire l'app utilizzando il file system o altri strumenti.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Scaricare e installare gli strumenti remoti in Windows Server

Scaricare la versione degli strumenti remoti corrispondente alla versione di Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Configurare il debugger remoto in Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere autorizzazioni per altri utenti, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [Configurare il debugger remoto](../debugger/remote-debugging.md#configure_msvsmon).

Per informazioni sull'esecuzione del debugger remoto come servizio, vedere [Eseguire il debugger remoto come servizio.](../debugger/remote-debugging.md#bkmk_configureService)

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Connettersi all'applicazione ASP.NET dal computer Visual Studio

1. Nel computer Visual Studio aprire la soluzione di cui si sta tentando di eseguire il debug (**MyASPApp** se si seguono tutti i passaggi descritti in questo articolo).
2. In Visual Studio, fare clic su **Debug > Connetti a processo** (CTRL e ALT ) .

    > [!TIP]
    > In Visual Studio 2017 e versioni successive, è possibile ricollegare allo stesso processo a cui ci si è connessi in precedenza utilizzando **Debug > Ricollega a processo...** (MAIUSC s z alt s'P).

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

    * Se si utilizza il modello di [hosting in-app in](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models) IIS, selezionare il processo **w3wp.exe** corretto. A partire da .NET Core 3, questa è l'impostazione predefinita.

    * In caso contrario, selezionare il processo **dotnet.exe.** (Questo è il modello di hosting out-of-process.)

    Se si dispone di più processi che mostrano *w3wp.exe* o *dotnet.exe*, controllare la colonna **Nome utente** . In alcuni scenari, nella colonna **Nome utente** viene visualizzato il nome del pool di applicazioni, ad esempio **IIS APPPOOL, DefaultAppPool**. Se viene visualizzato il pool di app, ma non è univoco, creare un nuovo pool di app denominato per l'istanza dell'app di cui si vuole eseguire il debug e quindi è possibile trovarlo facilmente nella colonna **Nome utente.**

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

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Risoluzione dei problemi Aprire le porte necessarie in Windows Server

Nella maggior parte delle configurazioni, le porte necessarie vengono aperte dall'installazione di ASP.NET e dal debugger remoto. Tuttavia, potrebbe essere necessario verificare che le porte siano aperte.

> [!NOTE]
> In una macchina virtuale di Azure è necessario aprire le porte tramite il [gruppo di sicurezza di rete.](/azure/virtual-machines/windows/nsg-quickstart-portal)

Porte richieste:

* 80 - Obbligatorio per IIS
::: moniker range=">=vs-2019"
* 4024 - Necessario per il debug remoto da Visual Studio 2019 (vedere [Assegnazioni di porte](../debugger/remote-debugger-port-assignments.md) del debugger remoto per ulteriori informazioni).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Necessario per il debug remoto da Visual Studio 2017 (vedere [Assegnazioni di porte](../debugger/remote-debugger-port-assignments.md) del debugger remoto per ulteriori informazioni).
::: moniker-end
* UDP 3702 - (porta di individuazione facoltativa) consente di fare clic sul pulsante **Trova** quando ci si connette al debugger remoto in Visual Studio.

1. Per aprire una porta in Windows Server, aprire il menu **Start,** cercare **Windows Firewall con sicurezza avanzata**.

2. Scegliere **quindi Regole in entrata > Nuova regola > Porta**, quindi fare clic su **Avanti**. Per UDP 3702, scegliere **Regole in uscita.**

3. In **Porte locali specifiche**immettere il numero di porta, quindi fare clic su **Avanti**.

4. Fare clic su **Consenti connessione**, quindi su **Avanti**.

5. Selezionare uno o più tipi di rete da abilitare per la porta e fare clic su **Avanti**.

    Il tipo selezionato deve includere la rete a cui è connesso il computer remoto.
6. Aggiungere il nome, ad esempio **IIS**, **Distribuzione Web**o **msvsmon**, per la regola in entrata e fare clic su **Fine**.

    La nuova regola dovrebbe comparire nell'elenco Regole in ingresso o Regole in uscita.

    Per ulteriori informazioni sulla configurazione di Windows Firewall, vedere [Configurare Windows Firewall per](../debugger/configure-the-windows-firewall-for-remote-debugging.md)il debug remoto .

3. Creare regole aggiuntive per le altre porte necessarie.
