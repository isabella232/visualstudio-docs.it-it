---
title: Eseguire il Debug remoto di ASP.NET Core in un Computer IIS remoto | Microsoft Docs
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
ms.openlocfilehash: 48c5d365c632deb4d654d5115a141ba9933d7a6f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410235"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Eseguire il Debug remoto di ASP.NET Core in un Computer IIS remoto in Visual Studio
Per eseguire il debug di un'applicazione ASP.NET che è stata distribuita a IIS, installare e quindi collegare all'app in esecuzione da Visual Studio eseguire remote tools sul computer in cui è distribuita l'app.

![Componenti del debugger remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Questa guida illustra come impostare e configurare un ASP.NET Core di Visual Studio, distribuirlo a IIS e associare il debugger remoto da Visual Studio. Eseguire il debug remoto ASP.NET 4.5.2, vedere [Remote Debug ASP.NET in un Computer IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). È anche possibile distribuire ed eseguire il debug su IIS usando Azure. Per il servizio App di Azure, è possibile distribuire con facilità ed eseguire il debug in un'istanza preconfigurata di IIS e il debugger remoto usando il [Snapshot Debugger](../debugger/debug-live-azure-applications.md) o da [collega il debugger da Esplora Server](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"
Per seguire i passaggi illustrati in questo articolo è necessario Visual Studio 2019.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 è necessario attenersi alla procedura illustrata in questo articolo.
::: moniker-end

Queste procedure sono state testate in queste configurazioni di server:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10

## <a name="network-requirements"></a>Requisiti di rete

Non è supportato tra due computer connessi tramite un proxy di debug. Debug tramite una latenza elevata o una connessione di larghezza di banda ridotta, ad esempio Internet, accesso remoto o la rete Internet tra paesi non è consigliabile e può avere esito negativo o essere inaccettabile. Per un elenco completo dei requisiti, vedere [requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Creare un'App già in esecuzione in IIS?

Questo articolo include i passaggi di configurazione di una configurazione di base di IIS in Windows server e la distribuzione dell'app da Visual Studio. Questi passaggi sono, per assicurarsi che il server ha richiesto i componenti installati, che l'app può essere eseguito correttamente e che si è pronti per eseguire il debug remoto.

* Se l'app è in esecuzione in IIS ed è sufficiente scaricare il debugger remoto e avviare il debug, passare a [scaricare e installare remote tools in Windows Server](#BKMK_msvsmon).

* Se si desidera visualizzare la Guida per assicurarsi che l'app è configurata, distribuzione e in esecuzione correttamente in IIS in modo che è possibile eseguire il debug, seguire tutti i passaggi descritti in questo argomento.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Creare l'applicazione ASP.NET Core nel computer di Visual Studio

1. Creare una nuova applicazione Web ASP.NET Core. 

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019, digitare **Ctrl + Q** per aprire la casella di ricerca, digitare **asp.net**, scegliere **modelli**, quindi scegliere **Crea nuova applicazione Web di ASP.NET Core** . Nella finestra di dialogo visualizzata, denominare il progetto **MyASPApp**, quindi scegliere **crea**. Scegliere quindi **applicazione Web (Model-View-Controller)**, quindi scegliere **crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017, scegliere **File > Nuovo > progetto**, quindi selezionare **Visual C# > Web > applicazione Web ASP.NET Core**. Nella sezione modelli ASP.NET Core, selezionare **applicazione Web (Model-View-Controller)**. Assicurarsi che sia selezionato ASP.NET Core 2.1, che **Abilita supporto Docker** non è selezionata e che **Authentication** è impostata su **Nessuna autenticazione**. Denominare il progetto **MyASPApp**.
    ::: moniker-end

4. Aprire il file About.cshtml.cs e impostare un punto di interruzione il `OnGet` (metodo) (in modelli precedenti, aprire HomeController.cs invece e impostare il punto di interruzione il `About()` (metodo)).

## <a name="bkmk_configureIIS"></a> Installare e configurare IIS in Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se sicurezza avanzata è abilitata in Internet Explorer (è abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per poter scaricare alcuni dei componenti server web. Aggiungere i siti attendibili scegliendo **Opzioni Internet > sicurezza > siti attendibili > siti**. Aggiungere i domini seguenti.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Quando si scarica il software, è possibile ricevere le richieste di concedere l'autorizzazione per caricare vari script del sito web e risorse. Alcune di queste risorse non sono necessarie, ma per semplificare il processo, fare clic su **Add** quando richiesto.

## <a name="install-aspnet-core-on-windows-server"></a>Installare ASP.NET Core in Windows Server

1. Installare l'[aggregazione di Hosting di.NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) nel sistema di hosting. L'aggregazione installa il runtime di .NET Core, la libreria di .NET Core e il modulo ASP.NET Core. Per altre istruzioni dettagliate, vedere [pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

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

1. Aprire l'Explorer di Windows e creare una nuova cartella denominata **C:\Publish**, in cui in seguito si distribuirà il progetto ASP.NET.

2. Se non è già aperto, aprire il **Internet Information Services (IIS) Manager**. (Nel riquadro sinistro di Server Manager, selezionare **IIS**. Fare clic con il pulsante destro del mouse sul server e selezionare **Gestione Internet Information Services (IIS)**.

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

Scaricare la versione di remote tools corrispondente alla versione di Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="BKMK_setup"></a> Configurare il debugger remoto in Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere le autorizzazioni per altri utenti, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [configurare il debugger remoto](../debugger/remote-debugging.md#configure_msvsmon).

Per informazioni sull'esecuzione del debugger remoto come servizio, vedere [eseguire il debugger remoto come servizio](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Connettersi all'applicazione ASP.NET dal computer di Visual Studio

1. Nel computer di Visual Studio, aprire la soluzione che si sta tentando di eseguire il debug (**MyASPApp** se si seguono tutti i passaggi in questo articolo).
2. In Visual Studio, fare clic su **Debug > Connetti a processo** (Ctrl + Alt + P).

    > [!TIP]
    > In Visual Studio 2017 e versioni successive, è possibile ricollegare allo stesso processo è associato in precedenza usando **Debug > riassocia a processo...** (Maiusc + Alt + P).

3. Impostare il campo qualificatore  **\<nome del computer remoto >** , quindi premere **invio**.

    Verificare che Visual Studio aggiunge la porta necessaria per il nome del computer, che viene visualizzata nel formato:  **\<nome del computer remoto >: porta**

    ::: moniker range=">=vs-2019"
    Visual Studio 2019, dovrebbe  **\<nome del computer remoto >: 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017, dovrebbe  **\<nome del computer remoto >: 4022**
    ::: moniker-end
    La porta è obbligatoria. Se non viene visualizzato il numero di porta, aggiungerlo manualmente.

4. Fare clic su **Aggiorna**.
    Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.

    Non vengono visualizzati tutti i processi, provare a usare l'indirizzo IP anziché il nome del computer remoto (la porta è obbligatoria). È possibile usare `ipconfig` in una riga di comando per ottenere l'indirizzo IPv4.

    Se si desidera utilizzare il **trovare** pulsante, potrebbe essere necessario [aprire la porta UDP 3702](#bkmk_openports) nel server.

5. Selezionare  **Mostra i processi di tutti gli utenti**.

6. Digitare la prima lettera del nome del processo per trovare rapidamente la tua app.

    * Selezionare **dotnet.exe**.

      Se si dispone di più processi che illustra **dotnet.exe**, selezionare la **nome utente** colonna. In alcuni scenari, il **nome utente** colonna indica il nome del pool di app, ad esempio **IIS APPPOOL\DefaultAppPool**. Se viene visualizzato il Pool di App, un modo semplice per identificare il processo corretto consiste nel creare un nuovo nome Pool di App per l'istanza dell'app da sottoporre a debug e quindi è possibile trovarlo facilmente nel **nome utente** colonna.

    * In alcuni scenari IIS, si potrebbe trovare il nome dell'app nell'elenco dei processi, come **MyASPApp.exe**. È possibile collegare invece al processo.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Scegliere **Connetti**.

8. Aprire il sito Web del computer remoto. In un browser passare a **http://\<nome computer remoto>**.

    Verrà visualizzata la pagina Web ASP.NET.

9. Nell'applicazione ASP.NET in esecuzione, fare clic sul collegamento per il **sulle** pagina.

    Il punto di interruzione verrà raggiunto in Visual Studio.

## <a name="bkmk_openports"></a> Risoluzione dei problemi: Aprire le porte necessarie in Windows Server

Nella maggior parte delle configurazioni, vengono aperte le porte richieste dall'installazione di ASP.NET e il debugger remoto. Tuttavia, devi verificare che le porte siano aperte.

> [!NOTE]
> In una VM di Azure, è necessario aprire le porte attraverso il [gruppo di sicurezza di rete](/azure/virtual-machines/windows/nsg-quickstart-portal).

Porte necessarie:

* 80 - required per IIS
::: moniker range=">=vs-2019"
* 4024 - richiesto per il debug remoto da Visual Studio 2019 (vedere [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) per altre informazioni).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - richiesto per il debug remoto da Visual Studio 2017 (vedere [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) per altre informazioni).
::: moniker-end
* UDP 3702, porta di individuazione (facoltativo) consente il **trovare** pulsante quando ci si collega al debugger remoto in Visual Studio.

1. Per aprire una porta in Windows Server, aprire il **avviare** menu, cercare **Windows Firewall con sicurezza avanzata**.

2. Quindi scegliere **regole connessioni in entrata > nuova regola > porta**, quindi fare clic su **successivo**. (Per la porta UDP 3702, scegliere **regole in uscita** invece.)

3. Sotto **porte locali specifiche**, immettere il numero di porta, fare clic su **successivo**.

4. Fare clic su **Consenti solo connessioni**, fare clic su **successivo**.

5. Selezionare uno o più tipi di rete da abilitare per la porta e fare clic su **successivo**.

    Il tipo selezionato deve includere la rete a cui è connesso il computer remoto.
6. Aggiungere il nome (ad esempio, **IIS**, **distribuzione Web**, o **msvsmon**) per la regola in ingresso e fare clic su **fine**.

    La nuova regola dovrebbe comparire nell'elenco Regole in ingresso o Regole in uscita.

    Se si desidera visualizzare ulteriori dettagli sulla configurazione di Windows Firewall, vedere [configurare il Firewall di Windows per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Creare regole aggiuntive per le altre porte necessarie.
