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
ms.openlocfilehash: 5c5a57c41753c8689e83da2a6f8473fa643a657f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041578"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Spostarsi nel codice con il debugger di Visual Studio

Il debugger di Visual Studio consentono di spostarsi nel codice per controllare lo stato di un'app e visualizzare il flusso di esecuzione. È possibile utilizzare i tasti di scelta rapida, i comandi di debug, i punti di interruzione e altre funzionalità per visualizzare rapidamente il codice da esaminare. Familiarità con i comandi di navigazione del debugger e tasti di scelta rapida rende più veloce e semplice trovare e risolvere i problemi delle app.  Se questa è la prima volta che si è provato a eseguire il debug di codice, è possibile leggere [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) e [tecniche e strumenti di debug](../debugger/write-better-code-with-visual-studio.md) prima di procedere con questo articolo.

## <a name="basic-debugging"></a>Debug di base

Per avviare l'app con il debugger collegato, premere **F5**, selezionare **Debug** > **Avvia debug**, oppure selezionare la freccia verde sulla barra degli strumenti di Visual Studio.

 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")

Durante il debug, evidenziato in giallo indica la riga di codice che eseguirà successivo.

 ![DBG&#95;nozioni di base&#95;Break&#95;modalità](../debugger/media/dbg_basics_break_mode.png "modalità di interruzione")

Più finestre del debugger, ad esempio la **moduli** e **Watch** windows, sono disponibili solo durante l'esecuzione del debugger. Alcune funzionalità di debug, ad esempio per visualizzare i valori delle variabili di **variabili locali** finestra o la valutazione delle espressioni nel **Watch** finestra, sono disponibili solo mentre il debugger viene sospeso in un punto di interruzione, detto anche *modalità di interruzione*.

In modalità di interruzione, l'esecuzione di app viene sospesa durante le funzioni, variabili e oggetti restano in memoria. È possibile esaminare la posizione degli elementi e gli stati per individuare le violazioni o bug. Per alcuni tipi di progetto, è anche possibile apportare modifiche all'app in modalità di interruzione. Per un video che illustra queste funzionalità, vedere [Guida introduttiva con il Debugger](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).

Se si interrompe nel codice che non dispone di origine o simboli (*PDB*) i file caricati, il debugger visualizza una **file di origine non trovati** o **simboli non trovati** pagina che può aiutarti Individuare e caricare i file. Vedere [Specificare file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Se non è possibile caricare i file di simboli o di origine, è possibile comunque eseguire il debug le istruzioni dell'assembly nel **Disassembly** finestra.

Non sempre è necessario avviare il debug eseguendo l'avvio di un'app all'inizio. È anche possibile premere **F11** al [istruzioni nel codice](#BKMK_Step_into__over__or_out_of_the_code), premere **F10** al [Esegui istruzione/routine di codice](#BKMK_Step_over_Step_out), o [eseguiti in un percorso specifico o funzione](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All).

## <a name="step-through-code"></a>Esecuzione del codice un'istruzione alla volta

I comandi di passaggio del debugger consentono di controllare lo stato dell'app o altre informazioni sul flusso di esecuzione.

Se è necessario trovare il punto di ingresso nell'app, iniziare con **F10** oppure **F11**.

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a> L'istruzione nel codice riga per riga

Per arrestare in ogni riga del codice o dell'istruzione durante il debug, usare **Debug** > **Esegui istruzione**, oppure premere **F11**.

Il debugger avanza tramite le istruzioni di codice, le righe non fisiche. Ad esempio, una clausola `if` può essere scritta in una riga:

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

Tuttavia, quando esegue l'istruzione in questa riga, il debugger considera la condizione come un unico passaggio, di conseguenza come un altro. Nell'esempio precedente, la condizione è true.

In una chiamata di funzione annidata, scegliendo **Esegui istruzione** verrà eseguita la funzione annidata più interna. Ad esempio, se si usa **Esegui istruzione** in una chiamata, ad esempio `Func1(Func2())`, il debugger eseguirà l'istruzione nella funzione `Func2`.

>[!TIP]
>Quando si esegue ogni riga di codice, è possibile passare il mouse sulle variabili per visualizzare i relativi valori oppure usare il [variabili locali](autos-and-locals-windows.md) e [Watch](watch-and-quickwatch-windows.md) windows per verificare i valori di passaggio. Si può anche rilevare visivamente lo stack di chiamata durante l'esecuzione di funzioni. Visualizzare [mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="BKMK_Step_over_Step_out"></a> Esaminare il codice e ignorare alcune funzioni

Potrebbe non rilevante una funzione durante il debug o si conosce funziona, come il codice ben collaudato della libreria. È possibile usare i comandi seguenti da ignorare nel codice. Le funzioni eseguono comunque, ma li ignora il debugger.

|Comando di tasti|Comando del menu Debug|Descrizione|
|----------------------|------------------|-----------------|
|**F10**|**Esegui istruzione/routine**|Se la riga corrente contiene una chiamata di funzione **Esegui istruzione/routine** esegue il codice, quindi viene sospesa alla prima riga del codice dopo che la funzione chiamata viene restituita.|
|**MAIUSC**+**F11**|**Esci da istruzione/routine**|**Esci da istruzione /** continua l'esecuzione di codice e sospende l'esecuzione quando termina la funzione corrente. Il debugger passa attraverso la funzione corrente.|

## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Eseguire fino a un percorso specifico o (funzione)

È preferibile eseguire direttamente a una posizione specifica o una funzione quando si sa esattamente quale codice si desidera controllare o si conosce in cui si desidera avviare il debug.

### <a name="run-to-a-breakpoint-in-code"></a>Eseguire un punto di interruzione nel codice

Per impostare un punto di interruzione semplice nel codice, fare clic sul margine a sinistra accanto alla riga di codice in cui si desidera sospendere l'esecuzione. È anche possibile selezionare la riga e premere **F9**, selezionare **Debug** > **Attiva/Disattiva punto di interruzione**, o fare doppio clic e selezionare **puntodiinterruzione**  >  **Inserisci punto di interruzione**. Il punto di interruzione viene visualizzato come un punto rosso nel margine sinistro accanto alla riga di codice. Il debugger sospende l'esecuzione prima dell'esecuzione di riga.

![Impostare un punto di interruzione](../debugger/media/dbg_basics_setbreakpoint.png "Impostare un punto di interruzione")

I punti di interruzione in Visual Studio forniscono un'ampia gamma di funzionalità aggiuntive, ad esempio punti di interruzione e punti di analisi condizionali. Per informazioni dettagliate, vedere [usando i punti di interruzione](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Eseguire un punto di interruzione (funzione)

È possibile impostare il debugger per l'esecuzione finché non raggiunge una funzione specificata. È possibile specificare la funzione inserendo il nome oppure sceglierla dallo stack di chiamate.

**Per specificare il nome di un punto di interruzione (funzione)**

1. Selezionare **Debug** > **nuovo punto di interruzione** > **interruzione della funzione**

1. Nel **nuovo punto di interruzione di funzione** finestra di dialogo digitare il nome della funzione e selezionare la lingua.

   ![Finestra di dialogo Nuovo punto di interruzione di funzione](../debugger/media/dbg_execution_newbreakpoint.png "nuovo punto di interruzione (funzione)")

1. Scegliere **OK**.

Se la funzione è sottoposta a overload o in più di uno spazio dei nomi, è possibile scegliere quello desiderato nel **i punti di interruzione** finestra.

![I punti di interruzione di funzione in overload](../debugger/media/dbg_execution_overloadedbreakpoints.png "i punti di interruzione di funzione in overload")

**Per selezionare un punto di interruzione di funzione dallo stack di chiamate**

1. Durante il debug, aprire il **Stack di chiamate** finestra selezionando **Debug** > **Windows** > **Stack di chiamate**.

1. Nel **Stack di chiamate** finestra, fare doppio clic su una funzione e selezionare **Esegui fino al cursore**, oppure premere **Ctrl**+**F10**.

Per tracciare visivamente lo stack di chiamate, vedere [mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Esecuzione in una posizione del cursore

Per l'esecuzione alla posizione del cursore, nel codice sorgente o il **Stack di chiamate** finestra, selezionare la riga di cui si desidera un'interruzione in corrispondenza del mouse e scegliere **Esegui fino al cursore**, oppure premere **Ctrl** + **F10**. Selezionando **Esegui fino al cursore** corrisponde all'impostazione di un punto di interruzione temporaneo.

### <a name="run-to-click"></a>Esegui fino alla riga selezionata

Durante la pausa del debugger, è possibile posizionarsi su un'istruzione nel codice sorgente o il **Disassembly** finestra e selezionare il **esecuzione qui** icona della freccia verde. Usando **Esegui fino al clic** Elimina la necessità di impostare un punto di interruzione temporaneo.

![Esegui fino alla riga selezionata](../debugger/media/dbg-run-to-click.png "Esegui fino alla riga selezionata")

> [!NOTE]
> **Esegui fino al clic** è disponibile a partire da [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

### <a name="manually-break-into-code"></a>Inserire un'interruzione nel codice manualmente

Per inserire un'interruzione nella riga successiva disponibile di codice in un'app in esecuzione, selezionare **Debug** > **Interrompi tutto**, oppure premere **Ctrl**+**Alt**  + **Interrompi**.

## <a name="BKMK_Set_the_next_statement_to_execute"></a> Spostare il puntatore del mouse per modificare il flusso di esecuzione

Quando il debugger viene sospeso, ovvero la freccia gialla nel margine del codice sorgente oppure **Disassembly** finestra contrassegna la posizione dell'istruzione successiva da eseguire. È possibile modificare l'istruzione successiva da eseguire tramite lo spostamento della freccia. È possibile ignorare un segmento di codice o tornare a una riga precedente. Spostando il puntatore è utile per le situazioni, ad esempio ignorare una sezione di codice che contiene un bug noto.

 ![Spostare il puntatore](../debugger/media/dbg_basics_example3.gif "spostare il puntatore del mouse")

Per modificare l'istruzione successiva da eseguire, il debugger deve essere in modalità di interruzione. Nel codice sorgente oppure **Disassembly** finestra, trascinare la freccia gialla in una riga diversa o fare doppio clic sulla riga di cui si desidera eseguire successivamente e selezionare **Imposta istruzione successiva**.

Il contatore del programma passa direttamente al nuovo percorso e istruzioni tra le esecuzioni precedenti e nuove punti non vengono eseguiti. Tuttavia, se si sposta il punto di esecuzione con le versioni precedenti, le istruzioni intermedi non sono annullate.

>[!CAUTION]
>- Lo spostamento dell'istruzione successiva in corrispondenza di un'altra funzione o ambito provoca in genere un errore dello stack di chiamate e, conseguentemente, un errore o un'eccezione di runtime. Se si sposta l'istruzione successiva in corrispondenza di un altro ambito, verrà visualizzata una finestra di dialogo contenente un avviso e in cui si può scegliere di annullare l'operazione.
>- In Visual Basic non è possibile spostare l'istruzione successiva in corrispondenza di un altro ambito o di un'altra funzione.
>- Se in C++ nativo sono abilitati i controlli runtime, l'impostazione dell'istruzione successiva può causare la generazione di un'eccezione quando l'esecuzione raggiunge la fine del metodo.
>- Quando l'opzione Modifica e continuazione è abilitata, **Imposta istruzione successiva** avrà esito negativo se sono state effettuate modifiche per cui Modifica e continuazione non è immediatamente in grado di eseguire nuovamente il mapping. Ad esempio questo può accadere se è stato modificato del codice all'interno di un blocco catch. In questo caso, un messaggio di errore indica che l'operazione non è supportato.
>- Nel codice gestito, è possibile spostare l'istruzione successiva se:
>   - L'istruzione successiva è inclusa in un metodo diverso da quello dell'istruzione corrente.
>   - Il debug è stato avviato da Just-In-Time di debug.
>   - Uno svuotamento dello stack di chiamate è in corso.
>   - È stata generata un'eccezione System.StackOverflowException or System.Threading.ThreadAbortException.

## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Eseguire il debug di codice non utente

Per impostazione predefinita, il debugger tenta di eseguire il debug solo il codice dell'app abilitando un'impostazione denominata *Just My Code*. Per altre informazioni dettagliate sul funzionamento di questa funzionalità per diversi tipi di progetto e linguaggi, e come è possibile personalizzare, vedere [Just My Code](../debugger/just-my-code.md).

Per esaminare il codice di framework, il codice della libreria di terze parti o le chiamate di sistema durante il debug, è possibile disabilitare Just My Code. In **degli strumenti** (o **Debug**) > **opzioni** > **debug**, deselezionare il **Abilita Just My Code** casella di controllo. Quando Just My Code è disabilitato, il codice non utente viene visualizzato nelle finestre del debugger e il debugger può eseguire il codice non utente.

> [!NOTE]
> Just My Code non è supportato per progetti per dispositivi.

### <a name="debug-system-code"></a>Il debug del codice di sistema

Se si sono caricati simboli di debug per codice di sistema di Microsoft e disabilitato Just My Code, è possibile eseguire una chiamata di sistema esattamente come qualsiasi altra chiamata.

Per caricare i simboli Microsoft, vedere [configurare i percorsi dei simboli e le opzioni di caricamento](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Per caricare i simboli per un componente di sistema specifici:**

1. Durante il debug, aprire il **moduli** finestra selezionando **Debug** > **Windows** > **moduli**, o premendo **Ctrl**+**Alt**+**U**.

1. Nel **moduli** finestra, è possibile indicare che i moduli disponibili simboli caricati nel **stato simboli** colonna. Fare clic sul modulo che si desidera caricare i simboli e selezionare **caricare i simboli**.

## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Eseguire istruzioni di proprietà e operatori nel codice gestito
 Il debugger esegue le istruzioni/routine di proprietà e operatori nel codice gestito per impostazione predefinita. Nella maggior parte dei casi, l'esperienza di debug risulta notevolmente migliorata. Per abilitare l'esecuzione di operatori o proprietà, scegliere **Debug** > **opzioni**. Nella pagina **Debug** > **Generale** deselezionare la casella di controllo **Esegui istruzione/routine di proprietà e operatori (solo gestito)**.

## <a name="see-also"></a>Vedere anche
- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Tecniche e strumenti di debug](../debugger/write-better-code-with-visual-studio.md)
- [Presentazione di debug](../debugger/debugger-feature-tour.md)
