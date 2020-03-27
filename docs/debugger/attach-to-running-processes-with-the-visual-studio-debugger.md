---
title: Connettersi ai processi in esecuzione con il debugger . Documenti Microsoft
ms.custom: seodec18
ms.date: 04/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5305be7615e426d7792d8dd3fefb2579e2ab6be
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233053"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Associare a processi in esecuzione con il debugger di Visual Studio
È possibile collegare il debugger di Visual Studio a un processo in esecuzione in un computer locale o remoto. Dopo aver eseguito il processo, selezionare **Esegui debug** > **connetti a processo** o premere **CTRL**+**Alt**+**P** in Visual Studio e utilizzare la finestra di dialogo Connetti a **processo** per connettere il debugger al processo.

Puoi usare **Connetti a processo** per eseguire il debug di app in esecuzione in computer locali o remoti, eseguire contemporaneamente il debug di più processi, eseguire il debug di app che non sono state create in Visual Studio o eseguire il debug di app non avviate da Visual Studio con il debugger collegato. Ad esempio, se si esegue un'app senza il debugger e si verifica un'eccezione, è possibile connettere il debugger al processo che esegue l'app e avviare il debug.

> [!TIP]
> Non si è certi di utilizzare **Connetti a processo** per lo scenario di debug? Vedere [Scenari di debug comuni](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a>Connettersi a un processo in esecuzione nel computer locale

Per riconnettersi rapidamente a un processo collegato in precedenza, vedere [Ricollega a un processo](#BKMK_reattach).

Per eseguire il debug di un processo in un computer remoto, vedere [Connettersi a un processo in un computer remoto.](#BKMK_Attach_to_a_process_on_a_remote_computer)

::: moniker range=">= vs-2019"
Per eseguire il debug di un processo .NET Core in un contenitore Docker Linux, vedere [Connettersi a un contenitore Docker Linux.](#BKMK_Linux_Docker_Attach)
::: moniker-end

**Per connettersi a un processo nel computer locale:**

1. In Visual Studio selezionare **Esegui debug** > **e seguito da elaborazione** oppure premere **CTRL**+**Alt**+**P**per aprire la finestra di dialogo Connetti a **processo** .

   **Il tipo di connessione** deve essere impostato su **Predefinito**. **La destinazione** della connessione deve essere il nome del computer locale.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. Nell'elenco **Processi disponibili** individuare e selezionare il processo o i processi a cui si desidera connettersi.

   - Per selezionare rapidamente un processo, digitarne il nome o la prima lettera nella casella **Filtra processi.**

   - Se non si conosce il nome del processo, sfogliare l'elenco o vedere Scenari di [debug comuni](#BKMK_Scenarios) per alcuni nomi di processo comuni.

   >[!TIP]
   >I processi possono essere avviati e interrotti in background mentre la finestra di dialogo **Connetti a processo** è aperta, pertanto l'elenco dei processi in esecuzione potrebbe non essere sempre aggiornato. È possibile selezionare **Aggiorna** in qualsiasi momento per visualizzare l'elenco corrente.

3. Nel campo **Allega a** verificare che sia elencato il tipo di codice di cui si intende eseguire il debug. L'impostazione **automatica** predefinita funziona per la maggior parte dei tipi di app.

   Per selezionare manualmente i tipi di codice:
   1. Fare clic su **Seleziona**.
   1. Nella finestra di dialogo **Seleziona tipo di codice** selezionare Esegui debug di questi tipi di **codice**.
   1. Selezionare i tipi di codice di cui si desidera eseguire il debug.
   1. Selezionare **OK**.

4. Selezionare **Allega**.

>[!NOTE]
>Puoi essere connesso a più app per il debug, ma nel debugger è attiva una sola app alla volta. È possibile impostare l'app attiva nella barra degli strumenti Percorso di **debug** di Visual Studio o nella finestra **Processi.**

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Connettersi a un processo su un computer remoto

È inoltre possibile selezionare un computer remoto nella finestra di dialogo **Connetti a processo,** visualizzare un elenco dei processi disponibili in esecuzione in tale computer e connettersi a uno o più processi per il debug. Il debugger remoto (*msvsmon.exe*) deve essere in esecuzione nel computer remoto. Per ulteriori informazioni, vedere [Debug remoto](../debugger/remote-debugging.md).

Per istruzioni più complete relative al debug di applicazioni ASP.NET distribuite in IIS, vedere ASP.NET di [debug remoto in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Per connettersi a un processo in esecuzione in un computer remoto:**

1. In Visual Studio selezionare **Esegui debug** > **e seguito da elaborazione** oppure premere **CTRL**+**Alt**+**P**per aprire la finestra di dialogo Connetti a **processo** .

2. **Il tipo di connessione** deve essere **Predefinito** per la maggior parte dei casi. Nella casella **Destinazione connessione** selezionare il computer remoto utilizzando uno dei metodi seguenti:

   - Selezionare la freccia a discesa accanto a **Destinazione connessione**e selezionare il nome del computer dall'elenco a discesa.
   - Digitare il nome del computer nella casella **Destinazione connessione** e premere **INVIO**.

     Verificare che Visual Studio aggiunga la porta richiesta al nome del computer, che viene visualizzato nel formato: ** \<nome computer remoto>:porta**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Se non è possibile connettersi utilizzando il nome del computer remoto, `123.45.678.9:4022`provare a utilizzare l'indirizzo IP e l'indirizzo della porta , ad esempio ). 4024 è la porta predefinita per il debugger remoto x64 di Visual Studio 2019. Per altre assegnazioni di porte del debugger remoto, vedere [Assegnazioni di porte](remote-debugger-port-assignments.md)del debugger remoto .

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Se non è possibile connettersi utilizzando il nome del computer remoto, `123.45.678.9:4022`provare a utilizzare l'indirizzo IP e l'indirizzo della porta , ad esempio ). 4022 è la porta predefinita per il debugger remoto x64 di Visual Studio 2017. Per altre assegnazioni di porte del debugger remoto, vedere [Assegnazioni di porte](remote-debugger-port-assignments.md)del debugger remoto .

     ::: moniker-end

   - Selezionare il pulsante **Trova** accanto alla casella **Destinazione connessione** per aprire la finestra di dialogo **Connessioni remote.** Nella finestra di dialogo **Connessioni remote** sono elencati tutti i dispositivi presenti nella subnet locale o collegati direttamente al computer. Potrebbe essere necessario aprire la [porta UDP 3702](../debugger/remote-debugger-port-assignments.md) sul server per individuare i dispositivi remoti. Selezionare il computer o il dispositivo desiderato e quindi fare clic su **Seleziona**.

   > [!NOTE]
   > L'impostazione Tipo di **connessione** viene mantenuta tra le sessioni di debug. L'impostazione **Destinazione connessione** viene mantenuta tra le sessioni di debug solo se si è verificata una connessione di debug riuscita con tale destinazione.

3. Fare clic su **Aggiorna** per popolare l'elenco **Processi disponibili.**

    >[!TIP]
    >I processi possono essere avviati e interrotti in background mentre la finestra di dialogo **Connetti a processo** è aperta, pertanto l'elenco dei processi in esecuzione potrebbe non essere sempre aggiornato. È possibile selezionare **Aggiorna** in qualsiasi momento per visualizzare l'elenco corrente.

4. Nell'elenco **Processi disponibili** individuare e selezionare il processo o i processi a cui si desidera connettersi.

   - Per selezionare rapidamente un processo, digitarne il nome o la prima lettera nella casella **Filtra processi.**

   - Se non si conosce il nome del processo, sfogliare l'elenco o vedere Scenari di [debug comuni](#BKMK_Scenarios) per alcuni nomi di processo comuni.

   - Per trovare i processi in esecuzione in tutti gli account utente, selezionare la casella di controllo **Mostra processi di tutti gli utenti.**

     >[!NOTE]
     >Se si tenta di connettersi a un processo appartenente a un account utente non attendibile, verrà visualizzata una finestra di dialogo contenente un avviso di sicurezza per chiedere conferma dell'operazione. Per ulteriori informazioni, vedere Avviso di [sicurezza: la connessione a un processo di proprietà di un utente non attendibile può essere pericolosa. Se le seguenti informazioni sembrano sospette o non si è sicuri, non connettersi a questo processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. Nel campo **Allega a** verificare che sia elencato il tipo di codice di cui si intende eseguire il debug. L'impostazione **automatica** predefinita funziona per la maggior parte dei tipi di app.

   Per selezionare manualmente i tipi di codice:
   1. Fare clic su **Seleziona**.
   1. Nella finestra di dialogo **Seleziona tipo di codice** selezionare Esegui debug di questi tipi di **codice**.
   1. Selezionare i tipi di codice di cui si desidera eseguire il debug.
   1. Selezionare **OK**.

6. Selezionare **Allega**.

>[!NOTE]
>Puoi essere connesso a più app per il debug, ma nel debugger è attiva una sola app alla volta. È possibile impostare l'app attiva nella barra degli strumenti Percorso di **debug** di Visual Studio o nella finestra **Processi.**

In alcuni casi, quando si esegue il debug in una sessione di Desktop remoto (Servizi terminal), l'elenco **processi disponibili** non visualizzerà tutti i processi disponibili. Se si esegue Visual Studio come utente con un account utente limitato, l'elenco **processi disponibili** non mostrerà i processi in esecuzione nella sessione 0. La sessione 0 viene utilizzata per i servizi e altri processi server, *incluso w3wp.exe*. È possibile risolvere il problema eseguendo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con un account amministratore o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalla console del server invece di una sessione di Servizi Terminal.

Se non è possibile adottare una di queste soluzioni alternative, una terza opzione consiste nel connettersi al processo eseguendo `vsjitdebugger.exe -p <ProcessId>` dalla riga di comando di Windows. È possibile determinare l'ID processo utilizzando *tlist.exe*. Per ottenere *tlist.exe*, scaricare e installare gli strumenti di debug per Windows disponibili in [Download di WDK e WinDbg](/windows-hardware/drivers/download-the-wdk).

::: moniker range=">= vs-2019"


## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Connettersi a un processo .NET Core in esecuzione su Linux usando SSH

Per ulteriori informazioni, consultate [Debug remoto di .NET Core in esecuzione su Linux con SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a>Connettersi a un processo in esecuzione in un contenitore Linux Docker

È possibile connettere il debugger di Visual Studio a un processo in esecuzione in un contenitore Linux .NET Core Docker nel computer locale o remoto utilizzando la finestra di dialogo **Connetti a processo** .

> [!IMPORTANT]
> Per usare questa funzionalità, è necessario installare il carico di lavoro di sviluppo multipiattaforma .NET Core e disporre dell'accesso locale al codice sorgente.

**Per connettersi a un processo in esecuzione in un contenitore Windows Docker Linux:To attach to a running process in a Linux Docker container:**

1. In Visual Studio, selezionare **Debug > Connetti a processo (CTRL-ALT-P)** per aprire la finestra di dialogo Connetti a **processo.**

![Menu Connetti a processo](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Impostare Il **tipo di connessione** su **Docker (contenitore Linux)**.
3. Selezionare Trova... per impostare la **destinazione della connessione** tramite la finestra di dialogo Seleziona **contenitore Docker.Select** **Find...** to set the Connection target via the Select Docker Container dialog box.

    È possibile eseguire il debug di un processo del contenitore Docker in locale o in remoto.
    
    **Per eseguire il debug locale di un processo contenitore Docker:To debug a Docker container process locally:**
    1. Impostare **l'host dell'interfaccia della riga di comando Docker** su **Computer locale**.
    1. Selezionare un contenitore in esecuzione a cui collegarsi dall'elenco e premere **OK**.
    
    ![Seleziona menu contenitore Docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. Per eseguire il debug di un processo contenitore Docker in remoto:**
    
    > [!NOTE] 
    > Sono disponibili due opzioni per la connessione remota a un processo in esecuzione in un contenitore Docker.There are two options for connecting remotely to a running process in a Docker container. La prima opzione, per utilizzare SSH, è ideale se nel computer locale non sono installati strumenti Docker.  Se si dispone di strumenti Docker installati localmente e si dispone di un daemon Docker configurato per accettare richieste remote, provare la seconda opzione, utilizzando un daemon Docker.

    1. ***Per connettersi a un computer remoto tramite SSH:***
        1. Selezionare **Aggiungi...** per connettersi a un sistema remoto.<br/>
        ![Connessione a un sistema remoto](../debugger/media/connect-remote-system.png "Connessione a un sistema remoto")
        1. Selezionare un contenitore in esecuzione a cui connettersi dopo la connessione a SSH o daemon e premere **OK**.

    
    1. ***Per impostare la destinazione su un contenitore remoto che esegue un processo tramite un [daemon DockerTo](https://docs.docker.com/engine/reference/commandline/dockerd/) set the target to a remote container running a process via a Docker daemon***
        1. Specificare l'indirizzo del daemon (ad esempio tramite TCP, IP e così via) in **Host Docker (facoltativo)** e fare clic sul collegamento di aggiornamento.
        1. Selezionare un contenitore in esecuzione a cui connettersi dopo la connessione al daemon e aver premuto **OK**.

4. Scegliere il processo contenitore corrispondente dall'elenco processi **disponibili** e selezionare **Connetti** per avviare il debug del processo contenitore di C' in Visual Studio.

    ![Menu di allega Docker completato](../debugger/media/docker-attach-complete.png "Menu di collegamento Per Linux Docker completato")
    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a>Connettersi a un processo in esecuzione in un contenitore Windows Docker

È possibile connettere il debugger di Visual Studio a un processo in esecuzione in un contenitore Windows Docker nel computer locale utilizzando la finestra di dialogo **Connetti a processo** .

> [!IMPORTANT]
> Per usare questa funzionalità con un processo .NET Core, è necessario installare il carico di lavoro di sviluppo multipiattaforma .NET Core e disporre dell'accesso locale al codice sorgente.

**Per connettersi a un processo in esecuzione in un contenitore Windows Docker:To attach to a running process in a Windows Docker container:**

1. In Visual Studio, selezionare **Debug > Connetti a processo** (oppure **CTRL-ALT-P**) per aprire la finestra di dialogo **Connetti a processo.**

   ![Menu Connetti a processo](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Impostare **Tipo di connessione** su **Docker (contenitore di Windows)**.
3. Selezionare **Trova...** per impostare la **destinazione della connessione** utilizzando la finestra di dialogo Seleziona **contenitore Docker** .

    > [!IMPORTANT]
    > Il processo di destinazione deve avere la stessa architettura del processore del contenitore Windows Docker in cui è in esecuzione.
    
   L'impostazione della destinazione su un contenitore remoto tramite SSH non è attualmente disponibile e può essere eseguita solo utilizzando un daemon Docker.
    
    ***Per impostare la destinazione su un contenitore remoto che esegue un processo tramite un [daemon DockerTo](https://docs.docker.com/engine/reference/commandline/dockerd/) set the target to a remote container running a process via a Docker daemon***
    1. Specificare l'indirizzo del daemon (ad esempio tramite TCP, IP e così via) in **Host Docker (facoltativo)** e fare clic sul collegamento di aggiornamento. 

    1. Selezionare un contenitore in esecuzione a cui connettersi dopo la connessione al daemon e scegliere OK.
    
4. Scegliere il processo contenitore corrispondente dall'elenco **Processi disponibili** e selezionare **Connetti** per avviare il debug del processo del contenitore di C.

    ![Menu di allega Docker completato](../debugger/media/docker-attach-complete-windows.png "Menu allega Docker di Windows completato")
    

5.  Scegliere il processo contenitore corrispondente dall'elenco dei processi disponibili e scegliere **Connetti** per avviare il debug del processo del contenitore di C.


::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a>Riattaccare a un processo

È possibile ricollegarsi rapidamente ai processi a cui si era precedentemente connessi scegliendo **Esegui funzionalità** > **di ricollegamento a processo** (**Maiusc**+**Alt**+**P**). Quando si sceglie questo comando, il debugger tenterà immediatamente di connettersi agli ultimi processi a cui ci si connette tentando tentando innanzitutto di trovare una corrispondenza con l'ID di processo precedente e, in caso di esito negativo, eseguendo la corrispondenza con il nome del processo precedente. Se non vengono trovate corrispondenze o se più processi hanno lo stesso nome, verrà aperta la finestra di dialogo **Connetti a processo** in modo da poter selezionare il processo corretto.

> [!NOTE]
> Il comando **Ricollega a elaborare** è disponibile a partire da Visual Studio 2017.The Reattach to Process command is available starting in Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a>Scenari di debug comuniCommon debugging scenarios

Per determinare se utilizzare **Connetti a processo** e a quale processo connettersi, nella tabella seguente sono illustrati alcuni scenari di debug comuni, con collegamenti a ulteriori istruzioni, se disponibili. (L'elenco non è esaustivo.)

Per alcuni tipi di app, ad esempio le app UWP (Universal Windows App), non ti connetti direttamente a un nome di processo, ma usi l'opzione di menu Esegui il **debug del pacchetto dell'app installato** in Visual Studio invece (vedi tabella).

Affinché il debugger possa connettersi a codice scritto in C++, è necessario che venga generato l'elemento `DebuggableAttribute`. È possibile aggiungere automaticamente questo elemento al codice mediante il collegamento all'opzione del linker [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

Per il debug di script sul lato client, il debug degli script deve essere abilitato nel browser. Per il debug di script sul lato client in Chrome, scegli **Web kit** come tipo di codice e, a `chrome.exe --remote-debugging-port=9222` seconda del tipo di app, potrebbe essere necessario chiudere tutte le istanze di Chrome e avviare il browser in modalità di debug (digitare da una riga di comando).

Per selezionare rapidamente un processo in esecuzione a cui connettersi, in Visual Studio digitare **CTRL**+**Alt**+**P**, quindi digitare la prima lettera del nome del processo.

|Scenario|Debug (metodo)|Nome del processo|Note e collegamenti|
|-|-|-|-|
|ASP.NET debug remoto 4 o 4.5 su un server IIS|Utilizzare strumenti remoti e **Connetti a processo**|*w3wp.exe*|Vedere [ASP.NET di debug remoto in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|ASP.NET Core di debug remoto in un server IIS|Utilizzare strumenti remoti e **Connetti a processo**|*dotnet.exe* o *appname.exe*|Per la distribuzione delle app, vedere [Pubblicare in IIS.](https://docs.asp.net/en/latest/publishing/iis.html) Per il debug, vedere [Debug remoto ASP.NET Core in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Eseguire il debug di script sul lato client in un server IIS locale, per i tipi di applicazione supportati |Usa **connessione per elaborare**|*chrome.exe*, *MicrosoftEdgeCP.exe*o *iexplore.exe*|Il debug degli script deve essere abilitato. Per Chrome, devi anche eseguire Chrome in modalità di debug e selezionare **Codice Webkit** nel campo **Allega a.**|
|Eseguire il debug di un'app In c'è, Visual Basic o C, nel computer locale|Utilizzare il debug standard (**F5**) o **Connetti a processo**|*\<nomeapp>.exe*|Nella maggior parte degli scenari, utilizzare il debug standard e non **Connetti a processo**.|
|Eseguire il debug remoto di un'app desktop di Windows|Remote tools|N/D| Vedi Eseguire il debug remoto di [un'app](../debugger/remote-debugging-csharp.md) di Visual Basic o di un'app in remoto per eseguire il debug di [un'app in C](../debugger/remote-debugging-cpp.md)|
|Debug .NET Core on Linux|Usa **connessione per elaborare**|*dotnet.exe*|Per utilizzare SSH, vedere [Remote debug .NET Core in esecuzione su Linux utilizzando SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). |
|Eseguire il debug di un'app ASP.NET nel computer locale dopo l'avvio dell'app senza il debuggerDebug an ASP.NET app on the local machine after you start the app without the debugger|Usa **connessione per elaborare**|*iiexpress.exe*|Ciò può essere utile per velocizzare il caricamento dell'app, ad esempio durante la profilatura. |
|Eseguire il debug di altri tipi di app supportati in un processo serverDebug other supported app types on a server process|Se il server è remoto, utilizzare gli strumenti remoti e **Connetti al processo**|*chrome.exe*, *iexplore.exe*o altri processi|Se necessario, utilizzare Monitoraggio risorse per identificare il processo. Vedere [Debug remoto](../debugger/remote-debugging.md).|
|Eseguire il debug remoto di un'applicazione Windows universale (UWP), OneCore, HoloLens o ioT app|Debug pacchetto dell'app installato|N/D|Vedere Eseguire il debug di [un pacchetto dell'app installato](debug-installed-app-package.md) anziché usare Connetti a **processo**|
|Eseguire il debug di un'applicazione Windows universale (UWP), OneCore, HoloLens o un'app IoT che non è stata avviata da Visual Studio|Debug pacchetto dell'app installato|N/D|Vedere Eseguire il debug di [un pacchetto dell'app installato](debug-installed-app-package.md) anziché usare Connetti a **processo**|

## <a name="use-debugger-features"></a>Usare le funzionalità del debuggerUse debugger features

Per usare tutte le funzionalità del debugger di Visual Studio (ad esempio colpire i punti di interruzione) quando ci si connette a un processo, l'app deve corrispondere esattamente all'origine e ai simboli locali. Ovvero, il debugger deve essere in grado di caricare i file di simboli corretti [(con estensione pdb).](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Per impostazione predefinita, questa operazione richiede una build di debug.

Per gli scenari di debug remoto, è necessario che il codice sorgente (o una copia del codice sorgente) sia già aperto in Visual Studio. I file binari dell'app compilati nel computer remoto devono provenire dalla stessa compilazione del computer locale.

In alcuni scenari di debug locale, è possibile eseguire il debug in Visual Studio senza accesso all'origine se i file di simboli corretti sono presenti con l'app. Per impostazione predefinita, questa operazione richiede una build di debug. Per ulteriori informazioni, consultate Specificare i [file di simboli e di origine.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Risolvere gli errori di connessione
 I processi in esecuzione a cui il debugger tenta di connettersi possono contenere uno o più tipi di codice. I tipi di codice a cui il debugger può connettersi vengono visualizzati e selezionati nella finestra di dialogo **Seleziona tipo di codice** .

 In alcuni casi il debugger riesce a connettersi a un tipo di codice ma non a un altro. Questa situazione può verificarsi quando si tenta di stabilire una connessione a un processo in esecuzione in un computer remoto, nel quale potrebbero essere stati installati i componenti per il debug remoto solo per alcuni tipi di codice. Può inoltre verificarsi quando si tenta di stabilire una connessione a due o più processi per il debug diretto di un database. Durante il debug SQL è supportata esclusivamente la connessione a un singolo processo.

 Se il debugger è in grado di connettersi ad alcuni tipi di codice, ma non a tutti, viene visualizzato un messaggio che identifica i tipi che non è riuscito a connettersi.

 Se il debugger riesce a connettersi ad almeno un tipo di codice, è possibile procedere con il debug del processo. Sarà possibile eseguire il debug solo dei tipi di codice con i quali è stata stabilita una connessione. Il codice non collegato nel processo verrà comunque eseguito, ma non sarà possibile impostare punti di interruzione, visualizzare dati o eseguire altre operazioni di debug su tale codice.

 Se si desiderano informazioni più specifiche sul motivo per cui il debugger non è riuscito a connettersi a un tipo di codice, provare a riconnettersi solo a tale tipo di codice.

 **Per ottenere informazioni specifiche sulla causa dell'errore di connessione a un tipo di codice:**

1. Disconnettersi dal processo. Scegliere **Scollega tutto**dal menu **Debug** .

1. Ricollega al processo, selezionando solo il tipo di codice che non è riuscito a connettere.

    1. Nella finestra di dialogo **Connetti a processo** selezionare il processo nell'elenco **Processi disponibili**.

    2. Selezionare **Seleziona**.

    3. Nella finestra di dialogo **Seleziona tipo di codice** selezionare il pulsante di opzione **Esegui il debug di questi tipi di codice** e il tipo di codice per cui si è verificato il problema di connessione. Deselezionare gli altri tipi di codice.

    4. Selezionare **OK**.

    5. Nella finestra di dialogo **Connetti a processo** selezionare **Connetti**.

    La connessione non verrà eseguita e verrà visualizzato un messaggio di errore specifico.

## <a name="see-also"></a>Vedere anche

- [Eseguire il debug di più processi](../debugger/debug-multiple-processes.md)
- [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Debug remoto](../debugger/remote-debugging.md)
