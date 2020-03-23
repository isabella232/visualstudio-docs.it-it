---
title: Navigazione del codice con il debugger . Documenti Microsoft
ms.custom: seodec18
ms.date: 11/12/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dfffdf0c12ea2a8f14769f26bb40a3943579248
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302119"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Spostarsi nel codice con il debugger di Visual StudioNavigate through code with the Visual Studio debugger

Il debugger di Visual Studio consente di spostarsi all'interno del codice per esaminare lo stato di un'app e mostrarne il flusso di esecuzione. È possibile utilizzare i tasti di scelta rapida, i comandi di debug, i punti di interruzione e altre funzionalità per accedere rapidamente al codice che si desidera esaminare. La familiarità con i comandi e i tasti di scelta rapida per lo spostamento nel debugger rende più semplice e veloce trovare e risolvere i problemi dell'app.  Se questa è la prima volta che si tenta di eseguire il debug del codice, si consiglia di leggere [Debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) e [tecniche e strumenti di debug](../debugger/write-better-code-with-visual-studio.md) prima di passare attraverso questo articolo.

## <a name="get-into-break-mode"></a>Entra in "modalità di interruzione"

In *modalità di interruzione,* l'esecuzione dell'app viene sospesa mentre funzioni, variabili e oggetti rimangono in memoria. Una volta che il debugger è in modalità di interruzione, è possibile spostarsi all'interno del codice. Il modo più comune per entrare rapidamente in modalità di interruzione è:

- Iniziare l'esecuzione del codice premendo **F10** o **F11**. In questo modo è possibile trovare rapidamente il punto di ingresso dell'app, quindi è possibile continuare a premere i comandi del passaggio per spostarsi nel codice.

- [Esegui in un percorso o funzione specifica,](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)ad esempio [impostando un punto di interruzione](using-breakpoints.md) e avviando l'app.

   Ad esempio, dall'editor di codice in Visual Studio, è possibile utilizzare il comando **Esegui fino al cursore** per avviare l'app, il debugger collegato e passare alla modalità di interruzione, quindi **F11** per esplorare il codice.

   ![Eseguire il cursore ed eseguire il codice nel passaggio a un'istruzione](../debugger/media/navigate-code-code-stepping.gif "Eseguire il cursore ed eseguire il codice nel passaggio a un'istruzione")

Una volta in modalità di interruzione, è possibile utilizzare una varietà di comandi per spostarsi all'interno del codice. In modalità di interruzione, è possibile esaminare i valori delle variabili per cercare violazioni o bug. Per alcuni tipi di progetto, puoi anche apportare modifiche all'app in modalità di interruzione.

La maggior parte delle finestre del debugger, ad esempio le finestre **Moduli** e **Espressioni di controllo,** sono disponibili solo quando il debugger è collegato all'app. Alcune funzionalità del debugger, ad esempio la visualizzazione di valori di variabile nella finestra **Variabili locali** o la valutazione di espressioni nella finestra Espressioni di **controllo,** sono disponibili solo quando il debugger è in pausa, ovvero in modalità di interruzione.

> [!NOTE]
> Se si suddivide nel codice per il quale non sono stati caricati file di origine o di simboli (*pdb),* il debugger visualizza una pagina File di **origine non trovati** o **Simboli non trovati** che consente di trovare e caricare i file. Consultate [Specificare i file di simboli (con estensione pdb) e i file](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)di origine. Se non è possibile caricare i file di simboli o di origine, è comunque possibile eseguire il debug delle istruzioni dell'assembly nella finestra **Disassembly.**

## <a name="step-through-code"></a>Esecuzione del codice un'istruzione alla volta

I comandi del passaggio del debugger consentono di controllare lo stato dell'app o di altre informazioni sul flusso di esecuzione.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a>Passare nel codice riga per riga

Per interrompere ogni istruzione durante il debug, utilizzare Esegui istruzione **di debug** > **Step Into**in oppure premere **F11**.

Il debugger scorre istruzioni di codice, non righe fisiche. Ad esempio, una clausola `if` può essere scritta in una riga:

  ```csharp
  int x = 42;
  string s = "Not answered";
  if( int x == 42) s = "Answered!";
  ```

  ```vb
  Dim x As Integer = 42
  Dim s As String = "Not answered"
  If x = 42 Then s = "Answered!"
  ```

Tuttavia, quando si esegue un'istruzione in questa riga, il debugger considera la condizione come un passaggio e la conseguenza come un'altra. Nell'esempio precedente, la condizione è vera.

In una chiamata di funzione annidata, scegliendo **Esegui istruzione** verrà eseguita la funzione annidata più interna. Ad esempio, se si utilizza **Esegui istruzione** in una chiamata come `Func1(Func2())`, il debugger esegue le istruzioni nella funzione `Func2`.

>[!TIP]
>Quando si esegue ogni riga di codice, è possibile passare il mouse sulle variabili per visualizzarne i valori oppure utilizzare le finestre [Variabili locali](autos-and-locals-windows.md) e [Espressioni di](watch-and-quickwatch-windows.md) controllo per osservare i valori che cambiano. È anche possibile tracciare visivamente [lo stack](how-to-use-the-call-stack-window.md) di chiamate durante l'esecuzione di un'istruzione nelle funzioni. (Solo per Visual Studio Enterprise, consultate Eseguire il mapping di metodi nello stack di [chiamate durante il debug).](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a>Eseguire il codice un'istruzione alla volta e ignorare alcune funzioni

È possibile che non si preoccupi di una funzione durante il debug o si sa che funziona, ad esempio codice di libreria ben testato. È possibile utilizzare i comandi seguenti per ignorare il codice durante l'esecuzione di istruzioni del codice. Le funzioni vengono comunque eseguite, ma il debugger le ignora.

|Comando da tastiera|Comando del menu Debug|Descrizione|
|----------------------|------------------|-----------------|
|**F10**|**Esegui istruzione/routine**|Se la riga corrente contiene una chiamata di funzione, **Step Over** esegue il codice, quindi sospende l'esecuzione nella prima riga di codice dopo la restituzione della funzione chiamata.|
|**Maiusc**+**F11**|**Esci**|**Esci** da estrale continua l'esecuzione del codice e sospende l'esecuzione quando la funzione corrente restituisce. Il debugger ignora la funzione corrente.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Eseguire fino a una posizione o una funzione specifica

È preferibile eseguire direttamente in una posizione o funzione specifica quando si conosce esattamente il codice che si desidera controllare o si sa dove si desidera avviare il debug.

### <a name="run-to-a-breakpoint-in-code"></a>Eseguire fino a un punto di interruzione nel codiceRun to a breakpoint in code

Per impostare un semplice punto di interruzione nel codice, fare clic sul margine all'estrema sinistra accanto alla riga di codice in cui si desidera sospendere l'esecuzione. È inoltre possibile selezionare la riga e premere **F9**, selezionare **Debug** > **Toggle Breakpoint**oppure fare clic con il pulsante destro del mouse e scegliere Inserisci punto di **interruzione** > **Insert Breakpoint**. Il punto di interruzione viene visualizzato come un punto rosso nel margine sinistro accanto alla riga di codice. Il debugger sospende l'esecuzione appena prima dell'esecuzione della riga.

![Impostare un punto di interruzioneSet a breakpoint](../debugger/media/dbg_basics_setbreakpoint.png "Imposta punto di interruzione")

I punti di interruzione in Visual Studio forniscono un'ampia gamma di funzionalità aggiuntive, ad esempio punti di interruzione e punti di analisi condizionali. Per informazioni [dettagliate,](../debugger/using-breakpoints.md)consultate Utilizzo dei punti di interruzione.

### <a name="run-to-a-function-breakpoint"></a>Eseguire fino a un punto di interruzione di funzioneRun to a function breakpoint

È possibile indicare al debugger di eseguire fino a quando non raggiunge una funzione specificata. È possibile specificare la funzione inserendo il nome oppure sceglierla dallo stack di chiamate.

**Per specificare un punto di interruzione di funzione in base al nomeTo specify a function breakpoint by name**

1. Selezionare **Debug nuovo** > punto di interruzione della funzione del punto**di interruzioneSelect** > Debug New Breakpoint**Function Breakpoint**

1. Nella finestra di **dialogo Nuovo punto** di interruzione della funzione digitare il nome della funzione e selezionarne la lingua.

   ![Finestra di dialogo Nuova punto di interruzione funzione](../debugger/media/dbg_execution_newbreakpoint.png "Nuovo punto di interruzione della funzioneNew Function Breakpoint")

1. Selezionare **OK**.

Se la funzione è in overload o in più di uno spazio dei nomi, è possibile scegliere quello desiderato nel **punti di interruzione** finestra.

![Punti di interruzione delle funzioni di overloadOverloaded function breakpoints](../debugger/media/dbg_execution_overloadedbreakpoints.png "Punti di interruzione delle funzioni di overloadOverloaded function breakpoints")

**Per selezionare un punto di interruzione di funzione dallo stack di chiamateTo select a function breakpoint from the call stack**

1. Durante il debug, aprire la finestra **Stack di chiamate** selezionando Esegui **debug** > **stack di chiamate**di**Windows** > .

1. Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse su una funzione e scegliere Esegui fino al **cursore**oppure premere **CTRL**+**F10**.

Per tracciare visivamente lo stack di chiamate, vedere [Metodi di mapping nello stack](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)di chiamate durante il debug .

### <a name="run-to-a-cursor-location"></a>Eseguire fino alla posizione di un cursore

Per eseguire l'esecuzione fino alla posizione del cursore, nel codice sorgente o nella finestra **Stack** di chiamate selezionare la riga in cui si desidera interrompere, fare clic con il pulsante destro del mouse e scegliere **Esegui fino al cursore**oppure premere **CTRL**+**F10**. Selezionare **Esegui fino al cursore** è come impostare un punto di interruzione temporaneo.

### <a name="run-to-click"></a>Esegui fino alla riga selezionata

Mentre è in pausa nel debugger, è possibile passare il mouse su un'istruzione nel codice sorgente o nella finestra **Disassembly** e selezionare l'icona della freccia verde Esegui esecuzione a **qui.** L'opzione **Esegui con fare clic** elimina la necessità di impostare un punto di interruzione temporaneo.

![Esegui fino alla riga selezionata](../debugger/media/dbg-run-to-click.png "Esegui fino alla riga selezionata")

> [!NOTE]
> **Run to Click** è [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]disponibile a partire da .

### <a name="manually-break-into-code"></a>Inserire un'interruzione nel codice manualmente

Per interrompere la successiva riga di codice disponibile in un'app in esecuzione, selezionare Debug**Break All (Interruzione**di **debug** > tutti) o Ctrl Alt Break **(Ctrl**+**Alt**+**Break**).

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a>Spostare il puntatore per modificare il flusso di esecuzione

Mentre il debugger è in pausa, una freccia gialla nel margine del codice sorgente o della finestra **Disassembly** contrassegna la posizione dell'istruzione successiva da eseguire. È possibile modificare l'istruzione successiva da eseguire spostando questa freccia. È possibile ignorare una parte di codice o tornare a una riga precedente. Lo spostamento del puntatore è utile per situazioni quali l'ignorare una sezione di codice che contiene un bug noto.

 ![Spostare il puntatore](../debugger/media/dbg_basics_example3.gif "Spostare il puntatore")

Per modificare l'istruzione successiva da eseguire, il debugger deve essere in modalità di interruzione. Nella finestra del codice sorgente o **Disassembly** trascinare la punta della freccia gialla su una riga diversa oppure fare clic con il pulsante destro del mouse sulla linea che si desidera eseguire successivamente e selezionare **Imposta istruzione successiva**.

Il contatore del programma passa direttamente alla nuova posizione e le istruzioni tra i punti di esecuzione vecchi e nuovi non vengono eseguite. Tuttavia, se si sposta il punto di esecuzione all'indietro, le istruzioni intermedie non vengono annullate.

>[!CAUTION]
>- Lo spostamento dell'istruzione successiva in corrispondenza di un'altra funzione o ambito provoca in genere un errore dello stack di chiamate e, conseguentemente, un errore o un'eccezione di runtime. Se si sposta l'istruzione successiva in corrispondenza di un altro ambito, verrà visualizzata una finestra di dialogo contenente un avviso e in cui si può scegliere di annullare l'operazione.
>- In Visual Basic non è possibile spostare l'istruzione successiva in corrispondenza di un altro ambito o di un'altra funzione.
>- Se in C++ nativo sono abilitati i controlli runtime, l'impostazione dell'istruzione successiva può causare la generazione di un'eccezione quando l'esecuzione raggiunge la fine del metodo.
>- Quando l'opzione Modifica e continuazione è abilitata, **Imposta istruzione successiva** avrà esito negativo se sono state effettuate modifiche per cui Modifica e continuazione non è immediatamente in grado di eseguire nuovamente il mapping. Ad esempio questo può accadere se è stato modificato del codice all'interno di un blocco catch. In questo caso, un messaggio di errore indica che l'operazione non è supportata.
>- Nel codice gestito, non è possibile spostare l'istruzione successiva se:In managed code, you cannot move the next statement if:
>   - L'istruzione successiva è inclusa in un metodo diverso da quello dell'istruzione corrente.
>   - Il debug è stato avviato dal debug JIT.
>   - È in corso una rimozione dello stack di chiamate.
>   - È stata generata un'eccezione System.StackOverflowException or System.Threading.ThreadAbortException.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Eseguire il debug di codice non utenteDebug non-user code

Per impostazione predefinita, il debugger tenta di eseguire il debug solo del codice dell'app abilitando un'impostazione denominata *Just My Code*. Per ulteriori informazioni sul funzionamento di questa funzionalità per diversi tipi di progetto e linguaggi e su come è possibile personalizzarla, vedere [Just My Code](../debugger/just-my-code.md).

Per esaminare il codice del framework, il codice di libreria di terze parti o le chiamate di sistema durante il debug, è possibile disattivare Just My Code.To look at framework code, third-party library code, or system calls while debugging, you can disable Just My Code. In **Strumenti** (o **Debug**) > **Opzioni** > **di debug**deselezionare la casella di controllo Abilita Just My **Code** . Quando Just My Code è disabilitato, il codice non utente viene visualizzato nelle finestre del debugger e il debugger può eseguire il codice non utente.

> [!NOTE]
> Just My Code non è supportato per progetti per dispositivi.

### <a name="debug-system-code"></a>Eseguire il debug del codice di sistemaDebug system code

Se sono stati caricati i simboli di debug per il codice di sistema Microsoft e sono stati disabilitati Just My Code, è possibile eseguire una chiamata di sistema come qualsiasi altra chiamata.

Per caricare i simboli Microsoft, vedere [Configurare le posizioni dei simboli e le opzioni di caricamento](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Per caricare i simboli per un componente di sistema specifico:**

1. Durante il debug, aprire la finestra **Moduli** selezionando **Debug** > **moduli****di Windows** > o premendo **CTRL**+**Alt**+**U**.

1. Nella finestra **Moduli,** è possibile stabilire quali moduli hanno simboli caricati nella colonna **Stato simbolo.** Fare clic con il pulsante destro del mouse sul modulo per il quale si desidera caricare i simboli e scegliere **Carica simboli**.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Eseguire istruzioni di proprietà e operatori nel codice gestito
 Il debugger esegue le istruzioni/routine di proprietà e operatori nel codice gestito per impostazione predefinita. Nella maggior parte dei casi, l'esperienza di debug risulta notevolmente migliorata. Per abilitare l'esecuzione di istruzioni in proprietà o operatori, scegliere**Opzioni** **di debug** > . Nella pagina**Generale** **di debug** > deselezionare la casella di controllo **Esegui istruzione/over delle proprietà e degli operatori (solo gestiti).**

## <a name="see-also"></a>Vedere anche
- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Tecniche e strumenti di debug CRT](../debugger/write-better-code-with-visual-studio.md)
- [Primo sguardo al debug](../debugger/debugger-feature-tour.md)
