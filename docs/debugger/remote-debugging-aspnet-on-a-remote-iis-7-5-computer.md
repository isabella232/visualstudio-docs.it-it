---
title: Eseguire il Debug remoto ASP.NET in un Computer remoto con IIS | Documenti Microsoft
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: dddbe20c36aac6bc1c21cc2e29e59231c5b8feaf
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2018
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Eseguire il Debug remoto ASP.NET in un Computer remoto con IIS
Per eseguire il debug di un'applicazione ASP.NET che è stata distribuita a IIS, installare e quindi collegare all'App in esecuzione da Visual Studio eseguire remote tools sul computer in cui è distribuita l'app.

![I componenti del debugger remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Questa guida viene illustrato come impostare e configurare un'applicazione di Visual Studio 2017 ASP.NET MVC 4.5.2, distribuirlo in IIS e collegare il debugger remoto da Visual Studio.

> [!NOTE]
> In remoto il debug di ASP.NET Core invece, vedere [remoto il Debug di ASP.NET Core in un Computer con IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Per il servizio App di Azure, è possibile distribuire facilmente ed eseguire il debug in un'istanza preconfigurata di IIS utilizzando la [Debugger Snapshot](../debugger/debug-live-azure-applications.md) (.NET 4.6.1 richiesto) o da [per collegare il debugger da Esplora Server](../debugger/remote-debugging-azure.md).

Queste procedure sono state testate su queste configurazioni del server:
* Windows Server 2012 R2 e IIS 8 (per Windows Server 2008 R2, i passaggi di server sono diversi)

## <a name="requirements"></a>Requisiti

Il debugger remoto è supportato in Windows Server a partire da Windows Server 2008 Service Pack 2. Per un elenco completo dei requisiti, vedere [requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Il debug tra due computer connessi tramite un proxy non è supportato. Il debug tramite una connessione di larghezza di banda ridotta, ad esempio di connessione remota a Internet, ad alta latenza o tramite Internet tra paesi non è consigliato e potrebbe non funzionare oppure essere inaccettabile.

## <a name="app-already-running-in-iis"></a>App già in esecuzione in IIS?

In questo articolo include i passaggi per la configurazione di una configurazione di base di IIS in Windows server e distribuzione dell'app da Visual Studio. Questi passaggi sono, per assicurarsi che il server ha necessari componenti installati, che l'app può essere eseguito correttamente e che si è pronti per eseguire il debug remoto.

* Se l'app è in esecuzione in IIS e si desidera scaricare il debugger remoto, avviare il debug, visitare [scaricare e installare remote tools in Windows Server](#BKMK_msvsmon).

* Se si desidera visualizzare la Guida per assicurarsi che l'app è configurato, distribuito e in esecuzione correttamente in IIS in modo che è possibile eseguire il debug, seguono tutti i passaggi descritti in questo argomento.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Creare ASP.NET 4.5.2 applicazione nel computer di Visual Studio
  
1. Creare una nuova applicazione MVC ASP.NET (**File > Nuovo > progetto**, quindi selezionare * * Visual c# > Web > applicazione Web ASP.NET. Nella sezione modelli **ASP.NET 4.5.2** selezionare **MVC**. Assicurarsi che **Attiva supporto Docker** non è selezionata e che **autenticazione** è impostato su **Nessuna autenticazione**. Denominare il progetto **MyASPApp**.)

2. Aprire il file HomeController.cs e impostare un punto di interruzione nel metodo `About()` .

## <a name="bkmk_configureIIS"></a> Installare e configurare IIS in Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se sicurezza avanzata è abilitata in Internet Explorer (è abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per consentire il download alcuni dei componenti server web. Aggiungere siti attendibili, passare a **Opzioni Internet > sicurezza > siti attendibili > siti**. Aggiungere i seguenti domini.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Quando si scarica il software, è possibile ricevere le richieste per concedere autorizzazioni per caricare vari script del sito web e risorse. Alcune di queste risorse non sono necessarie, ma per semplificare il processo, fare clic su **Aggiungi** quando richiesto.

## <a name="BKMK_deploy_asp_net"></a> Installare ASP.NET 4.5 in Windows Server

Se si desiderano informazioni più dettagliate per installare ASP.NET in IIS, vedere [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Nel riquadro sinistro di Server Manager, selezionare **IIS**. Il server e scegliere **Internet Information Services (IIS) Manager**.

1. Utilizzare l'installazione guidata piattaforma Web (WebPI) per installare ASP.NET 4.5 (scegliere il nodo del Server in Windows Server 2012 R2, **ottenere nuovi componenti della piattaforma Web** e quindi cercare ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Se si utilizza Windows Server 2008 R2, installare ASP.NET 4 invece con il seguente comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Riavviare il sistema (o eseguire **net stop stato /y** seguito da **net start w3svc** da un prompt dei comandi per visualizzare una modifica al percorso di sistema).

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

Dopo che l'app viene distribuito correttamente, verrà avviato automaticamente. Se non si avvia l'app da Visual Studio, avviare l'app in IIS.

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

5. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

6. Impostare il **Alias** campo **MyASPApp**, accettare il valore predefinito di Pool di applicazioni (**DefaultAppPool**) e impostare il **percorso fisico** a  **C:\Publish**.

7. In **connessioni**selezionare **pool di applicazioni**. Aprire **DefaultAppPool** e impostare il campo pool di applicazioni su **ASP.NET v 4.0** (ASP.NET 4.5 non è un'opzione per il pool di applicazioni).

8. Con il sito selezionato in Gestione IIS, scegliere **Modifica autorizzazioni**e assicurarsi che tale account IUSR, IIS_IUSRS o l'utente configurato per il Pool di applicazioni è un utente autorizzato con diritti di lettura ed esecuzione. Se nessuno di questi utenti sono presenti, aggiungere IUSR come utente con diritti di lettura ed esecuzione.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Pubblicare e distribuire l'app mediante la pubblicazione in una cartella locale da Visual Studio

È anche possibile pubblicare e distribuire l'app utilizzando il file system o altri strumenti.

1. (ASP.NET 4.5.2) Assicurarsi che il file Web. config riporti la versione corretta di .NET Framework.  Ad esempio, se la destinazione ASP.NET 4.5.2, assicurarsi che questa versione è elencata nel file Web. config.
  
    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>
  
    ```

    Ad esempio, la versione deve essere 4.0, se si installa ASP.NET 4 anziché 4.5.2.

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

1. Nel computer di Visual Studio, aprire il **MyASPApp** soluzione.
2. In Visual Studio, fare clic su **Debug > Connetti a processo** (Ctrl + Alt + P).

    > [!TIP]
    > In Visual Studio 2017, è possibile ricollegare allo stesso processo in precedenza associato a tramite **Debug > riconnettersi al processo...** (Maiusc + Alt + P). 

3. Impostare il campo qualificatore su  **\<nome del computer remoto >: 4022**.
4. Fare clic su **Aggiorna**.
    Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.

    Se eventuali processi non viene visualizzato, provare a usare l'indirizzo IP anziché il nome del computer remoto (la porta è obbligatoria). È possibile utilizzare `ipconfig` in una riga di comando per ottenere l'indirizzo IPv4.

5. Selezionare  **Mostra i processi di tutti gli utenti**.
6. Digitare la prima lettera del nome di un processo per trovare rapidamente **w3wp.exe** per ASP.NET 4.5.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess.png "RemoteDBG_AttachToProcess")

7. Fare clic su **collegare**

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
- 8172 - (facoltativo) necessarie per la distribuzione Web distribuire l'app da Visual Studio
- 4022 - necessari per il debug remoto da Visual Studio 2017 (vedere [assegnazioni di porta del Debugger remoto](../debugger/remote-debugger-port-assignments.md) per informazioni dettagliate.
- UDP 3702 - Discovery (facoltativo) porta consente del **trovare** pulsante quando ci si connette al debugger remoto in Visual Studio.

1. Per aprire una porta in Windows Server, aprire il **avviare** menu, cercare **Windows Firewall con sicurezza avanzata**.

2. Scegliere quindi **regole connessioni in entrata > nuova regola > porta**. Scegliere **Avanti** e in **porte locali specifiche**, immettere il numero di porta, fare clic su **Avanti**, quindi **Consenti la connessione**, fare clic su Avanti, e aggiungere il nome (**IIS**, **distribuzione Web**, o **msvsmon**) per la regola in ingresso.

    Se si desidera visualizzare ulteriori dettagli su come configurare Windows Firewall, vedere [configurare Windows Firewall per debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Creare regole aggiuntive per le altre porte necessarie.