---
title: Eseguire il Debug remoto di ASP.NET Core in un Computer IIS remoto | Microsoft Docs
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
ms.openlocfilehash: d9515d208f2ab4bb8c429d5063e5134676c71c24
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38785957"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>Eseguire il Debug remoto di ASP.NET Core in un Computer IIS remoto in Visual Studio 2017
Per eseguire il debug di un'applicazione ASP.NET che è stata distribuita a IIS, installare e quindi collegare all'app in esecuzione da Visual Studio eseguire remote tools sul computer in cui è distribuita l'app.

![Componenti del debugger remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Questa guida illustra come impostare e configurare una base di ASP.NET di Visual Studio 2017, distribuirlo a IIS e associare il debugger remoto da Visual Studio. Eseguire il debug remoto ASP.NET 4.5.2, vedere [Remote Debug ASP.NET in un Computer IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). È anche possibile distribuire ed eseguire il debug su IIS usando Azure. Per il servizio App di Azure, è possibile distribuire con facilità ed eseguire il debug in un'istanza preconfigurata di IIS e il debugger remoto usando il [Snapshot Debugger](../debugger/debug-live-azure-applications.md) o da [collega il debugger da Esplora Server](../debugger/remote-debugging-azure.md).

Queste procedure sono state testate in queste configurazioni di server:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10

## <a name="requirements"></a>Requisiti

Non è supportato tra due computer connessi tramite un proxy di debug. Debug tramite una latenza elevata o una connessione di larghezza di banda ridotta, ad esempio Internet, accesso remoto o la rete Internet tra paesi non è consigliabile e può avere esito negativo o essere inaccettabile. Per un elenco completo dei requisiti, vedere [requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Creare un'App già in esecuzione in IIS?

Questo articolo include i passaggi di configurazione di una configurazione di base di IIS in Windows server e la distribuzione dell'app da Visual Studio. Questi passaggi sono, per assicurarsi che il server ha richiesto i componenti installati, che l'app può essere eseguito correttamente e che si è pronti per eseguire il debug remoto.

* Se l'app è in esecuzione in IIS ed è sufficiente scaricare il debugger remoto e avviare il debug, passare a [scaricare e installare remote tools in Windows Server](#BKMK_msvsmon).

* Se si desidera visualizzare la Guida per assicurarsi che l'app è configurata, distribuzione e in esecuzione correttamente in IIS in modo che è possibile eseguire il debug, seguire tutti i passaggi descritti in questo argomento.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Creare l'applicazione ASP.NET Core nel computer Visual Studio 2017 

1. Creare una nuova applicazione ASP.NET Core. (**File > Nuovo > progetto**, quindi selezionare **Visual c# > Web > applicazione Web ASP.NET Core**).

    Nel **ASP.NET Core** sezione modelli, selezionare **applicazione Web**.

2. Verificare che l'opzione **ASP.NET Core 2.0** è selezionata, che **Abilita supporto Docker** viene **non** selezionata e che **autenticazione** è impostato su **Nessuna autenticazione**.

3. Denominare il progetto **MyASPApp** e fare clic su **OK** per creare la nuova soluzione.

4. Aprire il file About.cshtml.cs e impostare un punto di interruzione il `OnGet` (metodo) (in modelli precedenti, aprire HomeController.cs invece e impostare il punto di interruzione il `About()` (metodo)).

## <a name="bkmk_configureIIS"></a> Installare e configurare IIS in Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se sicurezza avanzata è abilitata in Internet Explorer (è abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per poter scaricare alcuni dei componenti server web. Aggiungere i siti attendibili scegliendo **Opzioni Internet > sicurezza > siti attendibili > siti**. Aggiungere i domini seguenti.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Quando si scarica il software, è possibile ricevere le richieste di concedere l'autorizzazione per caricare vari script del sito web e risorse. Alcune di queste risorse non sono necessarie, ma per semplificare il processo, fare clic su **Add** quando richiesto.

## <a name="install-aspnet-core-on-windows-server"></a>Installare ASP.NET Core in Windows Server

1. Installare il [Hosting di .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) bundle nel sistema di hosting. Installa il bundle di Runtime di .NET Core, libreria di .NET Core e il modulo ASP.NET Core. Per altre istruzioni dettagliate, vedere [pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Se il sistema non ha una connessione a Internet, ottenere e installare il *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* prima di installare il bundle di Hosting di .NET Core Windows Server.

3. Riavviare il sistema (o eseguire **net stop was /y** aggiungendo **net start w3svc** da un prompt dei comandi per visualizzare una modifica al percorso di sistema).

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

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Creare il file di impostazioni di pubblicazione in IIS in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Dopo che l'app distribuisce correttamente, viene avviata automaticamente. Se non si avvia l'app da Visual Studio, avviare l'app in IIS. Per ASP.NET Core, è necessario assicurarsi che il pool di applicazioni di campo per il **DefaultAppPool** è impostata su **nessun codice gestito**.

1. Nel **le impostazioni** della finestra di dialogo Abilita il debug facendo clic **successivo**, scegliere un **Debug** configurazione e quindi scegliere **Rimuovi file aggiuntivi nella destinazione** sotto la **pubblicare File** opzioni.

    > [!NOTE]
    > Se si sceglie una configurazione di rilascio, si disabilita il debug nel *Web. config* file durante la pubblicazione.

1. Fare clic su **salvare** e quindi ripubblicare l'app.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Facoltativo) Distribuire mediante la pubblicazione in una cartella locale

È possibile usare questa opzione per distribuire l'app se si desidera copiare l'app a IIS tramite Powershell, RoboCopy o si desidera copiare manualmente i file.

### <a name="BKMK_deploy_asp_net"></a> Configurare il sito Web ASP.NET nel computer Windows Server

1. Aprire l'Explorer di Windows e creare una nuova cartella denominata **C:\Publish**, in cui in seguito si distribuirà il progetto ASP.NET.

2. Se non è già aperto, aprire il **Internet Information Services (IIS) Manager**. (Nel riquadro sinistro di Server Manager, selezionare **IIS**. Fare doppio clic su server e selezionare **Internet Information Services (IIS) Manager**.)

3. Sotto **connessioni** nel riquadro a sinistra, passare alla **siti**.

4. Selezionare il **sito Web predefinito**, scegliere **impostazioni di base**e impostare il **percorso fisico** al **C:\Publish**.

4. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

5. Impostare il **Alias** campo **MyASPApp**, accettare il valore predefinito del Pool di applicazioni (**DefaultAppPool**) e impostare il **percorso fisico** a  **C:\Publish**.

6. Sotto **connessioni**, selezionare **pool di applicazioni**. Aprire **DefaultAppPool** e impostare il campo di pool di applicazioni **nessun codice gestito**.

7. Fare clic su Nuovo sito in Gestione IIS, scegliere **Edit Permissions**e assicurarsi che tale account IUSR, IIS_IUSRS o l'utente sia configurato per l'accesso all'app web è un utente autorizzato con diritti di lettura ed esecuzione.

    Se non viene visualizzato uno di questi utenti con accesso, eseguono passaggi per aggiungere IUSR come utente con diritti di lettura ed esecuzione.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Pubblicare e distribuire l'app tramite la pubblicazione in una cartella locale da Visual Studio

È anche possibile pubblicare e distribuire l'app usando il file system o altri strumenti.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Scaricare e installare remote tools in Windows Server

In questa esercitazione viene usato Visual Studio 2017.

Se hai problemi durante l'apertura della pagina con il download del debugger remoto, vedere [sbloccare il download del file](../debugger/remote-debugging.md#unblock_msvsmon) per assistenza.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> In alcuni scenari, può essere più efficiente per eseguire il debugger remoto da una condivisione file. Per altre informazioni, vedere [eseguire il debugger remoto da una condivisione file](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Configurare il debugger remoto in Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere le autorizzazioni per altri utenti, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [configurare il debugger remoto](../debugger/remote-debugging.md#configure_msvsmon).

Per informazioni sull'esecuzione del debugger remoto come servizio, vedere [eseguire il debugger remoto come servizio](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Connettersi all'applicazione ASP.NET dal computer di Visual Studio

1. Nel computer di Visual Studio, aprire la soluzione che si sta tentando di eseguire il debug (**MyASPApp** se si seguono tutti i passaggi in questo articolo).
2. In Visual Studio, fare clic su **Debug > Connetti a processo** (Ctrl + Alt + P).

    > [!TIP]
    > In Visual Studio 2017, è possibile ricollegare allo stesso processo è associato in precedenza usando **Debug > riassocia a processo...** (Maiusc + Alt + P). 

3. Impostare il campo qualificatore  **\<nome del computer remoto >: 4022**.
4. Fare clic su **Aggiorna**.
    Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.

    Non vengono visualizzati tutti i processi, provare a usare l'indirizzo IP anziché il nome del computer remoto (la porta è obbligatoria). È possibile usare `ipconfig` in una riga di comando per ottenere l'indirizzo IPv4.

    Se si desidera utilizzare il **trovare** pulsante, potrebbe essere necessario [aprire la porta UDP 3702](#bkmk_openports) nel server.

5. Selezionare  **Mostra i processi di tutti gli utenti**.
6. Digitare la prima lettera del nome di un processo per trovare rapidamente **dotnet.exe** (per ASP.NET Core).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Scegliere **Connetti**.

8. Aprire il sito Web del computer remoto. In un browser, passare a **http://\<nome del computer remoto >**.
    
    Verrà visualizzata la pagina Web ASP.NET.

9. Nell'applicazione ASP.NET in esecuzione, fare clic sul collegamento per il **sulle** pagina.

    Il punto di interruzione verrà raggiunto in Visual Studio.

## <a name="bkmk_openports"></a> Risoluzione dei problemi: Aprire le porte necessarie in Windows Server

Nella maggior parte delle configurazioni, vengono aperte le porte richieste dall'installazione di ASP.NET e il debugger remoto. Tuttavia, devi verificare che le porte siano aperte.

> [!NOTE]
> In una VM di Azure, è necessario aprire le porte attraverso il [gruppo di sicurezza di rete](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic).

Porte necessarie:

- 80 - required per IIS
- 4022 - richiesto per il debug remoto da Visual Studio 2017 (vedere [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) per informazioni dettagliate.
- 8172 - (facoltativa) richiesta per la distribuzione Web per distribuire l'app da Visual Studio.
- UDP 3702, porta di individuazione (facoltativo) consente il **trovare** pulsante quando ci si collega al debugger remoto in Visual Studio.

1. Per aprire una porta in Windows Server, aprire il **avviare** menu, cercare **Windows Firewall con sicurezza avanzata**.

2. Quindi scegliere **regole connessioni in entrata > nuova regola > porta**, quindi fare clic su **successivo**. (Per la porta UDP 3702, scegliere **regole in uscita** invece.)

3. Sotto **porte locali specifiche**, immettere il numero di porta, fare clic su **successivo**.

4. Fare clic su **Consenti solo connessioni**, fare clic su **successivo**.

5. Selezionare uno o più tipi di rete da abilitare per la porta e fare clic su **successivo**.

    Il tipo selezionato deve includere la rete a cui è connesso il computer remoto.
6. Aggiungere il nome (ad esempio, **IIS**, **distribuzione Web**, o **msvsmon**) per la regola in ingresso e fare clic su **fine**.

    Si dovrebbe vedere la nuova regola nell'elenco Regole connessioni in entrata o in uscita.

    Se si desidera visualizzare ulteriori dettagli sulla configurazione di Windows Firewall, vedere [configurare il Firewall di Windows per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Creare regole aggiuntive per le altre porte necessarie.
