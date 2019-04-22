---
title: Collegamento a processi in esecuzione con il debugger | Microsoft Docs
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
ms.openlocfilehash: dad698f2ba660b6848e614f13751335894a17ae0
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2019
ms.locfileid: "59366406"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Associare a processi in esecuzione con il debugger di Visual Studio
È possibile collegare il debugger di Visual Studio a un processo in esecuzione in un computer locale o remoto. Dopo l'esecuzione del processo, selezionare **Debug** > **Connetti a processo** oppure premere **Ctrl**+**Alt** + **P** in Visual Studio e utilizzare il **Connetti a processo** finestra di dialogo per collegare il debugger al processo.

È possibile usare **Connetti a processo** per eseguire il debug delle App in esecuzione su computer locali o remoti, eseguire il debug di più processi contemporaneamente, il debug delle App che non sono state create in Visual Studio o il debug di qualsiasi app non è stato avviato da Visual Studio con il debugger collegato. Ad esempio, se si sta eseguendo un'app senza il debugger e verificata un'eccezione, si può quindi collegare il debugger al processo di esecuzione dell'app e iniziare il debug.

> [!TIP]
> Non si è sicuri se usare **Connetti a processo** per lo scenario di debug? Visualizzare [comuni scenari di debug](#BKMK_Scenarios).

##  <a name="BKMK_Attach_to_a_running_process"></a> Connettersi a un processo in esecuzione nel computer locale

Per riconnettere rapidamente un processo si era connessi in precedenza, vedere [riassocia a un processo](#BKMK_reattach).

Per eseguire il debug di un processo in un computer remoto, vedere [connettersi a un processo in un computer remoto](#BKMK_Attach_to_a_process_on_a_remote_computer).

**Per connettersi a un processo nel computer locale:**

1. In Visual Studio, selezionare **Debug** > **Connetti a processo** (o premere **Ctrl**+**Alt** + **P**) per aprire la **Connetti a processo** nella finestra di dialogo.

   **Tipo di connessione** deve essere impostata su **predefinito**. **Destinazione della connessione** deve essere il nome del computer locale.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. Nel **processi disponibili** elencare, trovare e selezionare il processo o i processi di cui si desidera stabilire una connessione.

   - Per selezionare rapidamente un processo, digitare il nome o la prima lettera di **Filtra processi** casella.

   - Se non si conosce il nome del processo, scorrere l'elenco, oppure vedere [comuni scenari di debug](#BKMK_Scenarios) per alcuni nomi di processo comuni.

   >[!TIP]
   >I processi possono avviare e arrestare in background mentre il **Connetti a processo** nella finestra di dialogo è aperta, pertanto l'elenco dei processi in esecuzione potrebbe non essere sempre corrente. È possibile selezionare **Aggiorna** in qualsiasi momento per visualizzare l'elenco corrente.

3. Nel **Collega a** campo, assicurarsi che sia elencato il tipo di codice si prevede di eseguire il debug. Il valore predefinito **automatica** l'impostazione funziona per la maggior parte dei tipi di app.

   Per selezionare manualmente i tipi di codice:
   1. Fare clic su **Seleziona**.
   1. Nel **Seleziona tipo di codice** finestra di dialogo, selezionare **eseguire il Debug di questi tipi di codice**.
   1. Selezionare i tipi di codice da sottoporre a debug.
   1. Scegliere **OK**.

4. Selezionare **collegare**.

>[!NOTE]
>È possibile collegare più App per il debug, ma solo un'app è attiva nel debugger alla volta. È possibile impostare l'app attiva in Visual Studio **posizione di Debug** sulla barra degli strumenti oppure **processi** finestra.

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Connettersi a un processo in un computer remoto

È anche possibile selezionare un computer remoto nel **Connetti a processo** nella finestra di dialogo consente di visualizzare un elenco di processi disponibili in esecuzione in tale computer e collegare a una o più dei processi per il debug. Il debugger remoto (*msvsmon.exe*) deve essere in esecuzione nel computer remoto. Per altre informazioni, vedere [debug remoto](../debugger/remote-debugging.md).

Per istruzioni più complete per il debug di applicazioni ASP.NET che sono state distribuite a IIS, vedere [Remote Debug ASP.NET in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Per connettersi a un processo in esecuzione in un computer remoto:**

1. In Visual Studio, selezionare **Debug** > **Connetti a processo** (o premere **Ctrl**+**Alt** + **P**) per aprire la **Connetti a processo** nella finestra di dialogo.

2. **Tipo di connessione** deve essere **predefinito** per la maggior parte dei casi. Nel **destinazione della connessione** , selezionare il computer remoto, utilizzando uno dei metodi seguenti:

   - Selezionare la freccia giù accanto a **destinazione della connessione**e selezionare il nome del computer nell'elenco a discesa.
   - Digitare il nome del computer nel **destinazione della connessione** casella e premere **invio**.

     Verificare che Visual Studio aggiunge la porta necessaria per il nome del computer, che viene visualizzata nel formato:  **\<nome del computer remoto >: porta**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Se non è possibile connettersi usando il nome del computer remoto, provare a usare l'indirizzo IP e indirizzi di porta (ad esempio, `123.45.678.9:4022`). 4024 è la porta predefinita per il debugger remoto di Visual Studio 2019 x64. Per altre assegnazioni di porta del debugger remoto, vedere [assegnazioni di porta del debugger remoto](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Se non è possibile connettersi usando il nome del computer remoto, provare a usare l'indirizzo IP e indirizzi di porta (ad esempio, `123.45.678.9:4022`). 4022 è la porta predefinita per il debugger remoto di Visual Studio 2017 x64. Per altre assegnazioni di porta del debugger remoto, vedere [assegnazioni di porta del debugger remoto](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Selezionare il **trovare** accanto alle **destinazione della connessione** casella per aprire il **le connessioni Remote** nella finestra di dialogo. Il **le connessioni Remote** nella finestra di dialogo sono elencati tutti i dispositivi sulla subnet locale o collegato direttamente al computer in uso. Potresti dover [aprire la porta UDP 3702](../debugger/remote-debugger-port-assignments.md) sul server per individuare i dispositivi remoti. Selezionare il computer o dispositivo desiderato, quindi fare clic su **seleziona**.

   > [!NOTE]
   > Il **tipo di connessione** impostazione viene mantenuta tra sessioni di debug. Il **destinazione della connessione** impostazione viene mantenuta tra sessioni di debug solo se si è verificato ha stabilito una connessione di debug che hanno come destinazione.

3. Fare clic su **Refresh** per popolare le **processi disponibili** elenco.

    >[!TIP]
    >I processi possono avviare e arrestare in background mentre il **Connetti a processo** nella finestra di dialogo è aperta, pertanto l'elenco dei processi in esecuzione potrebbe non essere sempre corrente. È possibile selezionare **Aggiorna** in qualsiasi momento per visualizzare l'elenco corrente.

4. Nel **processi disponibili** elencare, trovare e selezionare il processo o i processi di cui si desidera stabilire una connessione.

   - Per selezionare rapidamente un processo, digitare il nome o la prima lettera di **Filtra processi** casella.

   - Se non si conosce il nome del processo, scorrere l'elenco, oppure vedere [comuni scenari di debug](#BKMK_Scenarios) per alcuni nomi di processo comuni.

   - Per trovare i processi in esecuzione in tutti gli account utente, selezionare la **Mostra i processi di tutti gli utenti** casella di controllo.

     >[!NOTE]
     >Se si tenta di connettersi a un processo appartenente a un account utente non attendibile, verrà visualizzata una finestra di dialogo contenente un avviso di sicurezza per chiedere conferma dell'operazione. Per altre informazioni vedere [avviso di sicurezza: La connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti risultano sospette o non si è certi, non stabilire la connessione al processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. Nel **Collega a** campo, assicurarsi che sia elencato il tipo di codice si prevede di eseguire il debug. Il valore predefinito **automatica** l'impostazione funziona per la maggior parte dei tipi di app.

   Per selezionare manualmente i tipi di codice:
   1. Fare clic su **Seleziona**.
   1. Nel **Seleziona tipo di codice** finestra di dialogo, selezionare **eseguire il Debug di questi tipi di codice**.
   1. Selezionare i tipi di codice da sottoporre a debug.
   1. Scegliere **OK**.

6. Selezionare **collegare**.

>[!NOTE]
>È possibile collegare più App per il debug, ma solo un'app è attiva nel debugger alla volta. È possibile impostare l'app attiva in Visual Studio **posizione di Debug** sulla barra degli strumenti oppure **processi** finestra.

In alcuni casi, quando esegue il debug in una sessione Desktop remoto (servizi Terminal), il **processi disponibili** elenco non verrà visualizzati tutti i processi disponibili. Se si esegue Visual Studio come utente che ha un account utente con limitazioni, il **processi disponibili** elenco non verrà visualizzati i processi sono in esecuzione nella sessione 0. Sessione 0 viene usata per i servizi e gli altri processi server, incluso *w3wp.exe*. È possibile risolvere il problema eseguendo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con un account amministratore o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalla console del server invece di una sessione di Servizi Terminal.

Se non è possibile adottare una di queste soluzioni alternative, una terza opzione consiste nel connettersi al processo eseguendo `vsjitdebugger.exe -p <ProcessId>` dalla riga di comando di Windows. È possibile determinare l'ID di processo con *tlist.exe*. Per ottenere *tlist.exe*, scaricare e installare gli strumenti di debug per Windows disponibili in [Download di WDK e WinDbg](/windows-hardware/drivers/download-the-wdk).

## <a name="BKMK_reattach"></a> Riassocia a un processo

È possibile riconnettere rapidamente i processi che in precedenza sono stati collegati a, scegliendo **Debug** > **riassocia a processo** (**MAIUSC** + **Alt**+**P**). Quando si sceglie questo comando, il debugger tenterà immediatamente di connettere all'ultima processi che sono stati collegati a tentando innanzitutto di associare l'ID del processo precedente e se ha esito negativo, associando il precedente il nome del processo. Se non vengono trovate corrispondenze o se alcuni processi hanno lo stesso nome, il **Connetti a processo** verrà aperta la finestra di dialogo che consente di selezionare il processo corretto.

> [!NOTE]
> Il **riassocia a processo** comando è disponibile a partire da Visual Studio 2017.

## <a name="BKMK_Scenarios"></a> Scenari di debug comuni

Per stabilire se usare **Connetti a processo** e sui processi a cui connettersi, la tabella seguente illustra alcuni scenari di debug comuni, con collegamenti a ulteriori istruzioni dove disponibile. (L'elenco non completo).

Per alcuni tipi di app, ad esempio le app di App di Windows universale (UWP), non collega direttamente a un nome di processo, ma usare il **Debug pacchetto applicazione installato** l'opzione di menu in Visual Studio invece (vedere la tabella).

Affinché il debugger possa connettersi a codice scritto in C++, è necessario che venga generato l'elemento `DebuggableAttribute`. È possibile aggiungere automaticamente questo elemento al codice mediante il collegamento all'opzione del linker [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

Per il debug di script lato client, è necessario abilitare il debug degli script nel browser. Per eseguire il debug dello script lato client in Chrome, scegliere **Web kit** come tipo di codice e a seconda del tipo di app, potrebbe essere necessario chiudere tutte le istanze di Chrome e avviare il browser in modalità di debug (tipo `chrome.exe --remote-debugging-port=9222` dalla riga di comando).

Per selezionare rapidamente un processo in esecuzione a cui connettersi, in Visual Studio, digitare **Ctrl**+**Alt**+**P**, quindi digitare la prima lettera del nome del processo.

|Scenario|Eseguire il debug (metodo)|Nome processo|Note e collegamenti|
|-|-|-|-|
|Il debug remoto di ASP.NET 4 o 4.5 in un server IIS|Utilizzare gli strumenti remoti e **Connetti a processo**|*w3wp.exe*|Vedere [Remote Debug ASP.NET in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Debug remoto di ASP.NET Core in un server IIS|Utilizzare gli strumenti remoti e **Connetti a processo**|*dotnet.exe*|Per la distribuzione di app, vedere [pubblicazione su IIS](https://docs.asp.net/en/latest/publishing/iis.html). Per eseguire il debug, vedere [Remote Debug ASP.NET Core in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Eseguire il debug di script sul lato client in un server IIS locale, per tipi di app supportati |Usare **Connetti a processo**|*Chrome.exe*, *MicrosoftEdgeCP.exe*, o *iexplore.exe*|Debug degli script deve essere abilitato. Per Chrome, è necessario eseguire anche Chrome in modalità di debug e selezionare **Webkit code** nel **collegare a** campo.|
|Debug di un'app c#, Visual Basic o C++ nel computer locale|Usare il debug standard (**F5**) o **Connetti a processo**|*\<appname>.exe*|Nella maggior parte degli scenari, usare il debug standard e non **Connetti a processo**.|
|Debug remoto di un'app desktop di Windows|Remote tools|N/D| Visualizzare [Remote debug di un'app c# o Visual Basic](../debugger/remote-debugging-csharp.md) o [un'app C++ di eseguire il debug remoto](../debugger/remote-debugging-cpp.md)|
|Eseguire il debug di un'app ASP.NET nel computer locale dopo avere avviato l'app senza il debugger|Usare **Connetti a processo**|*iiexpress.exe*|Questo potrebbe essere utile per rendere l'app di caricare più veloce, ad esempio, ad esempio, la profilatura. |
|Eseguire il debug di altri tipi di app supportati in un processo del server|Se il server è remoto, utilizzare gli strumenti remoti, e **Connetti a processo**|*Chrome.exe*, *iexplore.exe*, o di altri processi|Se necessario, è possibile utilizzare Monitoraggio risorse per semplificare l'identificazione del processo. Vedere [Debug remoto](../debugger/remote-debugging.md).|
|Un'app di App di Windows universale (UWP), OneCore, HoloLens o IoT eseguire il debug remoto|Debug pacchetto dell'app installato|N/D|Visualizzare [eseguire il Debug di un pacchetto dell'app installate](debug-installed-app-package.md) invece di usare **Connetti a processo**|
|Eseguire il debug di un'app per App di Windows universale (UWP), OneCore, HoloLens e IoT che non è stato avviato da Visual Studio|Debug pacchetto dell'app installato|N/D|Visualizzare [eseguire il Debug di un pacchetto dell'app installate](debug-installed-app-package.md) invece di usare **Connetti a processo**|

## <a name="use-debugger-features"></a>Usare le funzionalità del debugger

Per utilizzare le funzionalità complete del debugger di Visual Studio (ad esempio, raggiungere punti di interruzione) quando si collega a un processo, l'app deve corrispondere esattamente all'origine locale e simboli. Vale a dire, il debugger deve essere in grado di caricare i valori corretti [simboli (con estensione pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Per impostazione predefinita, questo richiede una build di debug.

Per scenari di debug remoti, è necessario disporre del codice sorgente (o una copia del codice sorgente) già aperto in Visual Studio. I file binari dell'app compilate nel computer remoto devono provenire dalla stessa build perché nel computer locale.

In alcuni scenari di debug locale, è possibile eseguire il debug in Visual Studio senza accesso all'origine se i file di simboli corretto sono presenti con l'app. Per impostazione predefinita, questo richiede una build di debug. Per altre informazioni, vedere [specificare i file di simboli e origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

##  <a name="BKMK_Troubleshoot_attach_errors"></a> Risolvere gli errori di connessione
 I processi in esecuzione a cui il debugger tenta di connettersi possono contenere uno o più tipi di codice. I tipi di codice a cui il debugger può connettersi vengono visualizzati e selezionati nella finestra di dialogo **Seleziona tipo di codice** .

 In alcuni casi il debugger riesce a connettersi a un tipo di codice ma non a un altro. Questa situazione può verificarsi quando si tenta di stabilire una connessione a un processo in esecuzione in un computer remoto, nel quale potrebbero essere stati installati i componenti per il debug remoto solo per alcuni tipi di codice. Può inoltre verificarsi quando si tenta di stabilire una connessione a due o più processi per il debug diretto di un database. Durante il debug SQL è supportata esclusivamente la connessione a un singolo processo.

 Se il debugger è in grado di connettersi solo ad alcuni, ma non tutti i tipi di codice, viene visualizzato un messaggio che identifica i tipi non è stato possibile collegare.

 Se il debugger riesce a connettersi ad almeno un tipo di codice, è possibile procedere con il debug del processo. Sarà possibile eseguire il debug solo dei tipi di codice con i quali è stata stabilita una connessione. Il codice scollegato nel processo verrà comunque eseguito, ma non sarà possibile impostare punti di interruzione, visualizzare i dati o eseguire altre operazioni di debug su tale codice.

 Se si desiderano informazioni più specifiche sul motivo per cui il debugger non è stato possibile collegare a un tipo di codice, provare a ricollegare solo tale tipo di codice.

 **Per ottenere informazioni specifiche sulla causa dell'errore di connessione a un tipo di codice:**

1.  Disconnettersi dal processo. Nel **Debug** dal menu **Disconnetti tutto**.

1.  Riassocia a processo, selezionando solo il tipo di codice che non è stato possibile collegare.

    1.  Nella finestra di dialogo **Connetti a processo** selezionare il processo nell'elenco **Processi disponibili**.

    2.  Selezionare **seleziona**.

    3.  Nella finestra di dialogo **Seleziona tipo di codice** selezionare il pulsante di opzione **Esegui il debug di questi tipi di codice** e il tipo di codice per cui si è verificato il problema di connessione. Deselezionare gli altri tipi di codice.

    4.  Scegliere **OK**.

    5.  Nel **Connetti a processo** finestra di dialogo **Attach**.

    La connessione non verrà eseguita e verrà visualizzato un messaggio di errore specifico.

## <a name="see-also"></a>Vedere anche

- [Eseguire il debug di più processi](../debugger/debug-multiple-processes.md)
- [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Debug remoto](../debugger/remote-debugging.md)