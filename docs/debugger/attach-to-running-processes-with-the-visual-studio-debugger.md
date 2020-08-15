---
title: Connettersi ai processi in esecuzione con il debugger | Microsoft Docs
ms.custom: seodec18
ms.date: 06/12/2020
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
ms.openlocfilehash: f4b4a90cc06396f9fb6afb8a356385e966ed1b3d
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249212"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Associare a processi in esecuzione con il debugger di Visual Studio

È possibile collegare il debugger di Visual Studio a un processo in esecuzione in un computer locale o remoto. Al termine dell'esecuzione del processo, selezionare **debug**  >  **Connetti a processo** oppure premere **CTRL** + **ALT** + **P** in Visual Studio e usare la finestra di dialogo **Connetti a processo** per aggiungere il debugger al processo.

È possibile usare **Connetti a processo** per eseguire il debug di app in esecuzione in computer locali o remoti, eseguire il debug di più processi simultaneamente, eseguire il debug di app che non sono state create in Visual Studio o eseguire il debug di qualsiasi app non avviata da Visual Studio con il debugger collegato. Se, ad esempio, si esegue un'app senza il debugger e si raggiunge un'eccezione, è possibile connettersi al processo che esegue l'app e avviare il debug.

> [!TIP]
> Se non si è certi se usare **Connetti a processo** per lo scenario di debug, Vedere [scenari di debug comuni](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Connettersi a un processo in esecuzione nel computer locale

Per riconnettersi rapidamente a un processo collegato in precedenza, vedere [Riconnetti a un processo](#BKMK_reattach).

**Per connettersi a un processo nel computer locale:**

1. In Visual Studio selezionare **debug**  >  **Connetti a processo** (oppure premere **CTRL** + **ALT** + **P**) per aprire la finestra di dialogo **Connetti a processo** .

1. Verificare il **tipo di connessione**.

   Nella maggior parte degli scenari è possibile usare il **valore predefinito**. Alcuni scenari possono richiedere un tipo di connessione diverso. Per altre informazioni, vedere le altre sezioni di questo articolo o [scenari di debug comuni](#BKMK_Scenarios).

1. Impostare la **destinazione della connessione** sul nome del computer locale.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

1. Nell'elenco **processi disponibili** individuare e selezionare il processo o i processi a cui si desidera connettersi.

   - Per selezionare rapidamente un processo, digitarne il nome o la prima lettera nella casella **Filtra processi** .

   - Se non si conosce il nome del processo, esplorare l'elenco o vedere gli [scenari di debug comuni](#BKMK_Scenarios) per alcuni nomi di processo comuni.

   >[!TIP]
   >I processi possono essere avviati e arrestati in background mentre la finestra di dialogo **Connetti a processo** è aperta, pertanto l'elenco dei processi in esecuzione potrebbe non essere sempre aggiornato. È possibile selezionare **Aggiorna** in qualsiasi momento per visualizzare l'elenco corrente.

1. Nel campo **Connetti a** verificare che sia elencato il tipo di codice di cui si intende eseguire il debug. L'impostazione **automatica** predefinita funziona per la maggior parte dei tipi di app.

   Se si utilizza il tipo di connessione **predefinito** , è possibile selezionare manualmente il tipo di codice a cui si desidera connettersi. In caso contrario, l'opzione **Seleziona** potrebbe essere disabilitata.

   Per selezionare manualmente i tipi di codice:
   1. Fare clic su **Seleziona**.
   1. Nella finestra di dialogo **Seleziona tipo di codice** selezionare **Esegui il debug di questi tipi di codice**.
      Se si verifica un errore quando si tenta di connettersi a un processo nell'elenco, è possibile utilizzare la finestra di dialogo [Seleziona tipo di codice](../debugger/select-code-type-dialog-box.md) per [risolvere](#BKMK_Troubleshoot_attach_errors) il problema.
   1. Selezionare i tipi di codice di cui si vuole eseguire il debug.
   1. Selezionare **OK**.

1. Selezionare **Allega**.

>[!NOTE]
>È possibile essere collegati a più app per il debug, ma solo un'app è attiva nel debugger alla volta. È possibile impostare l'app attiva nella barra degli strumenti del **percorso di debug** di Visual Studio o nella finestra **processi** .

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Connettersi a un processo in un computer remoto

È inoltre possibile selezionare un computer remoto nella finestra di dialogo **Connetti a processo** , visualizzare un elenco dei processi disponibili in esecuzione in tale computer e connettersi a uno o più processi per il debug. Il debugger remoto (*msvsmon.exe*) deve essere in esecuzione nel computer remoto. Per ulteriori informazioni, vedere [Remote Debugging](../debugger/remote-debugging.md).

Per istruzioni più complete sul debug di applicazioni ASP.NET distribuite in IIS, vedere [Remote Debugging ASP.NET on a Remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Per connettersi a un processo in esecuzione in un computer remoto:**

1. In Visual Studio selezionare **debug**  >  **Connetti a processo** (oppure premere **CTRL** + **ALT** + **P**) per aprire la finestra di dialogo **Connetti a processo** .

1. Verificare il **tipo di connessione**.

   Nella maggior parte degli scenari è possibile usare il **valore predefinito**. Alcuni scenari, ad esempio il debug di Linux o di un'app in contenitori, richiedono un tipo di connessione diverso. Per altre informazioni, vedere le altre sezioni di questo articolo o [scenari di debug comuni](#BKMK_Scenarios).

1. Nella casella **destinazione connessione** selezionare il computer remoto utilizzando uno dei metodi seguenti:

   - Selezionare la freccia a discesa accanto a **destinazione connessione**e selezionare il nome del computer dall'elenco a discesa.
   - Digitare il nome del computer nella casella **destinazione connessione** e premere **invio**.

     Verificare che in Visual Studio venga aggiunta la porta richiesta al nome del computer, che viene visualizzato nel formato: ** \<remote computer name> :p Ort**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Se non è possibile connettersi usando il nome del computer remoto, provare a usare l'indirizzo IP e la porta (ad esempio, `123.45.678.9:4022` ). 4024 è la porta predefinita per Visual Studio 2019 x64 remote debugger. Per altre assegnazioni di porta del debugger remoto, vedere [assegnazioni di porta del debugger remoto](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Se non è possibile connettersi usando il nome del computer remoto, provare a usare l'indirizzo IP e la porta (ad esempio, `123.45.678.9:4022` ). 4022 è la porta predefinita per Visual Studio 2017 x64 remote debugger. Per altre assegnazioni di porta del debugger remoto, vedere [assegnazioni di porta del debugger remoto](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Selezionare il pulsante **trova** accanto alla casella **destinazione connessione** per aprire la finestra di dialogo **connessioni remote** . Nella finestra di dialogo **connessioni remote** sono elencati tutti i dispositivi presenti nella subnet locale o collegati direttamente al computer. Potrebbe essere necessario [aprire la porta UDP 3702](../debugger/remote-debugger-port-assignments.md) sul server per individuare i dispositivi remoti. Selezionare il computer o il dispositivo desiderato, quindi fare clic su **Seleziona**.

   > [!NOTE]
   > L'impostazione del **tipo di connessione** viene mantenute tra le sessioni di debug. L'impostazione della **destinazione della connessione** viene mantenute tra le sessioni di debug solo se si è verificata una connessione di debug corretta con tale destinazione.

3. Fare clic su **Aggiorna** per popolare l'elenco **processi disponibili** .

    >[!TIP]
    >I processi possono essere avviati e arrestati in background mentre la finestra di dialogo **Connetti a processo** è aperta, pertanto l'elenco dei processi in esecuzione potrebbe non essere sempre aggiornato. È possibile selezionare **Aggiorna** in qualsiasi momento per visualizzare l'elenco corrente.

4. Nell'elenco **processi disponibili** individuare e selezionare il processo o i processi a cui si desidera connettersi.

   - Per selezionare rapidamente un processo, digitarne il nome o la prima lettera nella casella **Filtra processi** .

   - Se non si conosce il nome del processo, esplorare l'elenco o vedere gli [scenari di debug comuni](#BKMK_Scenarios) per alcuni nomi di processo comuni.

   - Per trovare i processi in esecuzione con tutti gli account utente, selezionare la casella di controllo **Mostra i processi di tutti gli utenti** .

     >[!NOTE]
     >Se si tenta di connettersi a un processo appartenente a un account utente non attendibile, verrà visualizzata una finestra di dialogo contenente un avviso di sicurezza per chiedere conferma dell'operazione. Per altre informazioni [, vedere Avviso di sicurezza: la connessione a un processo di proprietà di un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non si è certi di, non connettersi a questo processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. Nel campo **Connetti a** verificare che sia elencato il tipo di codice di cui si intende eseguire il debug. L'impostazione **automatica** predefinita funziona per la maggior parte dei tipi di app.

   Se si utilizza il tipo di connessione **predefinito** , è possibile selezionare manualmente il tipo di codice a cui si desidera connettersi. In caso contrario, l'opzione **Seleziona** potrebbe essere disabilitata.

   Per selezionare manualmente i tipi di codice:
   1. Fare clic su **Seleziona**.
   1. Nella finestra di dialogo **Seleziona tipo di codice** selezionare **Esegui il debug di questi tipi di codice**.
      Se si verifica un errore quando si tenta di connettersi a un processo nell'elenco, è possibile utilizzare la finestra di dialogo [Seleziona tipo di codice](../debugger/select-code-type-dialog-box.md) per [risolvere](#BKMK_Troubleshoot_attach_errors) il problema.
   1. Selezionare **OK**.

6. Selezionare **Allega**.

>[!NOTE]
>È possibile essere collegati a più app per il debug, ma solo un'app è attiva nel debugger alla volta. È possibile impostare l'app attiva nella barra degli strumenti del **percorso di debug** di Visual Studio o nella finestra **processi** .

In alcuni casi, quando si esegue il debug in una sessione di Desktop remoto (Servizi terminal), nell'elenco **processi disponibili** non verranno visualizzati tutti i processi disponibili. Se si esegue Visual Studio come utente che dispone di un account utente limitato, nell'elenco **processi disponibili** non verranno visualizzati i processi in esecuzione nella sessione 0. La sessione 0 viene utilizzata per i servizi e altri processi del server, tra cui *w3wp.exe*. È possibile risolvere il problema eseguendo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con un account amministratore o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalla console del server invece di una sessione di Servizi Terminal.

Se non è possibile adottare una di queste soluzioni alternative, una terza opzione consiste nel connettersi al processo eseguendo `vsjitdebugger.exe -p <ProcessId>` dalla riga di comando di Windows. È possibile determinare l'ID processo utilizzando *tlist.exe*. Per ottenere *tlist.exe*, scaricare e installare gli strumenti di debug per Windows disponibili in [Download di WDK e WinDbg](/windows-hardware/drivers/download-the-wdk).

::: moniker range=">= vs-2019"

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Connettersi a un processo .NET Core in esecuzione su Linux tramite SSH

Per altre informazioni, vedere [eseguire il debug remoto di .NET Core in esecuzione su Linux tramite SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Connettersi a un processo in esecuzione in un contenitore Docker Linux

È possibile collegare il debugger di Visual Studio a un processo in esecuzione in un contenitore Docker di Linux .NET Core nel computer locale o remoto usando la finestra **di dialogo Connetti a processo** .

> [!IMPORTANT]
> Per usare questa funzionalità, è necessario installare il carico di lavoro sviluppo multipiattaforma .NET Core e avere accesso locale al codice sorgente.

**Per connettersi a un processo in esecuzione in un contenitore Docker Linux:**

1. In Visual Studio selezionare **Debug > Connetti a processo (CTRL + ALT + P)** per aprire la finestra di dialogo **Connetti a processo** .

![Menu Connetti a processo](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Impostare il **tipo di connessione** su **Docker (contenitore Linux)**.
3. Selezionare **trova..** . per impostare la **destinazione della connessione** tramite la finestra di dialogo **Seleziona contenitore Docker** .

    È possibile eseguire il debug di un processo del contenitore Docker in locale o in remoto.
    
    **Per eseguire il debug di un processo contenitore Docker in locale:**
    1. Impostare host dell'interfaccia della riga di comando **Docker** sul **computer locale**.
    1. Selezionare un contenitore in esecuzione a cui connettersi dall'elenco e fare clic su **OK**.
    
    ![Selezionare il menu contenitore Docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. per eseguire il debug remoto di un processo del contenitore docker:**
    
    > [!NOTE] 
    > Sono disponibili due opzioni per la connessione remota a un processo in esecuzione in un contenitore docker. La prima opzione, per usare SSH, è ideale se gli strumenti Docker non sono installati nel computer locale.  Se gli strumenti Docker sono installati localmente e si ha un daemon Docker configurato per accettare le richieste remote, provare la seconda opzione usando un daemon docker.

    1. ***Per connettersi a un computer remoto tramite SSH:***
        1. Selezionare **Aggiungi** per connettersi a un sistema remoto.<br/>
        ![Connettersi a un sistema remoto](../debugger/media/connect-remote-system.png "Connettersi a un sistema remoto")
        1. Selezionare un contenitore in esecuzione a cui connettersi dopo aver eseguito correttamente la connessione a SSH o daemon e quindi fare clic su **OK**.

    1. ***Per impostare la destinazione su un contenitore remoto che esegue un processo tramite un [daemon Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
        1. Specificare l'indirizzo del daemon, ad esempio tramite TCP, IP e così via, in **Docker host (facoltativo)** e fare clic sul collegamento Refresh (Aggiorna).
        1. Selezionare un contenitore in esecuzione a cui connettersi dopo la connessione al daemon e fare clic su **OK**.

4. Scegliere il processo contenitore corrispondente nell'elenco dei **processi disponibili** e selezionare **Connetti** per avviare il debug del processo contenitore C# in Visual Studio.

    ![Menu Docker collegato completato](../debugger/media/docker-attach-complete.png "Menu Docker collegato Linux completato")    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a> Connettersi a un processo in esecuzione in un contenitore Docker di Windows

È possibile collegare il debugger di Visual Studio a un processo in esecuzione in un contenitore Docker di Windows sul computer locale usando la finestra **di dialogo Connetti a processo** .

> [!IMPORTANT]
> Per usare questa funzionalità con un processo di .NET Core, è necessario installare il carico di lavoro sviluppo multipiattaforma .NET Core e avere accesso locale al codice sorgente.

**Per connettersi a un processo in esecuzione in un contenitore Docker di Windows:**

1. In Visual Studio selezionare **Debug > Connetti a processo** (o **CTRL + ALT + P**) per aprire la finestra di dialogo **Connetti a processo** .

   ![Menu Connetti a processo](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Impostare il **tipo di connessione** su **Docker (contenitore di Windows)**.
3. Selezionare **trova..** . per impostare la **destinazione della connessione** usando la finestra di dialogo **Seleziona contenitore Docker** .

    > [!IMPORTANT]
    > Il processo di destinazione deve avere la stessa architettura del processore del contenitore di Windows Docker in cui è in esecuzione.
    
   L'impostazione della destinazione su un contenitore remoto tramite SSH non è attualmente disponibile e può essere eseguita solo tramite un daemon docker.
    
    ***Per impostare la destinazione su un contenitore remoto che esegue un processo tramite un [daemon Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
    1. Specificare l'indirizzo del daemon, ad esempio tramite TCP, IP e così via, in **Docker host (facoltativo)** e fare clic sul collegamento Refresh (Aggiorna). 

    1. Selezionare un contenitore in esecuzione a cui connettersi dopo la connessione al daemon e scegliere OK.
    
4. Scegliere il processo contenitore corrispondente nell'elenco dei **processi disponibili** e selezionare **Connetti** per avviare il debug del processo contenitore C#.

    ![Menu Docker collegato completato](../debugger/media/docker-attach-complete-windows.png "Menu di alconnessione Docker Windows completato")

5.  Scegliere il processo contenitore corrispondente nell'elenco dei processi disponibili e scegliere **Connetti** per avviare il debug del processo contenitore C#.

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> Riconnetti a un processo

È possibile ricollegare rapidamente ai processi a cui è stato precedentemente associato scegliendo **debug**  >  **Riconnetti a processo** (**MAIUSC** + **ALT** + **P**). Quando si sceglie questo comando, il debugger tenterà immediatamente di connettersi agli ultimi processi a cui si è connessi tentando innanzitutto di trovare la corrispondenza con l'ID del processo precedente e, in caso di esito negativo, eseguendo la corrispondenza con il nome del processo precedente. Se non vengono trovate corrispondenze o se più processi hanno lo stesso nome, verrà aperta la finestra **di dialogo Connetti a processo** , in modo da poter selezionare il processo corretto.

> [!NOTE]
> Il comando **Riconnetti a processo** è disponibile a partire da Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Scenari di debug comuni

Per determinare se usare **Connetti a processo** e il processo a cui collegarsi, nella tabella seguente vengono illustrati alcuni scenari di debug comuni, con collegamenti ad altre istruzioni, se disponibili. (L'elenco non è esaustivo).

Per alcuni tipi di app, ad esempio app di Windows universale (UWP), non è possibile connettersi direttamente al nome di un processo, ma usare l'opzione di menu **debug del pacchetto dell'app installato** in Visual Studio (vedere la tabella).

Affinché il debugger possa connettersi a codice scritto in C++, è necessario che venga generato l'elemento `DebuggableAttribute`. È possibile aggiungere automaticamente questo elemento al codice mediante il collegamento all'opzione del linker [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

Per il debug di script sul lato client, è necessario abilitare il debug degli script nel browser. Per il debug di script lato client in Chrome, scegliere **JavaScript (Chrome)** o **JavaScript (Microsoft Edge-Chromium)** come tipo di codice e, a seconda del tipo di app, potrebbe essere necessario chiudere tutte le istanze di Chrome e avviare il browser in modalità di debug (digitare `chrome.exe --remote-debugging-port=9222` da una riga di comando). Nelle versioni precedenti di Visual Studio, il debugger di script per Chrome era il **Web Kit**.

Per selezionare rapidamente un processo in esecuzione a cui connettersi, in Visual Studio, digitare **CTRL** + **ALT** + **P**, quindi digitare la prima lettera del nome del processo.

|Scenario|Metodo Debug|Nome del processo|Note e collegamenti|
|-|-|-|-|
|Debug remoto ASP.NET 4 o 4,5 su un server IIS|USA Remote Tools e **Connetti a processo**|*w3wp.exe*|Vedere [Remote Debugging ASP.NET on a Remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|ASP.NET Core di debug remoto in un server IIS|USA Remote Tools e **Connetti a processo**|*w3wp.exe* o *dotnet.exe*|A partire da .NET Core 3, il processo di *w3wp.exe* viene usato per il [modello di hosting predefinito in-app](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models). Per la distribuzione di app, vedere [pubblicare in IIS](/aspnet/core/host-and-deploy/iis/). Per informazioni più dettagliate, vedere [Remote Debugging ASP.NET Core in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|Eseguire il debug di script lato client in un server IIS locale, per i tipi di app supportati |Usare **Connetti a processo**|*chrome.exe*, *MicrosoftEdgeCP.exe*o *iexplore.exe*|È necessario abilitare il debug degli script. Per Chrome, è inoltre necessario eseguire Chrome in modalità di debug (digitare `chrome.exe --remote-debugging-port=9222` da una riga di comando) e selezionare **JavaScript (Chrome)** nel campo **Connetti a** .|
|Eseguire il debug di un'app C#, Visual Basic o C++ nel computer locale|Usare il debug standard (**F5**) o **Connetti a processo**|*\<appname>. exe*|Nella maggior parte degli scenari, utilizzare il debug standard e non la **connessione al processo**.|
|Eseguire il debug remoto di un'app desktop di Windows|Strumenti remoti|N/D| Vedere [eseguire il debug remoto di un'app C# o Visual Basic](../debugger/remote-debugging-csharp.md) o [eseguire il debug remoto di un'app C++](../debugger/remote-debugging-cpp.md)|
|Eseguire il debug di .NET Core in Linux|Usare **Connetti a processo**|*dotnet.exe*|Per usare SSH, vedere [eseguire il debug remoto di .NET Core in esecuzione su Linux tramite SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). Per le app in contenitori, vedere le sezioni precedenti di questo articolo.|
|Debug remoto di Python in Linux|Usare **Connetti a processo**|*debugpy*|Vedere [connettersi in remoto da strumenti Python](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)|
|Eseguire il debug di un'app ASP.NET nel computer locale dopo avere avviato l'app senza il debugger|Usare **Connetti a processo**|*iiexpress.exe*|Questa operazione può essere utile per velocizzare il caricamento dell'app, ad esempio quando si esegue la profilatura. |
|Eseguire il debug di altri tipi di app supportati in un processo server|Se il server è remoto, utilizzare Remote Tools e **Connetti a processo**|*chrome.exe*, *iexplore.exe*o altri processi|Se necessario, utilizzare Monitoraggio risorse per facilitare l'identificazione del processo. Vedere [Debug remoto](../debugger/remote-debugging.md).|
|Eseguire il debug remoto di un'app di Windows universale (UWP), OneCore, HoloLens o Internet.|Debug pacchetto dell'app installato|N/D|Vedere [eseguire il debug di un pacchetto dell'app installato](debug-installed-app-package.md) invece di usare **Connetti a processo**|
|Eseguire il debug di un'app di Windows universale (UWP), OneCore, HoloLens o Internet, che non è stata avviata da Visual Studio|Debug pacchetto dell'app installato|N/D|Vedere [eseguire il debug di un pacchetto dell'app installato](debug-installed-app-package.md) invece di usare **Connetti a processo**|

## <a name="use-debugger-features"></a>Usare le funzionalità del debugger

Per usare le funzionalità complete del debugger di Visual Studio, ad esempio il raggiungimento di punti di interruzione, quando ci si connette a un processo, l'app deve corrispondere esattamente all'origine e ai simboli locali. Ovvero, il debugger deve essere in grado di caricare i [file di simboli (con estensione pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)corretti. Per impostazione predefinita, è necessaria una compilazione di debug.

Per gli scenari di debug remoto, è necessario che il codice sorgente (o una copia del codice sorgente) sia già aperto in Visual Studio. I file binari dell'app compilata nel computer remoto devono provenire dalla stessa build del computer locale.

In alcuni scenari di debug locale è possibile eseguire il debug in Visual Studio senza accedere all'origine se sono presenti i file di simboli corretti con l'app. Per impostazione predefinita, è necessaria una compilazione di debug. Per altre informazioni, vedere [specificare i file di simboli e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Risolvere gli errori di connessione

In alcuni scenari, il debugger potrebbe richiedere assistenza per identificare correttamente il tipo di codice di cui eseguire il debug. Se i valori di connessione sono impostati correttamente (è possibile visualizzare il processo corretto nell'elenco **processi disponibili** ), ma il debugger non riesce a connettersi, provare a selezionare il tipo di connessione più appropriato nell'elenco **tipo di connessione** , che potrebbe essere necessario, ad esempio, se si sta eseguendo il debug di un'app Linux o Python. Se si usa il tipo di connessione predefinito, è possibile selezionare in alternativa il tipo specifico di codice a cui connettersi, come descritto più avanti in questa sezione.

I processi in esecuzione a cui il debugger tenta di connettersi possono contenere uno o più tipi di codice. I tipi di codice a cui il debugger può connettersi vengono visualizzati e selezionati nella finestra di dialogo [Seleziona tipo di codice](../debugger/select-code-type-dialog-box.md) .

In alcuni casi il debugger riesce a connettersi a un tipo di codice ma non a un altro. Questa situazione si verifica in genere quando:

- Si tenta di connettersi a un processo in esecuzione in un computer remoto. nel quale potrebbero essere stati installati i componenti per il debug remoto solo per alcuni tipi di codice.
- Si tenta di connettersi a due o più processi per il debug diretto di un database. Durante il debug SQL è supportata esclusivamente la connessione a un singolo processo.

Se il debugger è in grado di connettersi solo ad alcuni tipi di codice, viene visualizzato un messaggio che identifica i tipi che non sono stati collegati.

Se il debugger riesce a connettersi ad almeno un tipo di codice, è possibile procedere con il debug del processo. Sarà possibile eseguire il debug solo dei tipi di codice con i quali è stata stabilita una connessione. Il codice non collegato del processo verrà comunque eseguito, ma non sarà possibile impostare punti di interruzione, visualizzare dati o eseguire altre operazioni di debug su tale codice.

Se si desiderano informazioni più specifiche sui motivi per cui il debugger non è riuscito a connettersi a un tipo di codice, provare a riconnettersi solo a tale tipo di codice.

**Per ottenere informazioni specifiche sulla causa dell'errore di connessione a un tipo di codice:**

1. Disconnettersi dal processo. Scegliere **Disconnetti tutto**dal menu **debug** .

1. Riconnettersi al processo, selezionando solo il tipo di codice che non è riuscito a connettersi.

    1. Nella finestra di dialogo **Connetti a processo** selezionare il processo nell'elenco **Processi disponibili**.

    2. Scegliere **Seleziona**.

    3. Nella finestra di dialogo **Seleziona tipo di codice** selezionare il pulsante di opzione **Esegui il debug di questi tipi di codice** e il tipo di codice per cui si è verificato il problema di connessione. Deselezionare gli altri tipi di codice.

    4. Selezionare **OK**.

    5. Nella finestra di dialogo **Connetti a processo** selezionare **Connetti**.

    La connessione non verrà eseguita e verrà visualizzato un messaggio di errore specifico.

## <a name="see-also"></a>Vedere anche

- [Debug di più processi](../debugger/debug-multiple-processes.md)
- [Debug just-in-Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Debug remoto](../debugger/remote-debugging.md)
