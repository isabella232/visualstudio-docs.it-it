---
title: Usare i punti di interruzione nel debugger. Documenti Microsoft
ms.custom: ''
ms.date: 10/28/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6a8ee96834fc20186ba6719a7c4f377fea45d6b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302035"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Usare i punti di interruzione nel debugger di Visual StudioUse breakpoints in the Visual Studio debugger

I punti di interruzione sono una delle tecniche di debug più importanti nella casella degli strumenti dello sviluppatore. Impostare i punti di interruzione in qualsiasi punto si desidera sospendere l'esecuzione del debugger. Ad esempio, è possibile visualizzare lo stato delle variabili di codice o esaminare lo stack di chiamate in corrispondenza di un determinato punto di interruzione.  Se si sta tentando di risolvere un avviso o un problema durante l'utilizzo dei punti di interruzione, vedere [Risolvere i problemi relativi ai punti](../debugger/troubleshooting-breakpoints.md)di interruzione nel debugger di Visual Studio .

> [!NOTE]
> Se si conosce l'attività o il problema che si sta tentando di risolvere, ma è necessario conoscere il tipo di punto di interruzione da utilizzare, vedere [Individuare l'attività](../debugger/find-your-debugging-task.md#pause-running-code)di debug .

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a>Impostare punti di interruzione nel codice sorgenteSet breakpoints in source code

È possibile impostare un punto di interruzione in qualsiasi riga di codice eseguibile. Nel codice C, ad esempio, è possibile impostare un `for` punto di interruzione sulla `for` dichiarazione di variabile, sul ciclo o su qualsiasi codice all'interno del ciclo. Non è possibile impostare un punto di interruzione per lo spazio dei nomi o le dichiarazioni di classe o sulla firma del metodo.

Per impostare un punto di interruzione nel codice sorgente, fare clic sul margine all'estrema sinistra accanto a una riga di codice. È inoltre possibile selezionare la riga e premere **F9**, selezionare **Debug** > **Toggle Breakpoint**oppure fare clic con il pulsante destro del mouse e scegliere **Punto** > di interruzione Inserisci punto di**interruzione**. Il punto di interruzione viene visualizzato come un punto rosso nel margine sinistro.

Per la maggior parte dei linguaggi, inclusi i linguaggi, i punti di interruzione e le righe di esecuzione correnti vengono evidenziati automaticamente. Per il codice C, è possibile attivare l'evidenziazione dei punti di interruzione e delle righe correnti selezionando **Strumenti** (o **Debug)**> **Opzioni** > **di debug** >  **Evidenzia l'intera riga di origine per i punti di interruzione e l'istruzione corrente (solo C.**

![Impostare un punto di interruzioneSet a breakpoint](../debugger/media/basicbreakpoint.png "Punto di interruzione di baseBasic breakpoint")

Quando si esegue il debug, l'esecuzione viene sospesa in corrispondenza del punto di interruzione, prima che venga eseguito il codice su tale riga. Il simbolo del punto di interruzione mostra una freccia gialla.

In corrispondenza del punto di `testInt` interruzione nell'esempio seguente, il valore di è ancora 1. Pertanto, il valore non è stato modificato da quando la variabile è stata inizializzata (impostata su un valore pari a 1) perché l'istruzione in giallo non è ancora stata eseguita.

![Esecuzione punto di interruzione arrestata](../debugger/media/breakpointexecution.png "Esecuzione dei punti di interruzione")

Quando il debugger si arresta in corrispondenza del punto di interruzione, è possibile esaminare lo stato corrente dell'app, inclusi i valori delle [variabili](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) e lo stack di [chiamate.](../debugger/how-to-use-the-call-stack-window.md)

Di seguito sono riportate alcune istruzioni generali per l'utilizzo dei punti di interruzione.

- Il punto di interruzione è un interruttore. È possibile fare clic su di esso, premere **F9**o utilizzare **Debug** > **Toggle Breakpoint** per eliminarlo o reinserirlo.

- Per disabilitare un punto di interruzione senza eliminarlo, posizionare il puntatore del mouse o fare clic con il pulsante destro del mouse su di esso e selezionare **Disattiva punto di interruzione**. I punti di interruzione disabilitati vengono visualizzati come punti vuoti nel margine sinistro o nella finestra **Punti di interruzione.** Per riattivare un punto di interruzione, passare il mouse o fare clic con il pulsante destro del mouse su di esso e selezionare **Abilita punto di interruzione**.

- Impostare condizioni e azioni, aggiungere e modificare etichette o esportare un punto di interruzione facendo clic con il pulsante destro del mouse su di esso e selezionando il comando appropriato oppure passando il mouse su di esso e selezionando l'icona **Impostazioni.**

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Azioni e punti di analisi dei punti di analisi dei punti di analisi

Un punto di *analisi* è un punto di interruzione che stampa un messaggio nella finestra **di output.** Un punto di analisi può agire come un'istruzione di traccia temporanea nel linguaggio di programmazione e non sospende l'esecuzione del codice. Per creare un punto di analisi, impostare un'azione speciale nella finestra **Impostazioni punto di interruzione.** Per istruzioni dettagliate, vedere Usare i punti di [analisi nel debugger](../debugger/using-tracepoints.md)di Visual Studio .

## <a name="breakpoint-conditions"></a>Condizioni punto di interruzione

È possibile controllare dove e quando un punto di interruzione viene eseguito impostando le condizioni. La condizione può essere qualsiasi espressione valida riconosciuta dal debugger. Per altre informazioni sulle espressioni valide, vedere [Espressioni nel debugger](../debugger/expressions-in-the-debugger.md).

**Per impostare una condizione del punto di interruzione:**

1. Fare clic con il pulsante destro del mouse sul simbolo del punto di interruzione e selezionare **Condizioni**. In alternativa, passare il puntatore del mouse sul simbolo del punto di interruzione, selezionare l'icona **Impostazioni** e quindi selezionare **Condizioni** nella finestra **Impostazioni punto di interruzione.**

   È inoltre possibile impostare le condizioni nella finestra **Punti di interruzione** facendo clic con il pulsante destro del mouse su un punto di interruzione e scegliendo **Impostazioni**, quindi **Condizioni**.

   ![Impostazioni del punto di interruzione](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. Nell'elenco a discesa selezionare **Espressione condizionale**, **Numero passaggi**o **Filtro**e impostare il valore di conseguenza.

3. Selezionare **Chiudi** o premere **CTRL**+**INVIO** per chiudere la finestra Impostazioni punto **di interruzione.** In alternativa, nella finestra **Punti di interruzione** selezionare **OK** per chiudere la finestra di dialogo.

I punti di interruzione **+** con condizioni impostate vengono visualizzati con un simbolo nel codice sorgente e nelle finestre **Punti di interruzione.**

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Creare un'espressione condizionaleCreate a conditional expression

Quando si seleziona **Espressione condizionale**, è possibile scegliere tra due condizioni: **è true** o Quando **modificato**. Scegliere **È vero** per interrompere quando l'espressione viene soddisfatta o Quando viene **modificata** in interruzione quando il valore dell'espressione viene modificato.

Nell'esempio seguente, il punto di interruzione `testInt` viene raggiunto solo quando il valore di è **4**:

![Condizione punto di interruzione true](../debugger/media/breakpointconditionistrue.png "Il punto di interruzione è vero")

Nell'esempio seguente, il punto di interruzione `testInt` viene raggiunto solo quando il valore delle modifiche:In the following example, the breakpoint is hit only when the value of changes:

![Punto di interruzione quando viene modificato](../debugger/media/breakpointwhenchanged.png "Punto di interruzione quando viene modificato")

Se si imposta una condizione del punto di interruzione con sintassi non valida, viene visualizzato un messaggio di avviso. Se viene specificata una condizione del punto di interruzione con sintassi valida ma con semantica non valida, viene visualizzato un messaggio di avviso la prima volta che si raggiunge il punto di interruzione. In entrambi i casi, il debugger si interrompe quando raggiunge il punto di interruzione non valido. Il punto di interruzione viene ignorato solo se la condizione è valida e restituisce `false`.

>[!NOTE]
>Il comportamento del campo **Quando modificato** è diverso per i diversi linguaggi di programmazione.
>- Per il codice nativo, il debugger non considera la prima valutazione della condizione come una modifica, pertanto non raggiunge il punto di interruzione nella prima valutazione.
>- Per il codice gestito, il debugger raggiunge il punto di interruzione nella prima valutazione dopo la **selezione dell'opzione Quando è** stata selezionata l'opzione Quando è stata selezionata l'opzione Quando è stata selezionata l'opzione Quando è stata selezionata l'opzione Viene modificata.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Usare gli ID oggetto nelle espressioni condizionali (solo C e F)

 In alcuni casi si desidera osservare il comportamento di un oggetto specifico. Ad esempio, è possibile scoprire perché un oggetto è stato inserito in una raccolta più di una volta. In C# e F# è possibile creare ID oggetto per istanze specifiche dei [tipi riferimento](/dotnet/csharp/language-reference/keywords/reference-types) e usarle nelle condizioni del punto di interruzione. L'ID oggetto viene generato dai servizi di debug di Common Language Runtime (CLR) e associato all'oggetto.

**Per creare un ID oggetto:**

1. Impostare un punto di interruzione nel codice da qualche parte dopo la creazione dell'oggetto.

2. Avviare il debug e quando l'esecuzione viene sospesa in corrispondenza del punto di interruzione, selezionare **Debug** > variabili**locali di** **Windows** > o **Alt**+**4** per aprire la finestra **Variabili locali.**

   Individuare l'istanza dell'oggetto specifico nella finestra **Variabili locali,** fare clic con il pulsante destro del mouse su di essa e scegliere **Crea ID oggetto**.

   Dovresti vedere **$** un più un numero nella finestra **Variabili locali.** Si tratta dell'ID oggetto.

3. Aggiungere un nuovo punto di interruzione nel punto che si desidera analizzare; ad esempio, quando l'oggetto deve essere aggiunto alla raccolta. Fare clic con il pulsante destro del mouse sul punto di interruzione e scegliere **Condizioni**.

4. Utilizzare l'ID oggetto nel campo **Espressione condizionale.** Se, ad esempio, la `item` variabile è l'oggetto da aggiungere all'insieme, selezionare È **vero** e digitare **l'elemento\< **,>dove \<n> è il numero ID dell'oggetto.

   L'esecuzione si interromperà in corrispondenza del punto in cui l'oggetto deve essere aggiunto alla raccolta.

   Per eliminare l'ID oggetto, fare clic con il pulsante destro del mouse sulla variabile nella finestra **Variabili locali** e selezionare Elimina **ID oggetto**.

> [!NOTE]
> Gli ID oggetto creano riferimenti deboli e non impediscono all'oggetto di essere sottoposto a Garbage Collection. Sono validi solo per la sessione di debug corrente.

### <a name="set-a-hit-count-condition"></a>Impostare una condizione di conteggio dei passaggi

Se si sospetta che un ciclo nel codice inizi a comportarsi in modo non corretto dopo un determinato numero di iterazioni, è possibile impostare un punto di interruzione per interrompere l'esecuzione dopo tale numero di hit, anziché dover premere ripetutamente **F5** per raggiungere tale iterazione.

In **Condizioni** nella finestra **Impostazioni punto di interruzione** selezionare Numero **passaggi**, quindi specificare il numero di iterazioni. Nell'esempio seguente, il punto di interruzione è impostato per raggiungere ogni altra iterazione:In the following example, the breakpoint is set to hit on every other iteration:

![Conteggio passaggi punto di interruzione](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Impostare una condizione di filtro

È possibile limitare un punto di interruzione da attivare solo su dispositivi specificati o in thread e processi specificati.

In **Condizioni** nella finestra **Impostazioni punto di interruzione** selezionare **Filtro**e quindi immettere una o più delle espressioni seguenti:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Racchiudere i valori String tra virgolette doppie. È possibile combinare clausole usando `&` (AND), `||` (OR), `!` (NOT) e le parentesi.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Impostare i punti di interruzione delle funzioniSet function breakpoints

È possibile interrompere l'esecuzione quando viene chiamata una funzione. Ciò è utile, ad esempio, quando si conosce il nome della funzione ma non la relativa posizione. È inoltre utile se si dispone di funzioni con lo stesso nome e si desidera interromperle tutte (ad esempio funzioni in overload o funzioni in progetti diversi).

**Per impostare un punto di interruzione di funzione:To set a function breakpoint:**

1. Selezionare **Debug nuovo** > punto di**interruzione funzione**punto di**interruzione** > o premere **ALT**+**F9** > **Ctrl**+**B**.

   È anche possibile selezionare **Nuovo** > punto di**interruzione funzione** nella finestra Punti **di interruzione.**

1. Nella finestra di **dialogo Nuovo punto** di interruzione funzione immettere il nome della funzione nella casella **Nome funzione.**

   Per restringere la specifica della funzione:

   - Utilizzare il nome completo della funzione.

     Esempio:  `Namespace1.ClassX.MethodA()`

   - Aggiungere i tipi di parametro di una funzione in overload.

     Esempio:  `MethodA(int, string)`

   - Utilizzare il simbolo '!' per specificare il modulo.

     Esempio: `App1.dll!MethodA`

   - Utilizzare l'operatore di contesto nel linguaggio nativo di C.

     `{function, , [module]} [+<line offset from start of method>]`

     Esempio: `{MethodA, , App1.dll}+2`

1. Nell'elenco a discesa **Lingua** scegliere la lingua della funzione.

1. Selezionare **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Impostare un punto di interruzione di una funzione utilizzando un indirizzo di memoria (solo C
 È possibile utilizzare l'indirizzo di un oggetto per impostare un punto di interruzione di funzione su un metodo chiamato da un'istanza specifica di una classe.  Ad esempio, dato un oggetto `my_class`indirizzabile di tipo , `my_method` è possibile impostare un punto di interruzione di funzione sul metodo chiamato dall'istanza.

1. Impostare un punto di interruzione in un punto qualsiasi dopo la creazione di un'istanza della classe.

2. Trovare l'indirizzo dell'istanza `0xcccccccc`(ad esempio, ).

3. Selezionare **Debug nuovo** > punto di**interruzione funzione**punto di**interruzione** > o premere **ALT**+**F9** > **Ctrl**+**B**.

4. Aggiungere quanto segue alla casella **Nome funzione** e selezionare Il linguaggio **C.**

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Impostare punti di interruzione dati (.NET Core 3.0 o versione successiva)Set data breakpoints (.NET Core 3.0 or higher)

I punti di interruzione dei dati interrompono l'esecuzione quando la proprietà di un oggetto specifico viene modificata.

**Per impostare un punto di interruzione dei datiTo set a data breakpoint**

1. In un progetto .NET Core avviare il debug e attendere il raggiungimento di un punto di interruzione.

2. Nella finestra **Auto**, **Espressioni di controllo**o Variabili **locali,** fare clic con il pulsante destro del mouse su una proprietà e selezionare **Interrompi quando il valore cambia** nel menu di scelta rapida.

    ![Punto di interruzione dei dati gestiti](../debugger/media/managed-data-breakpoint.png "Punto di interruzione dei dati gestiti")

I punti di interruzione dei dati in .NET Core non funzioneranno per:Data breakpoints in .NET Core won't work for:

- Proprietà non espandibili nella descrizione comando, Variabili locali, Auto o finestra Espressioni di controllo
- Variabili statiche
- Classi con l'attributo DebuggerTypeProxy
- Campi all'interno di struct

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Impostare i punti di interruzione dei dati (solo C. nativo)

 I punti di interruzione dei dati interrompono l'esecuzione quando viene modificato un valore archiviato in un indirizzo di memoria specificato. Se il valore viene letto ma non modificato, l'esecuzione non viene interrotta.

**Per impostare un punto di interruzione dei dati:**

1. In un progetto di C, avviare il debug e attendere che venga raggiunto un punto di interruzione. Scegliere **Nuovo** > punto di**interruzione** dal menu **Debug**

    È inoltre possibile selezionare **Nuovo** > punto di**interruzione dati** nella finestra Punti **di interruzione** oppure fare clic con il pulsante destro del mouse su un elemento nella finestra **Auto**, Espressioni **di controllo**o Variabili **locali** e selezionare Interrompi quando il valore **viene modificato** nel menu di scelta rapida.

2. Nella casella **Indirizzo** digitare un indirizzo di memoria o un'espressione che restituisca un indirizzo di memoria. Ad esempio, digitare `&avar` per eseguire l'interruzione quando viene modificato il contenuto della variabile `avar` .

3. Nell'elenco a discesa **Conteggio byte** selezionare il numero di byte che si desidera controllare tramite il debugger. Ad esempio, se si seleziona **4**, il debugger controllerà i quattro byte a partire da `&avar` e si interromperà se viene modificato il valore di uno di questi byte.

I punti di interruzione dei dati non funzionano nelle condizioni seguenti:Data breakpoints don't work under the following conditions:
- Un processo di cui non viene eseguito il debug scrive nella posizione di memoria.
- La posizione di memoria è condivisa tra due o più processi.
- La posizione di memoria viene aggiornata all'interno del kernel. Ad esempio, se la memoria viene passata alla funzione Windows `ReadFile` a 32 bit, la memoria verrà aggiornata dalla modalità kernel, in modo che il debugger non si interrompa durante l'aggiornamento.
- Dove l'espressione di controllo è maggiore di 4 byte su hardware a 32 bit e 8 byte su hardware a 64 bit. Si tratta di una limitazione dell'architettura x86.

> [!NOTE]
> - I punti di interruzione dei dati dipendono da indirizzi di memoria specifici. L'indirizzo di una variabile cambia da una sessione di debug a quella successiva, in modo che i punti di interruzione dei dati vengano disabilitati automaticamente al termine di ogni sessione di debug.
>
> - Se si imposta un punto di interruzione dei dati in una variabile locale, il punto di interruzione resta abilitato quando la funzione termina, ma l'indirizzo di memoria non è più applicabile, pertanto il comportamento del punto di interruzione è imprevedibile. Se si imposta un punto di interruzione dati su una variabile locale, è necessario eliminare o disabilitare il punto di interruzione prima della fine della funzione.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Gestire i punti di interruzione nella finestra Punti di interruzione

 È possibile utilizzare la finestra **Punti di interruzione** per visualizzare e gestire tutti i punti di interruzione nella soluzione. Questa posizione centralizzata è particolarmente utile in una soluzione di grandi dimensioni o per scenari di debug complessi in cui i punti di interruzione sono critici.

Nella finestra **Punti di interruzione** è possibile cercare, ordinare, filtrare, abilitare/disabilitare o eliminare punti di interruzione. È inoltre possibile impostare condizioni e azioni o aggiungere una nuova funzione o un nuovo punto di interruzione dati.

Per aprire la finestra **Punti di interruzione,** selezionare **Debug** > **punti di interruzione**di**Windows** > oppure premere **Alt**+**F9** o **Ctrl**+**Alt**+**B**.

![Finestra Punti di interruzione](../debugger/media/breakpointswindow.png "finestra Punti di interruzione")

Per selezionare le colonne da visualizzare nella finestra **Punti di interruzione,** selezionare **Mostra colonne**. Selezionare un'intestazione di colonna per ordinare l'elenco dei punti di interruzione in base a tale colonna.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Etichette dei punti di interruzione
È possibile utilizzare le etichette per ordinare e filtrare l'elenco dei punti di interruzione nella finestra **Punti di interruzione.**

1. Per aggiungere un'etichetta a un punto di interruzione, fare clic con il pulsante destro del mouse sul punto di interruzione nel codice sorgente o nella finestra **Punti di interruzione,** quindi scegliere **Modifica etichette**. Aggiungere una nuova etichetta o sceglierne una esistente, quindi scegliere **OK**.
2. Ordinare l'elenco dei punti di interruzione nella finestra **Punti di interruzione** selezionando **Etichette**, **Condizioni**o altre intestazioni di colonna. È possibile selezionare le colonne da visualizzare selezionando **Mostra colonne** nella barra degli strumenti.

### <a name="export-and-import-breakpoints"></a>Esportare e importare punti di interruzione
 Per salvare o condividere lo stato e la posizione dei punti di interruzione, è possibile esportarli o importarli.

- Per esportare un singolo punto di interruzione in un file XML, fare clic con il pulsante destro del mouse sul punto di interruzione nella finestra Codice sorgente o **Punti di interruzione** e selezionare **Esporta** o **Esporta selezionato**. Selezionare un percorso di esportazione e quindi **selezionare Salva**. Il percorso predefinito è la cartella della soluzione.
- Per esportare più punti di interruzione, nella finestra **Punti di interruzione** selezionare le caselle accanto ai punti di interruzione o immettere i criteri di ricerca nel campo **Cerca.** Selezionare l'icona **Esporta tutti i punti di interruzione corrispondenti all'icona dei criteri** di ricerca correnti e salvare il file.
- Per esportare tutti i punti di interruzione, deselezionate tutte le caselle e lasciate vuoto il campo **Cerca.** Selezionare l'icona **Esporta tutti i punti di interruzione corrispondenti all'icona dei criteri** di ricerca correnti e salvare il file.
- Per importare punti di interruzione, nella finestra **Punti di interruzione** selezionare l'icona Importa punti di interruzione da un **file,** passare al percorso del file XML e scegliere **Apri**.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>Impostare punti di interruzione dalle finestre del debuggerSet breakpoints from debugger windows

È inoltre possibile impostare punti di interruzione dalle finestre del debugger **Stack di chiamate** e **Disassembly.**

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Impostare un punto di interruzione nella finestra Stack di chiamate

 Per interrompersi in corrispondenza dell'istruzione o della riga a cui ritorna una funzione chiamante, è possibile impostare un punto di interruzione nella finestra **Stack di chiamate.**

**Per impostare un punto di interruzione nella finestra Stack di chiamate:To set a breakpoint in the Call Stack window:**

1. Per aprire la finestra **Stack di chiamate,** è necessario essere sospesi durante il debug. Selezionare **Esegui debug** > **stack di chiamate****Windows** > oppure premere **CTRL**+**Alt**+**C**.

2. Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sulla funzione chiamante e scegliere Punto **di** > **interruzione Inserisci punto**di interruzione oppure premere **F9**.

   Accanto al nome della chiamata di funzione nel margine sinistro dello stack di chiamate viene visualizzato un simbolo di punto di interruzione.

Il punto di interruzione dello stack di chiamate viene visualizzato nella finestra **Punti di interruzione** come indirizzo, con una posizione di memoria che corrisponde all'istruzione eseguibile successiva nella funzione.

Il debugger si interrompe in corrispondenza dell'istruzione.

Per ulteriori informazioni sullo stack di chiamate, vedere [Procedura: utilizzare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

Per tracciare visivamente i punti di interruzione durante l'esecuzione del codice, vedere Eseguire il mapping di metodi nello stack di [chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Impostare un punto di interruzione nella finestra Disassembly

1. Per aprire la finestra **Disassembly,** è necessario essere sospesi durante il debug. Selezionare **Debug** > **disassembly****di Windows** > o premere **ALT**+**8**.

2. Nella finestra **Disassembly,** fare clic sul margine sinistro dell'istruzione in corrispondenza dell'interruzione. È inoltre possibile selezionarlo e premere **F9**oppure fare clic con il pulsante destro del mouse e scegliere **Punto di** > **interruzione Inserisci punto di interruzione**.

## <a name="see-also"></a>Vedere anche

- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Scrivere un codice C 'NET migliore con Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Primo sguardo al debug](../debugger/debugger-feature-tour.md)
- [Risolvere i problemi relativi ai punti di interruzione nel debugger di Visual StudioTroubleshoot breakpoints in the Visual Studio debugger](../debugger/troubleshooting-breakpoints.md)
