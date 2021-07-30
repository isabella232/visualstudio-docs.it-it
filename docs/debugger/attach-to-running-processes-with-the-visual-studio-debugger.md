---
title: Connettersi a processi in esecuzione con il debugger
description: Informazioni su come collegare il debugger Visual Studio a un processo in esecuzione in un computer locale o remoto.
ms.custom: SEO-VS-2020
ms.date: 06/28/2021
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 75654b8a20217fb99257eb1125852df6a81ca060
ms.sourcegitcommit: 879ba768364f3bfdaeb9004f740478489ab15c3a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2021
ms.locfileid: "114796242"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Associare a processi in esecuzione con il debugger di Visual Studio

È possibile collegare il debugger di Visual Studio a un processo in esecuzione in un computer locale o remoto. Quando il processo è in esecuzione, selezionare **Debug** Attach to Process (Esegui debug connessione a processo) o premere CTRL ALT p in Visual Studio e usare la finestra di dialogo Attach to Process (Collega a processo) per collegare  >   il debugger  +  +  al processo. 

È possibile  usare Associa a processo per eseguire il debug di app in esecuzione in computer locali o remoti, eseguire il debug di più processi contemporaneamente, eseguire il debug di app che non sono state create in Visual Studio o eseguire il debug di qualsiasi app non avviata da Visual Studio con il debugger collegato. Ad esempio, se si esegue un'app senza il debugger e si verifica un'eccezione, è possibile collegare il debugger al processo che esegue l'app e avviare il debug.

> [!TIP]
> Non si è certi di usare **Associa a processo per** lo scenario di debug? Vedere [Scenari di debug comuni.](#BKMK_Scenarios)

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Connettersi a un processo in esecuzione nel computer locale

Per ricollegare rapidamente a un processo a cui è stato collegato in precedenza, vedere [Ricollegare a un processo.](#BKMK_reattach)

**Per connettersi a un processo nel computer locale:**

1. In Visual Studio debug associa a processo  >   (o premere **CTRL** + **ALT** + **P**)  per aprire la finestra di dialogo Associa a processo .

1. Controllare il **tipo di connessione**.

   Nella maggior parte degli scenari è possibile usare **default.** Alcuni scenari possono richiedere un tipo di connessione diverso. Per altre informazioni, vedere le altre sezioni di questo articolo o [Scenari di debug comuni.](#BKMK_Scenarios)

1. Impostare il **nome del computer locale** come destinazione della connessione.

   ![Screenshot della finestra di dialogo Associa a processo con la destinazione della connessione impostata sul nome del computer locale.](../debugger/media/DBG_Basics_Attach_To_Process.png)

1. **Nell'elenco Processi disponibili** individuare e selezionare il processo o i processi a cui connettersi.

   - Per selezionare rapidamente un processo, digitarne il nome o la prima lettera nella **casella Filtra** processi.

   - Se non si conosce il nome del processo, esplorare l'elenco o vedere Scenari di [debug comuni](#BKMK_Scenarios) per alcuni nomi di processi comuni.

   >[!TIP]
   >I processi possono essere avviati  e arrestati in background mentre la finestra di dialogo Associa a processo è aperta, pertanto l'elenco dei processi in esecuzione potrebbe non essere sempre corrente. È possibile selezionare **Aggiorna** in qualsiasi momento per visualizzare l'elenco corrente.

1. Nel campo **Collega a verificare** che sia elencato il tipo di codice di cui si intende eseguire il debug. L'impostazione **automatica** predefinita funziona per la maggior parte dei tipi di app.

   Se si usa il **tipo di** connessione Predefinito, è possibile selezionare manualmente il tipo di codice a cui connettersi. In caso contrario, **l'opzione** Seleziona potrebbe essere disabilitata.

   Per selezionare manualmente i tipi di codice:
   1. Fare clic su **Seleziona**.
   1. Nella finestra **di dialogo Seleziona tipo di** codice selezionare Esegui debug di questi tipi di **codice**.
      Se si verifica un errore quando si tenta di connettersi [](../debugger/select-code-type-dialog-box.md) a un processo nell'elenco, è possibile usare la finestra di dialogo Seleziona tipo di codice per risolvere [il](#BKMK_Troubleshoot_attach_errors) problema.
   1. Selezionare i tipi di codice di cui si vuole eseguire il debug.
   1. Selezionare **OK**.

1. Selezionare **Allega**.

>[!NOTE]
>È possibile essere collegati a più app per il debug, ma nel debugger è attiva una sola app alla volta. È possibile impostare l'app attiva nella barra Visual Studio **posizione di debug** o nella **finestra** Processi.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Connettersi a un processo in un computer remoto

È anche possibile selezionare un  computer remoto nella finestra di dialogo Associa a processo , visualizzare un elenco dei processi disponibili in esecuzione nel computer e connettersi a uno o più processi per il debug. Il debugger remoto (*msvsmon.exe*) deve essere in esecuzione nel computer remoto. Per altre informazioni, vedere [Debug remoto.](../debugger/remote-debugging.md)

Per istruzioni più complete per il debug ASP.NET applicazioni distribuite in IIS, vedere Debug remoto ASP.NET [in un computer IIS remoto.](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)

**Per connettersi a un processo in esecuzione in un computer remoto:**

1. In Visual Studio debug associa a processo  >   (o premere **CTRL** + **ALT** + **P**)  per aprire la finestra di dialogo Associa a processo .

1. Controllare il **tipo di connessione**.

   Nella maggior parte degli scenari è possibile usare **default.** Alcuni scenari, ad esempio il debug di Linux o di un'app in contenitori, richiedono un tipo di connessione diverso. Per altre informazioni, vedere le altre sezioni di questo articolo o [Scenari di debug comuni.](#BKMK_Scenarios)

1. Nella casella **Destinazione connessione** selezionare il computer remoto usando uno dei metodi seguenti:

   - Selezionare la freccia a discesa accanto a **Destinazione connessione** e selezionare il nome del computer dall'elenco a discesa.
   - Digitare il nome del computer nella **casella Destinazione connessione** e premere **INVIO.**

     Verificare che Visual Studio la porta necessaria al nome del computer, che viene visualizzato nel formato: **\<remote computer name> :p ort**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Se non è possibile connettersi usando il nome del computer remoto, provare a usare l'indirizzo IP e la porta , ad esempio `123.45.678.9:4022` . 4024 è la porta predefinita per il debugger remoto Visual Studio 2019 x64. Per altre assegnazioni di porta del debugger remoto, vedere [Assegnazioni delle porte del debugger remoto.](remote-debugger-port-assignments.md)

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Se non è possibile connettersi usando il nome del computer remoto, provare a usare l'indirizzo IP e la porta , ad esempio `123.45.678.9:4022` . 4022 è la porta predefinita per il debugger remoto Visual Studio 2017 x64. Per altre assegnazioni di porta del debugger remoto, vedere [Assegnazioni delle porte del debugger remoto.](remote-debugger-port-assignments.md)

     ::: moniker-end

   - Selezionare il **pulsante** Trova accanto alla **casella Destinazione connessione** per aprire la finestra di **dialogo** Connessioni remote. Nella **finestra di** dialogo Connessioni remote sono elencati tutti i dispositivi presenti nella subnet locale o direttamente collegati al computer. Potrebbe essere necessario [aprire la porta UDP 3702](../debugger/remote-debugger-port-assignments.md) nel server per individuare i dispositivi remoti. Selezionare il computer o il dispositivo desiderato e quindi fare clic su **Seleziona**.

   > [!NOTE]
   > **L'impostazione Tipo di** connessione viene mantenuta tra le sessioni di debug. **L'impostazione Destinazione connessione** viene mantenuta tra le sessioni di debug solo se si è verificata una connessione di debug con tale destinazione.

3. Fare **clic su** Aggiorna per popolare **l'elenco Processi** disponibili.

    >[!TIP]
    >I processi possono essere avviati  e arrestati in background mentre la finestra di dialogo Associa a processo è aperta, pertanto l'elenco dei processi in esecuzione potrebbe non essere sempre corrente. È possibile selezionare **Aggiorna** in qualsiasi momento per visualizzare l'elenco corrente.

4. **Nell'elenco Processi disponibili** individuare e selezionare il processo o i processi a cui connettersi.

   - Per selezionare rapidamente un processo, digitarne il nome o la prima lettera nella **casella Filtra** processi.

   - Se non si conosce il nome del processo, esplorare l'elenco o vedere Scenari di [debug comuni](#BKMK_Scenarios) per alcuni nomi di processi comuni.

   - Per trovare i processi in esecuzione con tutti gli account utente, selezionare la casella di controllo **Mostra processi di tutti** gli utenti .

     >[!NOTE]
     >Se si tenta di connettersi a un processo appartenente a un account utente non attendibile, verrà visualizzata una finestra di dialogo contenente un avviso di sicurezza per chiedere conferma dell'operazione. Per altre informazioni, vedere [avviso di sicurezza: La connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non si è certi della loro provenienza e del loro stato, non connettersi al processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. Nel campo **Collega a verificare** che sia elencato il tipo di codice di cui si intende eseguire il debug. L'impostazione **automatica** predefinita funziona per la maggior parte dei tipi di app.

   Se si usa il **tipo di** connessione Predefinito, è possibile selezionare manualmente il tipo di codice a cui connettersi. In caso contrario, **l'opzione** Seleziona potrebbe essere disabilitata.

   Per selezionare manualmente i tipi di codice:
   1. Fare clic su **Seleziona**.
   1. Nella finestra **di dialogo Seleziona tipo di** codice selezionare Esegui debug di questi tipi di **codice**.
      Se si verifica un errore quando si tenta di connettersi [](../debugger/select-code-type-dialog-box.md) a un processo nell'elenco, è possibile usare la finestra di dialogo Seleziona tipo di codice per risolvere [il](#BKMK_Troubleshoot_attach_errors) problema.
   1. Selezionare **OK**.

6. Selezionare **Allega**.

>[!NOTE]
>È possibile essere collegati a più app per il debug, ma nel debugger è attiva una sola app alla volta. È possibile impostare l'app attiva nella barra Visual Studio **posizione di debug** o nella **finestra** Processi.

In alcuni casi, quando si esegue il debug in una  sessione di Desktop remoto (Servizi terminal), l'elenco Processi disponibili non visualizza tutti i processi disponibili. Se si esegue Visual Studio come utente con un account utente  limitato, l'elenco Processi disponibili non mostrerà i processi in esecuzione in sessione 0. sessione 0 viene usato per i servizi e altri processi server, tra cui *w3wp.exe*. È possibile risolvere il problema eseguendo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con un account amministratore o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalla console del server invece di una sessione di Servizi Terminal.

Se non è possibile adottare una di queste soluzioni alternative, una terza opzione consiste nel connettersi al processo eseguendo `vsjitdebugger.exe -p <ProcessId>` dalla riga di comando di Windows. È possibile determinare l'ID processo *usandotlist.exe*. Per ottenere *tlist.exe*, scaricare e installare gli strumenti di debug per Windows disponibili in [Download di WDK e WinDbg](/windows-hardware/drivers/download-the-wdk).

## <a name="attach-to-a-net-core-process-running-on-azure-app-service-windows"></a>Connettersi a un processo .NET Core in esecuzione Servizio app di Azure (Windows)

Se si esegue la pubblicazione in Servizio app di Azure (Windows), l'opzione Collega **debugger** è disponibile nel menu **...** in **Hosting**. Visual Studio tenta di collegare il debugger remoto all'istanza di Servizio app di Azure (Windows) in cui viene pubblicato il profilo.

:::image type="content" source="../debugger/media/attach-debugger-publish-profile.png" alt-text="Screenshot dell'opzione Collega debugger dalla pagina Riepilogo pubblicazione.":::

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Connettersi a un processo .NET Core in esecuzione in Linux tramite SSH

Per altre informazioni, vedere [Eseguire il debug remoto di .NET Core in esecuzione in Linux tramite SSH.](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)

::: moniker range=">= vs-2019"

## <a name="attach-to-a-process-running-on-a-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Connettersi a un processo in esecuzione in un contenitore Docker

A partire Visual Studio 2019, è possibile collegare il debugger Visual Studio a un processo in esecuzione in un contenitore Docker. Per un contenitore Docker .NET Core linux, vedere [Connettersi a un processo in esecuzione in un contenitore Docker Linux.](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container) Per un Windows contenitore Docker, vedere Connettersi a un processo in esecuzione Windows [contenitore Docker.](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-windows-docker-container)

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> Ricollegare a un processo

È possibile ricollegare rapidamente i processi a cui si era precedentemente collegati scegliendo **Debug** Ricollegare a processo  >   **(MAIUSC** + **ALT** + **P).** Quando si sceglie questo comando, il debugger tenterà immediatamente di connettersi agli ultimi processi a cui è stato eseguito il collegamento provando prima a trovare la corrispondenza con l'ID del processo precedente e, in caso di esito negativo, associando al nome del processo precedente. Se non viene trovata alcuna corrispondenza o se più  processi hanno lo stesso nome, verrà visualizzata la finestra di dialogo Associa a processo in modo da poter selezionare il processo corretto.

> [!NOTE]
> Il **comando Ricollegare a processo** è disponibile a partire Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Scenari di debug comuni

Per determinare se  usare La connessione a processo e il processo a cui connettersi, nella tabella seguente vengono illustrati alcuni scenari di debug comuni, con collegamenti ad altre istruzioni, se disponibili. L'elenco non è esaustivo.

Per alcuni tipi di app, ad esempio le app UWP (Universal Windows App), non ci si connette direttamente a un nome di processo, ma si usa invece l'opzione di menu Debug **Installed App Package** (Esegui debug pacchetto app installato) in Visual Studio (vedere la tabella).

Affinché il debugger possa connettersi a codice scritto in C++, è necessario che venga generato l'elemento `DebuggableAttribute`. È possibile aggiungere automaticamente questo elemento al codice mediante il collegamento all'opzione del linker [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

Per il debug di script sul lato client, il debug degli script deve essere abilitato nel browser. Per il debug di script lato client in Chrome, scegliere **JavaScript (Chrome)** o **JavaScript (Microsoft Edge - Chromium)** come tipo di codice e, a seconda del tipo di app, potrebbe essere necessario chiudere tutte le istanze di Chrome e avviare il browser in modalità di debug (digitare da una riga `chrome.exe --remote-debugging-port=9222` di comando). Nelle versioni precedenti di Visual Studio, il debugger di script per Chrome era **Web kit.**

Per selezionare rapidamente un processo in esecuzione a cui connettersi, in Visual Studio premere **CTRL** ALT P e quindi digitare la prima +  + lettera del nome del processo.

|Scenario|Metodo debug|Nome del processo|Note e collegamenti|
|-|-|-|-|
|Debug remoto ASP.NET 4 o 4.5 in un server IIS|Usare strumenti remoti e **Connettersi a processo**|*w3wp.exe*|Vedere [Debug remoto ASP.NET in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Eseguire il debug ASP.NET Core remoto in un server IIS|Usare strumenti remoti e **Connettersi a processo**|*w3wp.exe* o *dotnet.exe*|A partire da .NET Core 3, il *w3wp.exe* viene usato per il modello di [hosting in-app predefinito.](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) Per la distribuzione di app, [vedere Pubblicare in IIS.](/aspnet/core/host-and-deploy/iis/) Per informazioni più dettagliate, vedere [Debug remoto ASP.NET Core in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|Eseguire il debug di script lato client in un server IIS locale per i tipi di app supportati |Usare **Associa a processo**|*chrome.exe*, *MicrosoftEdgeCP.exe* o *iexplore.exe*|Il debug degli script deve essere abilitato. Per Chrome, è anche necessario eseguire Chrome in modalità di debug (digitare da una riga di comando) e selezionare `chrome.exe --remote-debugging-port=9222` **JavaScript (Chrome)** nel **campo Collega a.**|
|Eseguire il debug di un'app C#, Visual Basic o C++ nel computer locale|Usare il debug standard (**F5**) o **Connettersi a processo**|*\<appname>.exe*|Nella maggior parte degli scenari, usare il debug standard e non **Connettersi a processo.**|
|Eseguire il debug remoto di Windows'app desktop|Strumenti remoti|N/D| Vedere [Eseguire il debug remoto di un'app C# o Visual Basic](../debugger/remote-debugging-csharp.md) o Eseguire il debug remoto di [un'app C++](../debugger/remote-debugging-cpp.md)|
|Eseguire il debug di .NET Core in Linux|Usare **Associa a processo**|*dotnet.exe* o un nome di processo univoco|Per usare SSH, vedere [Eseguire il debug remoto di .NET Core in esecuzione in Linux tramite SSH.](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md) Per le app in contenitori, [vedere Connettersi a un processo in esecuzione in un contenitore Docker.](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container)|
|Eseguire il debug di un'app in contenitori|Usare **Associa a processo**|*dotnet.exe* o un nome di processo univoco|Vedere [Connettersi a un processo in esecuzione in un contenitore Docker](../debugger/attach-to-process-running-in-docker-container.md)|
|Eseguire il debug remoto di Python in Linux|Usare **Associa a processo**|*debugpy*|Vedere [Connettersi in remoto da Python Tools](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)|
|Eseguire il debug ASP.NET'app nel computer locale dopo l'avvio dell'app senza il debugger|Usare **Associa a processo**|*iiexpress.exe*|Ciò può essere utile per velocizzare il caricamento dell'app, ad esempio durante la profilatura. |
|Eseguire il debug di altri tipi di app supportati in un processo server|Se il server è remoto, usare strumenti remoti e **Connettersi a processo**|*chrome.exe*, *iexplore.exe* o altri processi|Se necessario, usare Monitoraggio risorse per identificare il processo. Vedere [Debug remoto](../debugger/remote-debugging.md).|
|Eseguire il debug remoto di un'app UWP (Universal Windows App), OneCore, HoloLens o IoT|Debug pacchetto dell'app installato|N/D|Vedere [Eseguire il debug di un pacchetto dell'app](debug-installed-app-package.md) installato invece di usare Associa a **processo**|
|Eseguire il debug di un'app UWP (Universal Windows App), OneCore, HoloLens o IoT che non è stata avviata da Visual Studio|Debug pacchetto dell'app installato|N/D|Vedere [Eseguire il debug di un pacchetto dell'app](debug-installed-app-package.md) installato invece di usare Associa a **processo**|

## <a name="use-debugger-features"></a>Usare le funzionalità del debugger

Per usare le funzionalità complete del debugger Visual Studio (ad esempio, raggiungere i punti di interruzione) quando ci si connette a un processo, l'app deve corrispondere esattamente all'origine e ai simboli locali. Ovvero, il debugger deve essere in grado di caricare i file [di simboli (con estensione pdb) corretti.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Per impostazione predefinita, questa operazione richiede una build di debug.

Per gli scenari di debug remoto, è necessario che il codice sorgente (o una copia del codice sorgente) sia già aperto in Visual Studio. I file binari dell'app compilata nel computer remoto devono derivare dalla stessa build del computer locale.

In alcuni scenari di debug locali è possibile eseguire il debug in Visual Studio senza accesso all'origine se con l'app sono presenti i file di simboli corretti. Per impostazione predefinita, questa operazione richiede una build di debug. Per altre informazioni, vedere Specificare [i file di simboli e di origine.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Risolvere gli errori di connessione

In alcuni scenari, il debugger potrebbe richiedere assistenza per identificare correttamente il tipo di codice di cui eseguire il debug. Se i valori di connessione sono impostati correttamente  (è possibile visualizzare il processo corretto nell'elenco Processi disponibili),  ma il debugger non riesce a connettersi, provare a selezionare il tipo di connessione più appropriato nell'elenco Tipo di connessione, che potrebbe essere necessario, ad esempio, se si esegue il debug di un'app Linux o Python. Se si usa il tipo di connessione Predefinito, è possibile selezionare in alternativa il tipo specifico di codice a cui connettersi, come descritto più avanti in questa sezione.

I processi in esecuzione a cui il debugger tenta di connettersi possono contenere uno o più tipi di codice. I tipi di codice a cui il debugger può connettersi vengono visualizzati e selezionati nella finestra di dialogo [Seleziona tipo di codice](../debugger/select-code-type-dialog-box.md) .

In alcuni casi il debugger riesce a connettersi a un tipo di codice ma non a un altro. In genere, ciò si verifica quando:

- Si tenta di connettersi a un processo in esecuzione in un computer remoto. nel quale potrebbero essere stati installati i componenti per il debug remoto solo per alcuni tipi di codice.
- Si tenta di connettersi a due o più processi per il debug diretto del database. Durante il debug SQL è supportata esclusivamente la connessione a un singolo processo.

Se il debugger è in grado di connettersi ad alcuni tipi di codice, ma non a tutti, viene visualizzato un messaggio che indica quali tipi non sono stati associati.

Se il debugger riesce a connettersi ad almeno un tipo di codice, è possibile procedere con il debug del processo. Sarà possibile eseguire il debug solo dei tipi di codice con i quali è stata stabilita una connessione. Il codice non associato nel processo verrà comunque eseguito, ma non sarà possibile impostare punti di interruzione, visualizzare i dati o eseguire altre operazioni di debug su tale codice.

Per informazioni più specifiche sui motivi per cui il debugger non è riuscito a connettersi a un tipo di codice, provare a ricollegare solo a tale tipo di codice.

**Per ottenere informazioni specifiche sulla causa dell'errore di connessione a un tipo di codice:**

1. Disconnettersi dal processo. Scegliere **Scollega** tutto dal menu **Debug**.

1. Ricollegare il processo, selezionando solo il tipo di codice che non è riuscito a connettersi.

    1. Nella finestra di dialogo **Connetti a processo** selezionare il processo nell'elenco **Processi disponibili**.

    2. Scegliere **Seleziona**.

    3. Nella finestra di dialogo **Seleziona tipo di codice** selezionare il pulsante di opzione **Esegui il debug di questi tipi di codice** e il tipo di codice per cui si è verificato il problema di connessione. Deselezionare gli altri tipi di codice.

    4. Selezionare **OK**.

    5. Nella finestra **di dialogo Collega a** processo selezionare **Collega**.

    La connessione non verrà eseguita e verrà visualizzato un messaggio di errore specifico.

## <a name="see-also"></a>Vedere anche

- [Eseguire il debug di più processi](../debugger/debug-multiple-processes.md)
- [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Debug remoto](../debugger/remote-debugging.md)
