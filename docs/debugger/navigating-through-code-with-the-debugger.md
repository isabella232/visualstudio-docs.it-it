---
title: Esplorare il codice con il debugger | Microsoft Docs
description: "Informazioni su come usare il debugger Visual Studio per risolvere i problemi del codice. Gli argomenti includono: passare alla modalità di interruzione, eseguire il codice un'istruzione alla riga di codice ed eseguire fino a una destinazione."
ms.custom: SEO-VS-2020
ms.date: 09/23/2021
ms.topic: how-to
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ab1298a0c6721d4044187e2582c2dbdd5e14326f
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427278"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Spostarsi nel codice con il debugger Visual Studio

Il debugger Visual Studio consente di spostarsi nel codice per esaminare lo stato di un'app e visualizzarne il flusso di esecuzione. È possibile usare i tasti di scelta rapida, i comandi di debug, i punti di interruzione e altre funzionalità per ottenere rapidamente il codice da esaminare. La familiarità con i comandi di navigazione del debugger e i tasti di scelta rapida rende più semplice e veloce trovare e risolvere i problemi delle app.

> [!NOTE]
> Se è la prima volta che si prova a eseguire [](../debugger/debugging-absolute-beginners.md) il debug del codice, è possibile leggere Debug per principianti assoluti e Tecniche e strumenti di debug prima di procedere con questo articolo. [](../debugger/write-better-code-with-visual-studio.md)

## <a name="get-into-break-mode"></a>Entra in "modalità di interruzione"

In *modalità di interruzione* l'esecuzione dell'app viene sospesa mentre funzioni, variabili e oggetti rimangono in memoria. Quando il debugger è in modalità di interruzione, è possibile spostarsi nel codice. I modi più comuni per passare rapidamente alla modalità di interruzione sono:

- Per iniziare l'esecuzione del codice, premere **F10** o **F11.** In questo modo è possibile trovare rapidamente il punto di ingresso dell'app, quindi continuare a premere i comandi del passaggio per spostarsi nel codice.

- [Eseguire fino a una posizione o una funzione](#run-to-a-specific-location-or-function)specifica, ad esempio impostando un punto di [interruzione](using-breakpoints.md) e avviando l'app.

   Ad esempio, dall'editor di codice in Visual Studio è possibile usare il comando Esegui fino al **cursore** per avviare l'app, il debugger collegato e passare alla modalità di interruzione, quindi **premere F11** per spostarsi nel codice.

   ![Eseguire fino al cursore ed eseguire un'istruzione nel codice](../debugger/media/navigate-code-code-stepping.gif "Eseguire fino al cursore ed eseguire un'istruzione al codice")

In modalità di interruzione è possibile usare un'ampia gamma di comandi per spostarsi all'interno del codice. In modalità di interruzione è possibile esaminare i valori delle variabili per cercare violazioni o bug. Per alcuni tipi di progetto, è anche possibile apportare modifiche all'app in modalità di interruzione.

La maggior parte delle finestre del debugger, ad **esempio** **le** finestre Moduli ed Espressioni di controllo, è disponibile solo quando il debugger è collegato all'app. Alcune funzionalità del debugger, ad  esempio la visualizzazione dei valori  delle variabili nella finestra Variabili locali o la valutazione di espressioni nella finestra Espressioni di controllo, sono disponibili solo mentre il debugger è in pausa, ovvero in modalità di interruzione.

> [!NOTE]
> Se si interrompe il codice in cui non sono caricati file di  origine o di simboli (con estensione *pdb),* il debugger visualizza una pagina File di origine non trovati o Simboli non **trovati** che consente di trovare e caricare i file. Vedere [Specificare i file di simboli (con estensione pdb) e di origine.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Se non è possibile caricare i file di simboli o di origine, è comunque possibile eseguire il debug delle istruzioni dell'assembly nella **finestra Disassembly.**

## <a name="step-through-code"></a>Esecuzione del codice un'istruzione alla volta

I comandi del passaggio del debugger consentono di esaminare lo stato dell'app o di scoprire di più sul flusso di esecuzione.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> Eseguire un'istruzione alla riga di codice riga per riga

Per arrestare ogni istruzione durante il debug, usare **Esegui debug**  >  **istruzione oppure** premere **F11.**

Il debugger esegue istruzioni di codice, non righe fisiche. Ad esempio, una clausola `if` può essere scritta in una riga:

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

Tuttavia, quando si esegue un'istruzione in questa riga, il debugger considera la condizione come un passaggio e la conseguenza come un altro. Nell'esempio precedente la condizione è true.

In una chiamata di funzione annidata, scegliendo **Esegui istruzione** verrà eseguita la funzione annidata più interna. Ad esempio, se si usa **Istruzione in** in una chiamata come , il debugger `Func1(Func2())` esegue l'istruzione nella funzione `Func2` .

>[!TIP]
>Quando si esegue ogni riga di codice, è possibile passare [](autos-and-locals-windows.md) il mouse [](watch-and-quickwatch-windows.md) sulle variabili per visualizzarne i valori oppure usare le finestre Variabili locali ed Espressioni di controllo per controllare la modifica dei valori. È anche possibile tracciare visivamente lo [stack di chiamate durante](how-to-use-the-call-stack-window.md) l'esecuzione di istruzioni nelle funzioni. (Solo per Visual Studio Enterprise, vedere [Eseguire il mapping dei metodi nello stack di chiamate durante il debug).](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a> Eseguire il codice un'istruzione alla pagina e ignorare alcune funzioni

È possibile che una funzione non sia di grande attenzione durante il debug o che si sappia che funziona, ad esempio un codice di libreria ben testato. È possibile usare i comandi seguenti per ignorare il codice durante l'esecuzione di istruzioni del codice. Le funzioni vengono comunque eseguite, ma il debugger le ignora.

|Comando da tastiera|Comando del menu Debug|Descrizione|
|----------------------|------------------|-----------------|
|**F10**|**Esegui istruzione/routine**|Se la riga corrente contiene una chiamata di funzione, **Step Over** esegue il codice, quindi sospende l'esecuzione in corrispondenza della prima riga di codice dopo la fine della funzione chiamata.|
|**MAIUSC** + **F11**|**Esci da istruzione/routine**|**L'istruzione/uscita** continua l'esecuzione del codice e sospende l'esecuzione quando la funzione corrente viene restituita. Il debugger ignora la funzione corrente.|

## <a name="run-to-a-specific-location-or-function"></a>Eseguire fino a una posizione o a una funzione specifica

È preferibile eseguire direttamente in una posizione o una funzione specifica quando si conosce esattamente il codice da esaminare o si sa da dove avviare il debug.

### <a name="run-to-a-breakpoint-in-code"></a>Eseguire fino a un punto di interruzione nel codice

Per impostare un punto di interruzione semplice nel codice, fare clic sul margine all'estrema sinistra accanto alla riga di codice in cui si vuole sospendere l'esecuzione. È anche possibile selezionare la riga e premere **F9,** selezionare Debug Attiva/Disattiva punto di interruzione oppure fare clic con il pulsante destro del mouse e scegliere Punto di  >   **interruzione** Inserisci punto  >  **di interruzione**. Il punto di interruzione viene visualizzato come punto rosso nel margine sinistro accanto alla riga di codice. Il debugger sospende l'esecuzione subito prima dell'esecuzione della riga.

![Impostare un punto di interruzione](../debugger/media/dbg_basics_setbreakpoint.png "Imposta punto di interruzione")

I punti di interruzione in Visual Studio forniscono un'ampia gamma di funzionalità aggiuntive, ad esempio punti di interruzione e punti di analisi condizionali. Per informazioni dettagliate, vedere [Uso dei punti di interruzione.](../debugger/using-breakpoints.md)

### <a name="run-to-a-function-breakpoint"></a>Eseguire fino a un punto di interruzione della funzione

È possibile indicare al debugger di eseguire finché non raggiunge una funzione specificata. È possibile specificare la funzione inserendo il nome oppure sceglierla dallo stack di chiamate.

**Per specificare un punto di interruzione della funzione in base al nome**

1. Selezionare Debug nuovo **punto**  >  **di**  >  **interruzione punto di interruzione**

1. Nella finestra **di dialogo Nuovo punto di** interruzione funzione digitare il nome della funzione e selezionarne il linguaggio.

   ![Finestra di dialogo Nuovo punto di interruzione funzione](../debugger/media/dbg_execution_newbreakpoint.png "Nuovo punto di interruzione della funzione")

1. Selezionare **OK**.

Se la funzione è in overload o in più di uno spazio dei nomi, è possibile scegliere quello desiderato nella finestra Punti **di** interruzione.

![Punti di interruzione delle funzioni in overload](../debugger/media/dbg_execution_overloadedbreakpoints.png "Punti di interruzione di funzione in overload")

**Per selezionare un punto di interruzione della funzione dallo stack di chiamate**

1. Durante il debug, aprire la **finestra Stack di** chiamate selezionando **Debug**  >  **Windows** Stack  >  **di chiamate**.

1. Nella finestra **Stack di chiamate fare** clic con il pulsante destro del mouse su una funzione e scegliere Esegui fino al **cursore** oppure **premere CTRL** + **F10.**

Per tracciare visivamente lo stack di chiamate, vedere [Eseguire il mapping dei metodi nello stack di chiamate durante il debug.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="run-to-a-cursor-location"></a>Eseguire fino alla posizione del cursore

Per eseguire fino alla posizione del cursore, nel codice sorgente o nella finestra **Stack** di chiamate selezionare la riga in corrispondenza della quale si vuole interrompere l'esecuzione, fare clic con il pulsante destro del mouse e scegliere Esegui fino al **cursore** oppure premere **CTRL** + **F10.** La selezione **di Esegui fino al cursore** è simile all'impostazione di un punto di interruzione temporaneo.

### <a name="run-to-click"></a>Esegui fino alla riga selezionata

Mentre è in pausa nel debugger, è possibile passare il puntatore del  mouse su un'istruzione nel codice sorgente o nella finestra **Disassembly** e selezionare l'icona a forma di freccia verde Esegui l'esecuzione fino a qui. **L'uso di Esegui su clic** elimina la necessità di impostare un punto di interruzione temporaneo.

![Esegui fino alla riga selezionata](../debugger/media/dbg-run-to-click.png "Esegui fino alla riga selezionata")

> [!NOTE]
> **Run to Click** è disponibile a partire da [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

### <a name="manually-break-into-code"></a>Inserire un'interruzione nel codice manualmente

Per interrompere la successiva riga di codice disponibile in un'app in esecuzione, selezionare **Debug**  >  **Interrompi tutto** oppure premere **CTRL** +  + **ALT+INTERR.**

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> Spostare il puntatore per modificare il flusso di esecuzione

Mentre il debugger è in pausa, una freccia gialla sul margine del codice sorgente o della finestra **Disassembly** contrassegna la posizione dell'istruzione successiva da eseguire. È possibile modificare l'istruzione successiva da eseguire spostando questa freccia. È possibile ignorare una parte di codice o tornare a una riga precedente. Lo spostamento del puntatore è utile in situazioni come l'omissione di una sezione di codice che contiene un bug noto.

 ![Spostare il puntatore](../debugger/media/dbg_basics_example3.gif "Spostare il puntatore")

Per modificare l'istruzione successiva da eseguire, il debugger deve essere in modalità di interruzione. Nella finestra Del codice sorgente o **Disassembly** trascinare la freccia gialla su una riga diversa oppure fare clic con il pulsante destro del mouse sulla riga da eseguire successivamente e scegliere **Imposta istruzione successiva**.

Il contatore del programma passa direttamente alla nuova posizione e le istruzioni tra i punti di esecuzione precedente e nuovo non vengono eseguite. Tuttavia, se si sposta il punto di esecuzione indietro, le istruzioni non vengono annullate.

>[!CAUTION]
>- Lo spostamento dell'istruzione successiva in corrispondenza di un'altra funzione o ambito provoca in genere un errore dello stack di chiamate e, conseguentemente, un errore o un'eccezione di runtime. Se si sposta l'istruzione successiva in corrispondenza di un altro ambito, verrà visualizzata una finestra di dialogo contenente un avviso e in cui si può scegliere di annullare l'operazione.
>- In Visual Basic non è possibile spostare l'istruzione successiva in corrispondenza di un altro ambito o di un'altra funzione.
>- Se in C++ nativo sono abilitati i controlli runtime, l'impostazione dell'istruzione successiva può causare la generazione di un'eccezione quando l'esecuzione raggiunge la fine del metodo.
>- Quando l'opzione Modifica e continuazione è abilitata, **Imposta istruzione successiva** avrà esito negativo se sono state effettuate modifiche per cui Modifica e continuazione non è immediatamente in grado di eseguire nuovamente il mapping. Ad esempio questo può accadere se è stato modificato del codice all'interno di un blocco catch. In questo caso, un messaggio di errore indica che l'operazione non è supportata.
>- Nel codice gestito non è possibile spostare l'istruzione successiva se:
>   - L'istruzione successiva è inclusa in un metodo diverso da quello dell'istruzione corrente.
>   - Il debug è stato avviato dal debug JIT.
>   - Rimozione dello stack di chiamate in corso.
>   - È stata generata un'eccezione System.StackOverflowException or System.Threading.ThreadAbortException.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Eseguire il debug di codice non utente

Per impostazione predefinita, il debugger tenta di eseguire il debug solo del codice dell'app abilitando un'impostazione denominata *Just My Code*. Per altre informazioni sul funzionamento di questa funzionalità per linguaggi e tipi di progetto diversi e su come personalizzarla, [vedere](../debugger/just-my-code.md)Just My Code .

Per esaminare il codice del framework, il codice della libreria di terze parti o le chiamate di sistema durante il debug, è possibile disabilitare Just My Code. In **Strumenti** (o **Debug**) > **Opzioni**  >  **di** debug deselezionare la casella di controllo **Just My Code** controllo. Quando Just My Code è disabilitato, il codice non utente viene visualizzato nelle finestre del debugger e il debugger può eseguire un'istruzione nel codice non utente.

> [!NOTE]
> Just My Code non è supportato per progetti per dispositivi.

### <a name="debug-system-code"></a>Eseguire il debug del codice di sistema

Se sono stati caricati simboli di debug per il codice di sistema Microsoft e Just My Code disabilitato, è possibile eseguire una chiamata di sistema come qualsiasi altra chiamata.

Per caricare i simboli Microsoft, vedere [Configurare i percorsi dei simboli e le opzioni di caricamento.](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options)

**Per caricare i simboli per un componente di sistema specifico:**

1. Durante il debug, aprire la finestra  **Moduli** selezionando Debug Windows moduli oppure premendo  >    >    + **CTRL** + **ALT+U.**

1. Nella finestra **Moduli** è possibile indicare quali moduli hanno simboli caricati nella **colonna Stato** simbolo. Fare clic con il pulsante destro del mouse sul modulo per cui si vogliono caricare i simboli e **scegliere Carica simboli**.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Eseguire istruzioni di proprietà e operatori nel codice gestito
 Il debugger esegue le istruzioni/routine di proprietà e operatori nel codice gestito per impostazione predefinita. Nella maggior parte dei casi, l'esperienza di debug risulta notevolmente migliorata. Per abilitare l'esecuzione di istruzioni nelle proprietà o negli operatori, scegliere **Opzioni di**  >  **debug**. Nella pagina **Debug**  >  **generale** deselezionare la **casella di controllo Step over properties and operators (Solo gestito).**

## <a name="see-also"></a>Vedi anche
- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Tecniche e strumenti di debug CRT](../debugger/write-better-code-with-visual-studio.md)
- [Prima di tutto esaminare il debug](../debugger/debugger-feature-tour.md)
