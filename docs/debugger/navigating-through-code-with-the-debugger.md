---
title: Esplorare il codice con il debugger | Microsoft Docs
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
ms.openlocfilehash: e07e2612e01453115cf4cd6120d92bfd5b0168bd
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "70222649"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Esplorare il codice con il debugger di Visual Studio

Il debugger di Visual Studio consente di spostarsi nel codice per esaminare lo stato di un'app e visualizzarne il flusso di esecuzione. È possibile utilizzare i tasti di scelta rapida, i comandi di debug, i punti di interruzione e altre funzionalità per ottenere rapidamente il codice che si desidera esaminare. Una certa familiarità con i comandi e i collegamenti di navigazione del debugger rende più semplice e rapida la ricerca e la risoluzione dei problemi delle app.  Se è la prima volta che si tenta di eseguire il debug del codice, è consigliabile leggere il [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) e [tecniche e strumenti di debug](../debugger/write-better-code-with-visual-studio.md) prima di procedere con questo articolo.

## <a name="basic-debugging"></a>Debug di base

Per avviare l'app con il debugger collegato, premere **F5**, selezionare **debug**  > **avviare il debug**o selezionare la freccia verde sulla barra degli strumenti di Visual Studio.

 ![Il&#95;&#95;debug&#95;di base dbg](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")

Durante il debug, un'evidenziazione gialla mostra la riga di codice che verrà eseguita successivamente.

 ![Modalità&#95;di&#95;break&#95;nozioni di base di dbg](../debugger/media/dbg_basics_break_mode.png "Modalità di interruzione")

La maggior parte delle finestre del debugger, come i **moduli** e le finestre **espressioni di controllo** , sono disponibili solo durante l'esecuzione del debugger. Alcune funzionalità del debugger, ad esempio la visualizzazione dei valori delle variabili nella finestra **variabili locali** o la valutazione delle espressioni nella finestra **espressioni di controllo** , sono disponibili solo quando il debugger viene sospeso in corrispondenza di un punto di interruzione, detto anche *modalità di interruzione*.

In modalità di interruzioni, l'esecuzione dell'app viene sospesa mentre le funzioni, le variabili e gli oggetti rimangono in memoria. È possibile esaminare le posizioni e gli Stati degli elementi per cercare violazioni o bug. Per alcuni tipi di progetto, è anche possibile apportare modifiche all'app in modalità di interruzioni. Per un video che illustra queste funzionalità, vedere [Introduzione con il debugger](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).

Se si interrompe il codice che non dispone di file di origine o di simboli (con*estensione PDB*) caricati, il debugger visualizza una pagina **file di origine non trovati** o **simboli non trovati** che consentono di trovare e caricare i file. Vedere [Specificare file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Se non è possibile caricare i file di simboli o di origine, è comunque possibile eseguire il debug delle istruzioni di assembly nella finestra **Disassembly** .

Non è sempre necessario avviare il debug avviando un'app all'inizio. È anche possibile premere **F11** per eseguire l' [istruzione del codice](#BKMK_Step_into__over__or_out_of_the_code), premere **F10** per eseguire l'istruzione/routine del [codice](#BKMK_Step_over_Step_out)oppure [eseguire fino a una posizione o una funzione specifica](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All).

## <a name="step-through-code"></a>Esecuzione del codice un'istruzione alla volta

I comandi dei passaggi del debugger consentono di esaminare lo stato dell'app o di ottenere altre informazioni sul flusso di esecuzione.

Se è necessario trovare il punto di ingresso nell'app, iniziare con **F10** o **F11**.

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a>Esegui istruzione codice riga per riga

Per arrestare ogni riga di codice o istruzione durante il debug, utilizzare **debug**  > **Esegui istruzione**oppure premere **F11**.

Il debugger esegue le istruzioni del codice, non le righe fisiche. Ad esempio, una clausola `if` può essere scritta in una riga:

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

Tuttavia, quando si esegue l'istruzione in questa riga, il debugger considera la condizione come un unico passaggio e la conseguenza. Nell'esempio precedente, la condizione è true.

In una chiamata di funzione annidata, scegliendo **Esegui istruzione** verrà eseguita la funzione annidata più interna. Se, ad esempio, si utilizza **Esegui istruzione** in una chiamata come `Func1(Func2())`, il debugger esegue la procedura nella `Func2` della funzione.

>[!TIP]
>Quando si esegue ogni riga di codice, è possibile passare il mouse sulle variabili per visualizzarne i valori oppure utilizzare le finestre variabili [locali](autos-and-locals-windows.md) e [espressioni di controllo](watch-and-quickwatch-windows.md) per controllare la modifica dei valori. È inoltre possibile tracciare visivamente lo stack di chiamate durante l'esecuzione di funzioni. Vedere [eseguire il mapping dei metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="BKMK_Step_over_Step_out"></a>Eseguire il codice un'istruzione alla volta e ignorare alcune funzioni

È possibile che non si sia interessati a una funzione durante il debug o si sappia che funziona, come il codice di libreria testato correttamente. Per ignorare il codice, è possibile usare i comandi seguenti. Le funzioni sono ancora in esecuzione, ma il debugger ne ignora.

|Comando tastiera|Comando di menu debug|Descrizione|
|----------------------|------------------|-----------------|
|**F10**|**Esegui istruzione/routine**|Se la riga corrente contiene una chiamata di funzione, Esegui **istruzione/** routine esegue il codice, quindi sospende l'esecuzione in corrispondenza della prima riga di codice dopo la restituzione della funzione chiamata.|
|**MAIUSC**+**F11**|**Esci da istruzione/routine**|Esci **da istruzione/uscita** continua a eseguire il codice e sospende l'esecuzione quando restituisce la funzione corrente. Il debugger ignora la funzione corrente.|

## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Eseguire fino a una posizione o una funzione specifica

È possibile che si preferisca eseguire direttamente una posizione o una funzione specifica quando si conosce esattamente il codice da ispezionare o si conosce la posizione in cui si desidera avviare il debug.

### <a name="run-to-a-breakpoint-in-code"></a>Eseguire fino a un punto di interruzione nel codice

Per impostare un punto di interruzione semplice nel codice, fare clic sul margine a sinistra accanto alla riga di codice in cui si desidera sospendere l'esecuzione. È anche possibile selezionare la riga e premere **F9**, selezionare **debug**  > **Imposta/Rimuovi**punto di interruzione oppure fare clic con il pulsante destro del mouse **e selezionare punto di interruzione  > ** Inserisci punto di**interruzione**. Il punto di interruzione viene visualizzato come un punto rosso nel margine sinistro accanto alla riga di codice. Il debugger sospende l'esecuzione immediatamente prima dell'esecuzione della riga.

![Imposta un punto di interruzione](../debugger/media/dbg_basics_setbreakpoint.png "Imposta punto di interruzione")

I punti di interruzione in Visual Studio forniscono un'ampia gamma di funzionalità aggiuntive, ad esempio punti di interruzione e punti di analisi condizionali. Per informazioni dettagliate, vedere uso dei punti di [interruzione](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Eseguire fino a un punto di interruzione della funzione

È possibile indicare al debugger di eseguire fino a quando non raggiunge una funzione specificata. È possibile specificare la funzione inserendo il nome oppure sceglierla dallo stack di chiamate.

**Per specificare un punto di interruzione della funzione in base al nome**

1. Selezionare **Debug**  > **nuovo** punto di interruzione  >  punto di**interruzione della funzione**

1. Nella finestra di dialogo nuovo punto di **interruzione della funzione** Digitare il nome della funzione e selezionare la lingua corrispondente.

   ![Finestra di dialogo nuovo punto di interruzione della funzione](../debugger/media/dbg_execution_newbreakpoint.png "Nuovo punto di interruzione della funzione")

1. Scegliere **OK**.

Se la funzione è in overload o in più di uno spazio dei nomi, è possibile scegliere quella desiderata nella finestra punti di **interruzione** .

![Punti di interruzione di funzione in overload](../debugger/media/dbg_execution_overloadedbreakpoints.png "Punti di interruzione di funzione in overload")

**Per selezionare un punto di interruzione della funzione nello stack di chiamate**

1. Durante il debug, aprire la finestra **stack di chiamate** selezionando **Debug**  > **Windows**  > **stack di chiamate**.

1. Nella finestra **stack di chiamate** fare clic con il pulsante destro del mouse su una funzione e scegliere **Esegui fino al cursore**oppure premere **CTRL** +**F10**.

Per tracciare visivamente lo stack di chiamate, vedere [eseguire il mapping dei metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Eseguire fino a una posizione del cursore

Per eseguire fino alla posizione del cursore, nel codice sorgente o nella finestra **stack di chiamate** selezionare la riga in corrispondenza della quale si desidera interrompere l'esecuzione, fare clic con il pulsante destro del mouse e scegliere **Esegui fino al cursore**oppure premere **CTRL** +**F10**. Selezionare **Esegui fino al cursore** equivale a impostare un punto di interruzione temporaneo.

### <a name="run-to-click"></a>Esegui fino alla riga selezionata

Mentre è sospesa nel debugger, è possibile passare il puntatore del mouse su un'istruzione nel codice sorgente o nella finestra **Disassembly** e selezionare l'icona **Esegui esecuzione in questa** freccia verde. L'utilizzo **di run per fare clic** Elimina la necessità di impostare un punto di interruzione temporaneo.

![Esegui fino al clic](../debugger/media/dbg-run-to-click.png "Esegui fino alla riga selezionata")

> [!NOTE]
> L' **esecuzione fino al clic** è disponibile a partire da [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

### <a name="manually-break-into-code"></a>Inserire un'interruzione nel codice manualmente

Per interrompere la successiva riga di codice disponibile in un'app in esecuzione, selezionare **Debug**  > **Interrompi tutto**oppure premere **CTRL** +**ALT** +**Interrompi**.

## <a name="BKMK_Set_the_next_statement_to_execute"></a>Spostare il puntatore per modificare il flusso di esecuzione

Mentre il debugger viene sospeso, una freccia gialla nel margine della finestra del codice sorgente o del **Disassembly** contrassegna la posizione dell'istruzione successiva da eseguire. È possibile modificare l'istruzione successiva per l'esecuzione spostando la freccia. È possibile ignorare una parte del codice oppure tornare a una riga precedente. Lo stato di un puntatore è utile per situazioni come ignorare una sezione di codice che contiene un bug noto.

 ![Spostare il puntatore](../debugger/media/dbg_basics_example3.gif "Spostare il puntatore")

Per modificare l'istruzione successiva da eseguire, il debugger deve essere in modalità di interruzione. Nella finestra codice sorgente o **Disassembly** trascinare la freccia gialla in una riga diversa oppure fare clic con il pulsante destro del mouse sulla riga che si desidera eseguire successivamente e scegliere **Imposta istruzione successiva**.

Il contatore del programma passa direttamente alla nuova posizione e le istruzioni tra il vecchio e il nuovo punto di esecuzione non vengono eseguite. Tuttavia, se si sposta il punto di esecuzione all'indietro, le istruzioni che interessano non vengono annullate.

>[!CAUTION]
>- Lo spostamento dell'istruzione successiva in corrispondenza di un'altra funzione o ambito provoca in genere un errore dello stack di chiamate e, conseguentemente, un errore o un'eccezione di runtime. Se si sposta l'istruzione successiva in corrispondenza di un altro ambito, verrà visualizzata una finestra di dialogo contenente un avviso e in cui si può scegliere di annullare l'operazione.
>- In Visual Basic non è possibile spostare l'istruzione successiva in corrispondenza di un altro ambito o di un'altra funzione.
>- Se in C++ nativo sono abilitati i controlli runtime, l'impostazione dell'istruzione successiva può causare la generazione di un'eccezione quando l'esecuzione raggiunge la fine del metodo.
>- Quando l'opzione Modifica e continuazione è abilitata, **Imposta istruzione successiva** avrà esito negativo se sono state effettuate modifiche per cui Modifica e continuazione non è immediatamente in grado di eseguire nuovamente il mapping. Ad esempio questo può accadere se è stato modificato del codice all'interno di un blocco catch. Quando si verifica questo problema, viene visualizzato un messaggio di errore che indica che l'operazione non è supportata.
>- Nel codice gestito non è possibile spostare l'istruzione successiva se:
>   - L'istruzione successiva è inclusa in un metodo diverso da quello dell'istruzione corrente.
>   - Il debug è stato avviato dal debug JIT.
>   - È in corso la rimozione di uno stack di chiamate.
>   - È stata generata un'eccezione System.StackOverflowException or System.Threading.ThreadAbortException.

## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Debug del codice non utente

Per impostazione predefinita, il debugger tenta di eseguire il debug solo del codice dell'app abilitando un'impostazione denominata *Just My Code*. Per ulteriori informazioni sul funzionamento di questa funzionalità per diversi tipi di progetto e linguaggi e su come è possibile personalizzarla, vedere [Just My Code](../debugger/just-my-code.md).

Per esaminare il codice del Framework, il codice della libreria di terze parti o le chiamate di sistema durante il debug, è possibile disabilitare Just My Code. In **strumenti** (o **debug**) > **Opzioni**  > **debug**deselezionare la casella di controllo **Abilita Just My Code** . Quando Just My Code è disabilitato, il codice non utente viene visualizzato nelle finestre del debugger e il debugger può eseguire un'istruzione nel codice non utente.

> [!NOTE]
> Just My Code non è supportato per progetti per dispositivi.

### <a name="debug-system-code"></a>Debug del codice di sistema

Se sono stati caricati i simboli di debug per il codice di sistema Microsoft e sono stati disabilitati Just My Code, è possibile eseguire un'istruzione in una chiamata di sistema proprio come qualsiasi altra chiamata.

Per caricare i simboli Microsoft, vedere [configurare i percorsi dei simboli e le opzioni di caricamento](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Per caricare i simboli per un componente di sistema specifico:**

1. Durante il debug, aprire la finestra **moduli** selezionando **debug**  > **moduli**di**Windows**  >  o premendo **CTRL** +**ALT** +**U**.

1. Nella finestra **moduli** è possibile indicare i moduli con i simboli caricati nella colonna **stato simboli** . Fare clic con il pulsante destro del mouse sul modulo per il quale si desidera caricare i simboli e selezionare **Carica simboli**.

## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Eseguire istruzioni di proprietà e operatori nel codice gestito
 Il debugger esegue le istruzioni/routine di proprietà e operatori nel codice gestito per impostazione predefinita. Nella maggior parte dei casi, l'esperienza di debug risulta notevolmente migliorata. Per abilitare l'esecuzione di un'istruzione in proprietà o operatori, scegliere **Debug**  > **Opzioni**. Nella pagina **Debug** > **Generale** deselezionare la casella di controllo **Esegui istruzione/routine di proprietà e operatori (solo gestito)** .

## <a name="see-also"></a>Vedere anche
- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Tecniche e strumenti di debug](../debugger/write-better-code-with-visual-studio.md)
- [Esaminare prima di tutto il debug](../debugger/debugger-feature-tour.md)
