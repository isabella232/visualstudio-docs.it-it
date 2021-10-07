---
title: Debug remoto ASP.NET Core in un computer IIS remoto | Microsoft Docs
description: Eseguire il debug ASP.NET Core'applicazione distribuita in un computer Internet Information Services remoto (IIS) usando il debugger Visual Studio remoto.
ms.custom: remotedebugging, SEO-VS-2020
ms.date: 08/27/2021
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 376a0f438e17d1023644e545812c50cf35b34dca
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635933"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Debug remoto ASP.NET Core in un computer IIS remoto in Visual Studio

Per eseguire il debug di un'applicazione ASP.NET Core distribuita in IIS, installare ed eseguire gli strumenti remoti nel computer in cui è stata distribuita l'app e quindi connettersi all'app in esecuzione da Visual Studio.

![Componenti del debugger remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Questa guida illustra come impostare e configurare un Visual Studio ASP.NET Core, distribuirlo in IIS e collegare il debugger remoto da Visual Studio. Per eseguire il debug ASP.NET 4.5.2, vedere [Remote Debug ASP.NET on an IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). È anche possibile eseguire la distribuzione e il debug in IIS usando Azure. Ad Servizio app di Azure, è possibile eseguire facilmente la distribuzione e il debug in un'istanza preconfigurata di IIS e nel debugger remoto usando il [Snapshot Debugger](../debugger/debug-live-azure-applications.md) o collegando il [debugger da Esplora server](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"
Visual Studio 2019 è necessario per seguire la procedura illustrata in questo articolo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 è necessario seguire la procedura illustrata in questo articolo.
::: moniker-end

Queste procedure sono state testate in queste configurazioni server:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10
* Windows Server 2019 e IIS 10

## <a name="network-requirements"></a>Requisiti di rete

Il debug tra due computer connessi tramite un proxy non è supportato. Non è consigliabile eseguire il debug su una connessione a latenza elevata o a larghezza di banda ridotta, ad esempio una connessione remota a Internet o su Internet tra paesi diversi, che potrebbe avere esito negativo o essere inaccettabilmente lenta. Per un elenco completo dei requisiti, vedere [Requisiti.](../debugger/remote-debugging.md#requirements_msvsmon)

## <a name="app-already-running-in-iis"></a>App già in esecuzione in IIS?

Questo articolo include i passaggi per configurare una configurazione di base di IIS Windows server e distribuire l'app da Visual Studio. Questi passaggi sono inclusi per assicurarsi che nel server siano installati i componenti necessari, che l'app possa essere eseguita correttamente e che si sia pronti per il debug remoto.

* Se l'app è in esecuzione in IIS e si vuole solo scaricare il debugger remoto e avviare il debug, passare a Scaricare e installare gli strumenti remoti [in Windows Server.](#BKMK_msvsmon)

* Per assicurarsi che l'app sia configurata, distribuita ed eseguita correttamente in IIS in modo da poter eseguire il debug, seguire tutti i passaggi descritti in questo argomento.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Creare l ASP.NET Core app applicazione nel computer Visual Studio

1. Creare una nuova applicazione Web ASP.NET Core.

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 scegliere **Crea un nuovo progetto** nella finestra iniziale. Se la finestra iniziale non è aperta, scegliere **Finestra**  >  **iniziale file**. Digitare **app Web,** scegliere **C#** come linguaggio, quindi ASP.NET Core **Applicazione Web (Model-View-Controller)** e infine **scegliere Avanti.** Nella schermata successiva assegnare al progetto il **nome MyASPApp** e quindi scegliere **Avanti.**

    Scegliere il framework di destinazione consigliato o .NET 6 e quindi scegliere **Crea.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 scegliere **File > Nuovo > Project**, quindi selezionare **Visual C# > Web > ASP.NET Core Web Application**. Nella sezione ASP.NET Core modelli selezionare **Applicazione Web (Model-View-Controller).** Assicurarsi che sia ASP.NET Core 2.1, che l'opzione Abilita supporto  **Docker** non sia selezionata e che l'opzione Autenticazione sia impostata su **Nessuna autenticazione**. Assegnare al progetto **il nome MyASPApp**.
    ::: moniker-end

4. Aprire il file About.cshtml.cs e impostare un punto di interruzione nel metodo . Nei modelli precedenti aprire invece HomeController.cs e impostare il punto di `OnGet` interruzione nel `About()` metodo .

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Installare e configurare IIS in Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser Windows Server

Se la configurazione della sicurezza avanzata è abilitata in Internet Explorer (abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per consentire il download di alcuni componenti del server Web. Aggiungere i siti attendibili selezionando Opzioni **Internet > Sicurezza > siti > attendibili**. Aggiungere i domini seguenti.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Quando si scarica il software, è possibile che si otterrà una richiesta di concessione dell'autorizzazione per caricare vari script e risorse del sito Web. Alcune di queste risorse non sono necessarie, ma per semplificare il processo, fare clic **su Aggiungi** quando richiesto.

## <a name="install-aspnet-core-on-windows-server"></a>Installare ASP.NET Core in Windows Server

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

Quando la distribuzione è completata, l'app viene avviata automaticamente. Se l'app non viene avviata da Visual Studio, avviare l'app in IIS per verificare che venga eseguita correttamente. Per ASP.NET Core, è anche necessario assicurarsi che il campo Pool di applicazioni per **DefaultAppPool** sia impostato su **Nessun codice gestito.**

1. Passare a una configurazione di debug.

   ::: moniker range=">=vs-2019"
   Scegliere **Modifica** per modificare il profilo e quindi scegliere **Impostazioni**. Scegliere una **configurazione** di debug e quindi scegliere **Rimuovi file aggiuntivi nella destinazione** nelle opzioni **Pubblicazione** file.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Nella finestra **Impostazioni,** abilitare il debug facendo clic su Avanti **,** scegliere una configurazione di **debug** e quindi scegliere Rimuovi file aggiuntivi nella destinazione nelle **opzioni Pubblicazione** file. 
   ::: moniker-end

   > [!IMPORTANT]
   > Se si sceglie una configurazione versione, il debug viene disabilitato nel file *web.config* quando si esegue la pubblicazione.

1. Fare **clic su Salva** e quindi ripubblicare l'app.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Facoltativo) Eseguire la distribuzione pubblicando in una cartella locale

È possibile usare questa opzione per distribuire l'app se si vuole copiare l'app in IIS usando PowerShell, RoboCopy o copiare manualmente i file.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Configurare il ASP.NET Core Web nel computer Windows Server

1. Aprire Windows Explorer e creare una nuova cartella, **C:\Publish,** in cui in seguito si distribuirà ASP.NET Core progetto.

2. Se non è già aperto, aprire gestione **Internet Information Services (IIS).** (Nel riquadro sinistro di Server Manager selezionare **IIS.** Fare clic con il pulsante destro del mouse sul server e selezionare **Gestione Internet Information Services (IIS)**.

3. In **Connessioni** nel riquadro sinistro passare a **Siti**.

4. Selezionare sito **Web predefinito,** scegliere **Basic Impostazioni** e impostare **percorso fisico** **su C:\Publish.**

5. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

6. Impostare il **campo Alias** su **MyASPApp**, accettare il pool di applicazioni predefinito (**DefaultAppPool**) e impostare **percorso fisico** su **C:\Publish**.

7. In **Connessioni** selezionare **Pool di applicazioni.** Aprire **DefaultAppPool e** impostare il campo Pool di applicazioni **su Nessun codice gestito.**

8. Fare clic con il pulsante destro del mouse sul nuovo sito in Gestione IIS, scegliere Modifica autorizzazioni e assicurarsi che IUSR, IIS_IUSRS o l'utente configurato per l'accesso all'app Web sia un utente autorizzato con diritti di lettura & Execute.

    Se uno di questi utenti non viene visualizzato con accesso, seguire la procedura per aggiungere IUSR come utente con diritti di lettura & Esecuzione.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Pubblicare e distribuire l'app pubblicando in una cartella locale da Visual Studio

È anche possibile pubblicare e distribuire l'app usando file system o altri strumenti.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Scaricare e installare gli strumenti remoti in Windows Server

Scaricare la versione degli strumenti remoti che corrisponde alla versione di Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Configurare il debugger remoto in Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere autorizzazioni per altri utenti, modificare la modalità di autenticazione o il numero di porta per il debugger [remoto,](../debugger/remote-debugging.md#configure_msvsmon)vedere Configurare il debugger remoto .

Per informazioni sull'esecuzione del debugger remoto come servizio, vedere [Eseguire il debugger remoto come servizio](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Connettersi all'applicazione ASP.NET dal computer Visual Studio locale

1. Nel computer Visual Studio aprire la soluzione di cui si sta tentando di eseguire il debug (**MyASPApp** se si stanno seguendo tutti i passaggi di questo articolo).
2. In Visual Studio fare clic su **Debug > collega a processo** (CTRL+ALT+P).

    > [!TIP]
    > In Visual Studio 2017 e versioni successive, è possibile ricollegare allo stesso processo a cui è stato precedentemente collegato usando Debug > Ricollegare **a processo...** (MAIUSC+ALT+P).

3. Impostare il campo Qualificatore su **\<remote computer name>** e premere **INVIO.**

    Verificare che Visual Studio la porta necessaria al nome del computer, che viene visualizzata nel formato: **\<remote computer name> :p ort**

    ::: moniker range=">=vs-2022"
    In Visual Studio 2022 dovrebbe essere visualizzato **\<remote computer name> :4026**
    ::: moniker-end
    ::: moniker range="vs-2019"
    In Visual Studio 2019 dovrebbe essere visualizzato **\<remote computer name> :4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 dovrebbe essere visualizzato **\<remote computer name> :4022**
    ::: moniker-end
    La porta è obbligatoria. Se il numero di porta non viene visualizzato, aggiungerlo manualmente.

4. Fare clic su **Aggiorna**.
    Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.

    Se non viene visualizzato alcun processo, provare a usare l'indirizzo IP anziché il nome del computer remoto (la porta è obbligatoria). È possibile usare `ipconfig` in una riga di comando per ottenere l'indirizzo IPv4.

    Se si vuole usare il **pulsante** Trova, potrebbe essere necessario [aprire la porta UDP 3702](#bkmk_openports) nel server.

5. Selezionare  **Mostra i processi di tutti gli utenti**.

6. Digitare la prima lettera del nome del processo per trovare rapidamente l'app.

    * Se si usa il modello [di hosting in-process](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) in IIS, selezionare il **processo** diw3wp.execorretto. A partire da .NET Core 3, questa è l'impostazione predefinita.

    * In caso contrario, selezionare **dotnet.exe** processo. Si tratta del modello di hosting out-of-process.

    Se sono presenti più processi che *w3wp.exe* o *dotnet.exe,* controllare la **colonna Nome** utente. In alcuni scenari la colonna **Nome utente** mostra il nome del pool di app, ad esempio **IIS APPPOOL\DefaultAppPool.** Se viene visualizzato il pool di app, ma non è univoco, creare un nuovo pool di app denominato per l'istanza dell'app di cui si vuole eseguire il debug e quindi è possibile trovarlo facilmente nella colonna **Nome** utente.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Scegliere **Connetti**.

8. Aprire il sito Web del computer remoto. In un browser passare a **http:// \<remote computer name>**.

    Verrà visualizzata la pagina Web ASP.NET.

9. Nell'applicazione ASP.NET in esecuzione fare clic sul collegamento alla **pagina** Informazioni su.

    Il punto di interruzione verrà raggiunto in Visual Studio.

## <a name="troubleshooting-iis-deployment"></a>Risoluzione dei problemi relativi alla distribuzione di IIS

- Se non è possibile connettersi all'host usando il nome host, provare l'indirizzo IP.
- Assicurarsi che le porte necessarie siano aperte nel server remoto.
- Per ASP.NET Core, è necessario assicurarsi che il campo Pool di applicazioni per **DefaultAppPool** sia impostato su **Nessun codice gestito**.
- Verificare che la versione ASP.NET usata nell'app sia la stessa della versione installata nel server. Per l'app, è possibile visualizzare e impostare la versione nella **pagina** Proprietà. Per impostare l'app su una versione diversa, è necessario installare tale versione.
- Se l'app ha provato ad aprire, ma viene visualizzato un avviso relativo al certificato, scegliere di considerare attendibile il sito. Se l'avviso è già stato chiuso, è possibile modificare il profilo di pubblicazione, un file *.pubxml, nel progetto e aggiungere l'elemento seguente (solo per test): `<AllowUntrustedCertificate>true</AllowUntrustedCertificate>`
- Se l'app non viene avviata Visual Studio, avviare l'app in IIS per verificare che sia stata distribuita correttamente.
- Controllare la finestra Output in Visual Studio informazioni sullo stato e controllare i messaggi di errore.

## <a name="open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Aprire le porte necessarie in Windows Server

Nella maggior parte delle configurazioni, le porte necessarie vengono aperte dall'installazione di ASP.NET e del debugger remoto. Tuttavia, potrebbe essere necessario verificare che le porte siano aperte.

> [!NOTE]
> In una macchina virtuale di Azure è necessario aprire le porte tramite il [gruppo di sicurezza di rete](/azure/virtual-machines/windows/nsg-quickstart-portal).

Porte necessarie:

* 80 - Obbligatorio per IIS (HTTP)
::: moniker range=">=vs-2022"
* 4026 - Obbligatorio per il debug remoto da Visual Studio 2022 (per altre informazioni, vedere [Assegnazioni](../debugger/remote-debugger-port-assignments.md) delle porte del debugger remoto).
::: moniker-end
::: moniker range="vs-2019"
* 4024 : obbligatorio per il debug remoto da Visual Studio 2019 (per altre informazioni, vedere [Assegnazioni](../debugger/remote-debugger-port-assignments.md) delle porte del debugger remoto).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Obbligatorio per il debug remoto da Visual Studio 2017 (per altre informazioni, vedere [Assegnazioni](../debugger/remote-debugger-port-assignments.md) delle porte del debugger remoto).
::: moniker-end
* UDP 3702 : (facoltativo) Porta  di individuazione consente di usare il pulsante Trova quando ci si connette al debugger remoto in Visual Studio.

1. Per aprire una porta in Windows Server, aprire il menu **Start,** cercare Windows **Firewall con sicurezza avanzata**.

2. Scegliere quindi **Regole in ingresso > Nuova regola > porta** e quindi fare clic su **Avanti.** Per UDP 3702 scegliere **regole in** uscita.

3. In **Porte locali specifiche** immettere il numero di porta e fare clic su **Avanti.**

4. Fare **clic su Consenti connessione**, quindi su **Avanti**.

5. Selezionare uno o più tipi di rete da abilitare per la porta e fare clic su **Avanti.**

    Il tipo selezionato deve includere la rete a cui è connesso il computer remoto.

6. Aggiungere il nome (ad **esempio, IIS**, **Distribuzione Web** o **msvsmon**) per la regola in ingresso e fare clic su **Fine**.

    La nuova regola dovrebbe comparire nell'elenco Regole in ingresso o Regole in uscita.

    Per altri dettagli sulla configurazione di Windows Firewall, vedere Configurare il firewall Windows [per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Creare regole aggiuntive per le altre porte necessarie.
