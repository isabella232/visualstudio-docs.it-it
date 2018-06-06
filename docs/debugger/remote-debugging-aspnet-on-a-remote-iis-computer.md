---
title: Eseguire il Debug remoto ASP.NET Core in un Computer remoto con IIS | Documenti Microsoft
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 607f4bb2bcce3d8895a4a07df8d70c866e7a6aab
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746930"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>Eseguire il Debug remoto di ASP.NET Core in un Computer remoto con IIS in Visual Studio 2017
Per eseguire il debug di un'applicazione ASP.NET che è stata distribuita a IIS, installare e quindi collegare all'App in esecuzione da Visual Studio eseguire remote tools sul computer in cui è distribuita l'app.

![I componenti del debugger remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Questa guida viene illustrato come impostare e configurare un Core di ASP.NET di Visual Studio 2017, distribuirlo in IIS e collegare il debugger remoto da Visual Studio. Eseguire il debug remoto ASP.NET 4.5.2, vedere [ASP.NET di eseguire il Debug remoto in un Computer IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). È anche possibile distribuire ed eseguire il debug in IIS utilizzando Azure. Per il servizio App di Azure, è possibile distribuire facilmente ed eseguire il debug in un'istanza preconfigurata di IIS e il debugger remoto utilizzando il [Debugger Snapshot](../debugger/debug-live-azure-applications.md) o [per collegare il debugger da Esplora Server](../debugger/remote-debugging-azure.md).

Queste procedure sono state testate su queste configurazioni del server:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10

## <a name="requirements"></a>Requisiti

Il debug tra due computer connessi tramite un proxy non è supportato. Il debug tramite una connessione di larghezza di banda ridotta, ad esempio di connessione remota a Internet, ad alta latenza o tramite Internet tra paesi non è consigliato e potrebbe non funzionare oppure essere inaccettabile. Per un elenco completo dei requisiti, vedere [requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>App già in esecuzione in IIS?

In questo articolo include i passaggi per la configurazione di una configurazione di base di IIS in Windows server e distribuzione dell'app da Visual Studio. Questi passaggi sono, per assicurarsi che il server ha necessari componenti installati, che l'app può essere eseguito correttamente e che si è pronti per eseguire il debug remoto.

* Se l'app è in esecuzione in IIS e si desidera scaricare il debugger remoto, avviare il debug, visitare [scaricare e installare remote tools in Windows Server](#BKMK_msvsmon).

* Se si desidera visualizzare la Guida per assicurarsi che l'app è configurato, distribuito e in esecuzione correttamente in IIS in modo che è possibile eseguire il debug, seguono tutti i passaggi descritti in questo argomento.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Creare l'applicazione ASP.NET Core nel computer di Visual Studio 2017 

1. Creare una nuova applicazione ASP.NET Core. (**File > Nuovo > progetto**, quindi selezionare **Visual c# > Web > applicazione Web di ASP.NET Core**).

    Nel **ASP.NET Core** sezione modelli, selezionare **applicazione Web**.

2. Assicurarsi che **ASP.NET Core 2.0** è selezionata, che **Attiva supporto Docker** è **non** selezionata e che **autenticazione** è impostato su **Nessuna autenticazione**.

3. Denominare il progetto **MyASPApp** e fare clic su **OK** per creare la nuova soluzione.

4. Aprire il file About.cshtml.cs e impostare un punto di interruzione nella `OnGet` (metodo) (nei modelli meno recenti, aprire HomeController.cs invece e impostare il punto di interruzione nel `About()` (metodo)).

## <a name="bkmk_configureIIS"></a> Installare e configurare IIS in Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se sicurezza avanzata è abilitata in Internet Explorer (è abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per consentire il download alcuni dei componenti server web. Aggiungere siti attendibili, passare a **Opzioni Internet > sicurezza > siti attendibili > siti**. Aggiungere i seguenti domini.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Quando si scarica il software, è possibile ricevere le richieste per concedere autorizzazioni per caricare vari script del sito web e risorse. Alcune di queste risorse non sono necessarie, ma per semplificare il processo, fare clic su **Aggiungi** quando richiesto.

## <a name="install-aspnet-core-on-windows-server"></a>Installare ASP.NET Core in Windows Server

1. Installare il [.NET Core Windows Server che ospita](https://aka.ms/dotnetcore-2-windowshosting) bundle nel sistema host. Installa il bundle di Runtime .NET Core, libreria di base .NET e il modulo di base di ASP.NET. Per altre istruzioni dettagliate, vedere [la pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

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

1. Aprire Esplora risorse e creare una nuova cartella **C:\Publish**, in cui verranno distribuiti in un secondo momento il progetto ASP.NET.

2. Se non è già aperto, aprire il **Internet Information Services (IIS) Manager**. (Nel riquadro sinistro di Server Manager, selezionare **IIS**. Il server e scegliere **Gestione Internet Information Services (IIS)**.)

3. In **connessioni** nel riquadro a sinistra, passare a **siti**.

4. Selezionare il **sito Web predefinito**, scegliere **le impostazioni di base**e impostare il **percorso fisico** a **C:\Publish**.

4. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

5. Impostare il **Alias** campo **MyASPApp**, accettare il valore predefinito di Pool di applicazioni (**DefaultAppPool**) e impostare il **percorso fisico** a  **C:\Publish**.

6. In **connessioni**selezionare **pool di applicazioni**. Aprire **DefaultAppPool** e impostare il campo pool di applicazioni su **nessun codice gestito**.

7. Il pulsante destro del nuovo sito in Gestione IIS, scegliere **Modifica autorizzazioni**e assicurarsi che tale account IUSR, IIS_IUSRS o l'utente configurato per l'accesso all'app web è un utente autorizzato con diritti di lettura ed esecuzione.

    Se non viene visualizzato uno di questi utenti con accesso, eseguire passaggi per aggiungere IUSR come utente con diritti di lettura ed esecuzione.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Pubblicare e distribuire l'app mediante la pubblicazione in una cartella locale da Visual Studio

È anche possibile pubblicare e distribuire l'app utilizzando il file system o altri strumenti.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Scaricare e installare remote tools in Windows Server

In questa esercitazione, si utilizza Visual Studio 2017.

Nel caso di problemi durante l'apertura della pagina con il download del debugger remoto, vedere [sbloccare il download del file](../debugger/remote-debugging.md#unblock_msvsmon) per assistenza.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> In alcuni scenari, può essere più efficiente per eseguire il debugger remoto da una condivisione file. Per ulteriori informazioni, vedere [eseguire il debugger remoto da una condivisione file](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Impostare il debugger remoto in Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere le autorizzazioni per altri utenti, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [configurare il debugger remoto](../debugger/remote-debugging.md#configure_msvsmon).

Per informazioni sull'esecuzione del debugger remoto come servizio, vedere [eseguire il debugger remoto come servizio](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Connettersi all'applicazione ASP.NET dal computer di Visual Studio

1. Nel computer di Visual Studio, aprire la soluzione che si sta tentando di eseguire il debug (**MyASPApp** se si segue tutti i passaggi in questo articolo).
2. In Visual Studio, fare clic su **Debug > Connetti a processo** (Ctrl + Alt + P).

    > [!TIP]
    > In Visual Studio 2017, è possibile ricollegare allo stesso processo in precedenza associato a tramite **Debug > riconnettersi al processo...** (Maiusc + Alt + P). 

3. Impostare il campo qualificatore su  **\<nome del computer remoto >: 4022**.
4. Fare clic su **Aggiorna**.
    Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.

    Se eventuali processi non viene visualizzato, provare a usare l'indirizzo IP anziché il nome del computer remoto (la porta è obbligatoria). È possibile utilizzare `ipconfig` in una riga di comando per ottenere l'indirizzo IPv4.

    Se si desidera utilizzare il **trovare** pulsante, potrebbe essere necessario [aprire la porta UDP 3702](#bkmk_openports) sul server.

5. Selezionare  **Mostra i processi di tutti gli utenti**.
6. Digitare la prima lettera del nome di un processo per trovare rapidamente **dotnet.exe** (per ASP.NET Core).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Scegliere **Connetti**.

8. Aprire il sito Web del computer remoto. In un browser, passare a **http://\<nome del computer remoto >**.
    
    Verrà visualizzata la pagina Web ASP.NET.

9. Nell'applicazione ASP.NET in esecuzione, fare clic sul collegamento per il **su** pagina.

    Il punto di interruzione verrà raggiunto in Visual Studio.

## <a name="bkmk_openports"></a> Risoluzione dei problemi: Aprire le porte necessarie in Windows Server

Nella maggior parte delle installazioni, vengono aperte le porte richieste dall'installazione di ASP.NET e il debugger remoto. Tuttavia, devi verificare che le porte siano aperte.

> [!NOTE]
> In una macchina virtuale di Azure, è necessario aprire porte tramite il [il gruppo di sicurezza di rete](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Porte richieste:

- 80 - necessari per IIS
- 4022 - necessari per il debug remoto da Visual Studio 2017 (vedere [assegnazioni di porta del Debugger remoto](../debugger/remote-debugger-port-assignments.md) per informazioni dettagliate.
- 8172 - (facoltativo) è obbligatorio per la distribuzione Web distribuire l'app da Visual Studio.
- UDP 3702 - Discovery (facoltativo) porta consente del **trovare** pulsante quando ci si connette al debugger remoto in Visual Studio.

1. Per aprire una porta in Windows Server, aprire il **avviare** menu, cercare **Windows Firewall con sicurezza avanzata**.

2. Scegliere quindi **regole connessioni in entrata > nuova regola > porta**, quindi fare clic su **Avanti**. (Per la porta UDP 3702, scegliere **regole in uscita** invece.)

3. In **porte locali specifiche**, immettere il numero di porta, fare clic su **Avanti**.

4. Fare clic su **Consenti la connessione**, fare clic su **Avanti**.

5. Selezionare uno o più tipi di rete da abilitare per la porta e fare clic su **Avanti**.

    Il tipo selezionato deve includere la rete a cui è connesso il computer remoto.
6. Aggiungere il nome (ad esempio, **IIS**, **distribuzione Web**, o **msvsmon**) per la regola in ingresso e fare clic su **fine**.

    Verrà visualizzata la nuova regola nell'elenco di regole in entrata o in uscita.

    Se si desidera visualizzare ulteriori dettagli su come configurare Windows Firewall, vedere [configurare Windows Firewall per debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Creare regole aggiuntive per le altre porte necessarie.
