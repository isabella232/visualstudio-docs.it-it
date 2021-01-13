---
title: Usare i punti di interruzione nel debugger | Microsoft Docs
description: Informazioni sui punti di interruzione, una delle più importanti tecniche di debug. Questo articolo illustra le azioni del punto di interruzione, punti, le condizioni e molto altro ancora.
ms.custom: SEO-VS-2020
ms.date: 06/30/2020
ms.topic: how-to
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
ms.openlocfilehash: c8487482b1d87ba87dfc3a8b1e07be1360227a2f
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150444"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Usare i punti di interruzione nel debugger di Visual Studio

I punti di interruzione rappresentano una delle tecniche di debug più importanti nella casella degli strumenti dello sviluppatore. Per sospendere l'esecuzione del debugger, impostare i punti di interruzione. Ad esempio, è possibile visualizzare lo stato delle variabili di codice o esaminare lo stack di chiamate in un determinato punto di interruzione.  Se si sta provando a risolvere un avviso o un problema durante l'uso di punti di interruzione, vedere [risolvere i problemi relativi ai punti di interruzione nel debugger di Visual Studio](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Se si conosce l'attività o il problema che si sta tentando di risolvere, ma è necessario conoscere il tipo di punto di interruzione da usare, vedere [domande frequenti: trovare la funzionalità di debug](../debugger/find-your-debugging-task.md#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> Imposta punti di interruzione nel codice sorgente

È possibile impostare un punto di interruzione in qualsiasi riga di codice eseguibile. Nel codice C# seguente, ad esempio, è possibile impostare un punto di interruzione sulla riga di codice con l'assegnazione di variabile ( `int testInt = 1` ), il `for` ciclo o qualsiasi codice all'interno del `for` ciclo. Non è possibile impostare un punto di interruzione in firme di metodi, dichiarazioni per uno spazio dei nomi o una classe o dichiarazioni di variabili se non è presente alcuna assegnazione e nessun getter/setter.

Per impostare un punto di interruzione nel codice sorgente, fare clic sul margine a sinistra accanto a una riga di codice. È anche possibile selezionare la riga e premere **F9**, selezionare **debug**  >  **Imposta/Rimuovi** punto di interruzione oppure fare clic con il pulsante destro del mouse e scegliere punto di interruzione Inserisci punto di **interruzione**  >  . Il punto di interruzione viene visualizzato come un punto rosso nel margine sinistro.

Per la maggior parte dei linguaggi, tra cui C#, i punti di interruzione e le righe di esecuzione correnti vengono automaticamente Per il codice C++, è possibile attivare l'evidenziazione del punto di interruzione e delle righe correnti selezionando **strumenti** (o **debug**) > **Opzioni**  >  **debug**  >   **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente (solo C++)**.

![Imposta un punto di interruzione](../debugger/media/basicbreakpoint.png "Punto di interruzione di base")

Quando si esegue il debug, l'esecuzione viene sospesa in corrispondenza del punto di interruzione, prima dell'esecuzione del codice su tale riga. Il simbolo del punto di interruzione Mostra una freccia gialla.

Nel punto di interruzione nell'esempio seguente, il valore di `testInt` è ancora 1. Il valore non è stato modificato dopo l'inizializzazione della variabile (impostata sul valore 1) perché l'istruzione in giallo non è stata ancora eseguita.

![Esecuzione punto di interruzione arrestata](../debugger/media/breakpointexecution.png "Esecuzione del punto di interruzione")

Quando il debugger si arresta in corrispondenza del punto di interruzione, è possibile esaminare lo stato corrente dell'app, inclusi i [valori delle variabili](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) e lo [stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

Di seguito sono riportate alcune istruzioni generali per l'utilizzo dei punti di interruzione.

- Il punto di interruzione è un elemento di attivazione. È possibile fare clic su di esso, premere **F9** o usare l'   >  **interruttore** di debug per eliminare o reinserire il punto di interruzione.

- Per disabilitare un punto di interruzione senza eliminarlo, passare il puntatore del mouse o fare clic con il pulsante destro del mouse su di esso e scegliere **Disabilita** punto I punti di interruzione disabilitati vengono visualizzati come punti vuoti nel margine sinistro o nella finestra punti di **interruzione** . Per riabilitare un punto di interruzione, passare il puntatore del mouse o fare clic con il pulsante destro del mouse su di esso e scegliere **Abilita** punto

- Impostare le condizioni e le azioni, aggiungere e modificare etichette oppure esportare un punto di interruzione facendo clic con il pulsante destro del mouse su di esso e selezionando il comando appropriato oppure passando il puntatore del mouse e selezionando l'icona **delle impostazioni** .

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Azioni del punto di interruzione e punti

Un *punto di analisi è un* punto di interruzione che stampa un messaggio nella finestra di **output** . Un punto di analisi può fungere da istruzione di traccia temporanea nel linguaggio di programmazione e non sospende l'esecuzione del codice. Per creare un punto di analisi, impostare un'azione speciale nella finestra impostazioni del punto di **interruzione** . Per istruzioni dettagliate, vedere [usare punti nel debugger di Visual Studio](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Condizioni punto di interruzione

È possibile controllare dove e quando un punto di interruzione viene eseguito impostando le condizioni. La condizione può essere qualsiasi espressione valida riconosciuta dal debugger. Per altre informazioni sulle espressioni valide, vedere [Espressioni nel debugger](../debugger/expressions-in-the-debugger.md).

**Per impostare una condizione del punto di interruzione:**

1. Fare clic con il pulsante destro del mouse sul simbolo e selezionare **condizioni**. In alternativa, passare il puntatore del mouse sul simbolo del punto di interruzione, selezionare l'icona **delle impostazioni** e quindi selezionare **condizioni** nella finestra impostazioni del punto di **interruzione** .

   È anche possibile impostare le condizioni nella finestra punti di **interruzione** facendo clic con il pulsante destro del mouse su un punto di interruzione e selezionando **Impostazioni**, quindi selezionando le **condizioni**.

   ![Impostazioni del punto di interruzione](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. Nell'elenco a discesa selezionare **espressione condizionale**, **numero di passaggi** o **filtro**, quindi impostare il valore di conseguenza.

3. Selezionare **Chiudi** oppure premere **CTRL** + **invio** per chiudere la finestra impostazioni del punto di **interruzione** . In alternativa, nella finestra punti di **interruzione** selezionare **OK** per chiudere la finestra di dialogo.

I punti di interruzione con set di condizioni vengono visualizzati con un **+** simbolo nelle finestre del codice sorgente e dei punti di **interruzione** .

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Creare un'espressione condizionale

Quando si seleziona **espressione condizionale**, è possibile scegliere tra due condizioni: **è true** o in **caso di modifica**. Scegliere **è true** per interrompere il tentativo quando l'espressione viene soddisfatta o **quando viene modificata** per interrompere l'intervallo quando il valore dell'espressione viene modificato.

Nell'esempio seguente il punto di interruzione viene raggiunto solo quando il valore di `testInt` è **4**:

![Condizione punto di interruzione true](../debugger/media/breakpointconditionistrue.png "Il punto di interruzione è true")

Nell'esempio seguente il punto di interruzione viene raggiunto solo quando il valore di viene `testInt` modificato:

![Punto di interruzione quando viene modificato](../debugger/media/breakpointwhenchanged.png "Punto di interruzione quando viene modificato")

Se si imposta una condizione del punto di interruzione con sintassi non valida, viene visualizzato un messaggio di avviso. Se viene specificata una condizione del punto di interruzione con sintassi valida ma con semantica non valida, viene visualizzato un messaggio di avviso la prima volta che si raggiunge il punto di interruzione. In entrambi i casi, il debugger si interrompe quando raggiunge il punto di interruzione non valido. Il punto di interruzione viene ignorato solo se la condizione è valida e restituisce `false`.

>[!NOTE]
> Per il campo **When Changed** , il debugger non considera la prima valutazione della condizione come una modifica, quindi non raggiunge il punto di interruzione alla prima valutazione.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Usare gli ID oggetto nelle espressioni condizionali (solo C# e F #)

 In alcuni casi è opportuno osservare il comportamento di un oggetto specifico. Ad esempio, potrebbe essere necessario individuare il motivo per cui un oggetto è stato inserito più volte in una raccolta. In C# e F# è possibile creare ID oggetto per istanze specifiche dei [tipi riferimento](/dotnet/csharp/language-reference/keywords/reference-types) e usarle nelle condizioni del punto di interruzione. L'ID oggetto viene generato dai servizi di debug di Common Language Runtime (CLR) e associato all'oggetto.

**Per creare un ID oggetto:**

1. Impostare un punto di interruzione nel codice dopo la creazione dell'oggetto.

2. Avviare il debug e quando l'esecuzione viene sospesa in corrispondenza del punto di interruzione, selezionare **debug**  >    >  **variabili locali** di Windows o **ALT** + **4** per aprire la finestra **variabili locali** .

   Individuare l'istanza specifica dell'oggetto nella finestra **variabili locali** , fare clic con il pulsante destro del mouse su di essa e scegliere **Crea ID oggetto**.

   **$** Nella finestra **variabili locali** verrà visualizzato un segno più un numero. Si tratta dell'ID oggetto.

3. Aggiungere un nuovo punto di interruzione nel punto in cui si desidera esaminare; ad esempio, quando l'oggetto deve essere aggiunto alla raccolta. Fare clic con il pulsante destro del mouse sul punto di interruzione e scegliere **Condizioni**.

4. Usare l'ID oggetto nel campo **espressione condizionale** . Se ad esempio la variabile `item` è l'oggetto da aggiungere alla raccolta, Select **è true** e Type **Item = = $ \<n>**, dove \<n> è il numero ID dell'oggetto.

   L'esecuzione si interromperà in corrispondenza del punto in cui l'oggetto deve essere aggiunto alla raccolta.

   Per eliminare l'ID oggetto, fare clic con il pulsante destro del mouse sulla variabile nella finestra variabili **locali** e scegliere **Elimina ID oggetto**.

> [!NOTE]
> Gli ID oggetto creano riferimenti deboli e non impediscono all'oggetto di essere sottoposto a Garbage Collection. Sono validi solo per la sessione di debug corrente.

### <a name="set-a-hit-count-condition"></a>Impostare una condizione per il numero di passaggi

Se si ritiene che un ciclo nel codice inizi a presentare un comportamento errato dopo un certo numero di iterazioni, è possibile impostare un punto di interruzione per arrestare l'esecuzione dopo tale numero di riscontri, anziché premere ripetutamente **F5** per raggiungere tale iterazione.

In **condizioni** nella finestra **Impostazioni** del punto di interruzione selezionare numero di **passaggi**, quindi specificare il numero di iterazioni. Nell'esempio seguente il punto di interruzione viene impostato in modo da essere raggiunto ogni altra iterazione:

![Numero di passaggi del punto di interruzione](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Imposta una condizione di filtro

È possibile limitare un punto di interruzione da attivare solo su dispositivi specificati o in thread e processi specificati.

In **condizioni** nella finestra **Impostazioni** del punto di interruzione selezionare **filtro**, quindi immettere una o più delle espressioni seguenti:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Racchiudere i valori String tra virgolette doppie. È possibile combinare clausole usando `&` (AND), `||` (OR), `!` (NOT) e le parentesi.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Imposta punti di interruzione della funzione

È possibile interrompere l'esecuzione quando viene chiamata una funzione. Questa operazione è utile, ad esempio, quando si conosce il nome della funzione, ma non la relativa posizione. È utile anche se si dispone di funzioni con lo stesso nome e si desidera interrompere tutte le funzioni (ad esempio funzioni o funzioni in overload in progetti diversi).

**Per impostare un punto di interruzione della funzione:**

1. Selezionare **debug**  >  **nuovo** punto  >  di **interruzione funzione** punto di interruzione oppure premere **ALT** + **F9**  >  **CTRL** + **B**.

   È anche possibile selezionare **nuovo** punto  >  di **interruzione della funzione** nella finestra punti di **interruzione** .

1. Nella finestra di dialogo nuovo punto di **interruzione della funzione** immettere il nome della funzione nella casella **nome funzione** .

   Per restringere la specifica della funzione:

   - Usare il nome completo della funzione.

     Esempio: `Namespace1.ClassX.MethodA()`

   - Aggiungere i tipi di parametro di una funzione in overload.

     Esempio: `MethodA(int, string)`

   - Usare il simbolo '!' per specificare il modulo.

     Esempio: `App1.dll!MethodA`

   - Usare l'operatore di contesto in C++ nativo.

     `{function, , [module]} [+<line offset from start of method>]`

     Esempio: `{MethodA, , App1.dll}+2`

1. Nell'elenco a discesa **lingua** scegliere la lingua della funzione.

1. Selezionare **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Impostare un punto di interruzione della funzione utilizzando un indirizzo di memoria (solo C++ nativo)
 È possibile utilizzare l'indirizzo di un oggetto per impostare un punto di interruzione della funzione in un metodo chiamato da un'istanza specifica di una classe.  Dato un oggetto indirizzabile di tipo, ad esempio `my_class` , è possibile impostare un punto di interruzione di funzione sul `my_method` metodo chiamato dall'istanza.

1. Impostare un punto di interruzione in un punto successivo alla creazione di un'istanza della classe.

2. Trovare l'indirizzo dell'istanza (ad esempio, `0xcccccccc` ).

3. Selezionare **debug**  >  **nuovo** punto  >  di **interruzione funzione** punto di interruzione oppure premere **ALT** + **F9**  >  **CTRL** + **B**.

4. Aggiungere quanto segue alla casella **nome funzione** e selezionare linguaggio **C++** .

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Impostare i punti di interruzione dei dati (.NET Core 3,0 o versione successiva)

I punti di interruzione dei dati interrompono l'esecuzione quando la proprietà di un oggetto specifico viene modificata.

**Per impostare un punto di interruzione dei dati**

1. In un progetto .NET Core avviare il debug e attendere che venga raggiunto un punto di interruzione.

2. Nella finestra **auto**, **espressioni di controllo** o **variabili locali** , fare clic con il pulsante destro del mouse su una proprietà e scegliere **Interrompi quando valore cambia** nel menu di scelta rapida.

    ![Punto di interruzione dei dati gestiti](../debugger/media/managed-data-breakpoint.png "Punto di interruzione dei dati gestiti")

I punti di interruzione dei dati in .NET Core non funzionano per:

- Proprietà non espandibili nella descrizione comando, variabili locali, auto o finestra Espressioni di controllo
- Variabili statiche
- Classi con l'attributo DebuggerTypeProxy
- Campi all'interno di struct

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Imposta punti di interruzione dei dati (solo C++ nativo)

 I punti di interruzione dei dati interrompono l'esecuzione quando un valore archiviato in un indirizzo di memoria specificato viene modificato. Se il valore viene letto ma non modificato, l'esecuzione non viene interrotta.

**Per impostare un punto di interruzione dei dati:**

1. In un progetto C++ avviare il debug e attendere che venga raggiunto un punto di interruzione. Scegliere **nuovo** punto di interruzione dati punto di interruzione dal menu **debug** .  >  

    È anche possibile selezionare **nuovo**  >  punto di **interruzione dei dati** nella finestra punti di **interruzione** oppure fare clic con il pulsante destro del mouse su un elemento nella finestra **auto**, **espressioni di controllo** o **variabili locali** e selezionare **Interrompi quando il valore cambia** nel menu di scelta rapida.

2. Nella casella **Indirizzo** Digitare un indirizzo di memoria o un'espressione che restituisca un indirizzo di memoria. Ad esempio, digitare `&avar` per eseguire l'interruzione quando viene modificato il contenuto della variabile `avar` .

3. Nell'elenco a discesa **Conteggio byte** selezionare il numero di byte che si desidera controllare tramite il debugger. Ad esempio, se si seleziona **4**, il debugger controllerà i quattro byte a partire da `&avar` e si interromperà se viene modificato il valore di uno di questi byte.

I punti di interruzione dei dati non funzionano nelle condizioni seguenti:
- Un processo di cui non viene eseguito il debug scrive nella posizione di memoria.
- La posizione di memoria è condivisa tra due o più processi.
- La posizione di memoria viene aggiornata all'interno del kernel. Se, ad esempio, la memoria viene passata alla funzione di Windows a 32 bit `ReadFile` , la memoria verrà aggiornata dalla modalità kernel, in modo che il debugger non si interrompa sull'aggiornamento.
- Dove l'espressione Watch è maggiore di 4 byte su hardware a 32 bit e 8 byte su hardware a 64 bit. Si tratta di una limitazione dell'architettura x86.

> [!NOTE]
> - I punti di interruzione dei dati dipendono da indirizzi di memoria specifici. L'indirizzo di una variabile cambia da una sessione di debug a quella successiva, quindi i punti di interruzione dei dati vengono disabilitati automaticamente alla fine di ogni sessione di debug.
>
> - Se si imposta un punto di interruzione dei dati in una variabile locale, il punto di interruzione resta abilitato quando la funzione termina, ma l'indirizzo di memoria non è più applicabile, pertanto il comportamento del punto di interruzione è imprevedibile. Se si imposta un punto di interruzione dei dati su una variabile locale, è necessario eliminare o disabilitare il punto di interruzione prima che la funzione termini.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Gestire i punti di interruzione nella finestra Punti di interruzione

 È possibile usare la finestra punti di **interruzione** per visualizzare e gestire tutti i punti di interruzione nella soluzione. Questa posizione centralizzata è particolarmente utile in una soluzione di grandi dimensioni o in scenari di debug complessi in cui i punti di interruzione sono cruciali.

Nella finestra punti di **interruzione** è possibile cercare, ordinare, filtrare, abilitare/disabilitare o eliminare punti di interruzione. È anche possibile impostare condizioni e azioni oppure aggiungere una nuova funzione o un nuovo punto di interruzione dei dati.

Per aprire la finestra punti di **interruzione** , selezionare **debug** punti di  >    >  **interruzione** di Windows oppure premere **ALT** + **F9** o **CTRL** + **ALT** + **B**.

![Finestra punti di interruzione](../debugger/media/breakpointswindow.png "finestra Punti di interruzione")

Per selezionare le colonne da visualizzare nella finestra punti di **interruzione** , selezionare **Mostra colonne**. Selezionare un'intestazione di colonna per ordinare l'elenco di punti di interruzione in base a tale colonna.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Etichette dei punti di interruzione
È possibile utilizzare le etichette per ordinare e filtrare l'elenco dei punti di interruzione nella finestra punti di **interruzione** .

1. Per aggiungere un'etichetta a un punto di interruzione, fare clic con il pulsante destro del mouse sul punto di interruzione nel codice sorgente o nella finestra punti di **interruzione** , quindi scegliere **modifica etichette**. Aggiungere una nuova etichetta o sceglierne una esistente e quindi fare clic su **OK**.
2. Ordinare l'elenco dei punti di interruzione nella finestra punti di **interruzione** selezionando le **etichette**, le **condizioni** o altre intestazioni di colonna. È possibile selezionare le colonne da visualizzare selezionando **Mostra colonne** sulla barra degli strumenti.

### <a name="export-and-import-breakpoints"></a>Esportare e importare punti di interruzione
 Per salvare o condividere lo stato e la posizione dei punti di interruzione, è possibile esportarli o importarli.

- Per esportare un singolo punto di interruzione in un file XML, fare clic con il pulsante destro del mouse sul punto di interruzione nella finestra codice sorgente o punti di **interruzione** e selezionare **Esporta** o **Esporta selezionato**. Selezionare un percorso di esportazione e quindi fare clic su **Salva**. Il percorso predefinito è la cartella della soluzione.
- Per esportare diversi punti di interruzione, nella finestra punti di **interruzione** selezionare le caselle accanto ai punti di interruzione oppure immettere i criteri di ricerca nel campo di **ricerca** . Selezionare l'icona Esporta tutti i punti di **interruzione corrispondenti ai criteri di ricerca correnti** e salvare il file.
- Per esportare tutti i punti di interruzione, deselezionare tutte le caselle e lasciare vuoto il campo di **ricerca** . Selezionare l'icona Esporta tutti i punti di **interruzione corrispondenti ai criteri di ricerca correnti** e salvare il file.
- Per importare i punti di interruzione, nella finestra punti di **interruzione** selezionare l'icona **Importa punti di interruzione da un file** , passare al percorso del file XML e selezionare **Apri**.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a> Imposta punti di interruzione dalle finestre del debugger

È anche possibile impostare punti di interruzione dalle finestre **dello stack di chiamate** e del debugger **Disassembly** .

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Impostare un punto di interruzione nella finestra stack di chiamate

 Per interrompere l'istruzione o la riga restituita da una funzione chiamante, è possibile impostare un punto di interruzione nella finestra **stack di chiamate** .

**Per impostare un punto di interruzione nella finestra stack di chiamate:**

1. Per aprire la finestra **stack di chiamate** , è necessario essere sospesi durante il debug. Selezionare **debug**  >    >  **stack di chiamate** Windows oppure premere **CTRL** + **ALT** + **C**.

2. Nella finestra **stack di chiamate** fare clic con il pulsante destro del mouse sulla funzione chiamante **, scegliere punto** di  >  **interruzione Inserisci** punto di interruzione oppure premere **F9**.

   Accanto al nome della chiamata di funzione sul margine sinistro dello stack di chiamate viene visualizzato un simbolo di punto di interruzione.

Il punto di interruzione dello stack di chiamate viene visualizzato nella finestra punti di **interruzione** come indirizzo, con una posizione di memoria corrispondente alla successiva istruzione eseguibile nella funzione.

Il debugger si interrompe in corrispondenza dell'istruzione.

Per altre informazioni sullo stack di chiamate, vedere [procedura: usare la finestra stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

Per tracciare visivamente i punti di interruzione durante l'esecuzione del codice, vedere [eseguire il mapping dei metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Imposta un punto di interruzione nella finestra Disassembly

1. Per aprire la finestra **Disassembly** , è necessario sospenderla durante il debug. Selezionare **debug**  >    >  **Disassembly** Windows o premere **ALT** + **8**.

2. Nella finestra **Disassembly** fare clic sul margine sinistro dell'istruzione che si desidera interrompere. È anche possibile selezionarlo e premere **F9** oppure fare clic con il pulsante destro del mouse **e scegliere punto di interruzione**  >  **Inserisci** punto di interruzione.

## <a name="see-also"></a>Vedere anche

- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Scrivi codice C# migliore con Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Esaminare prima di tutto il debug](../debugger/debugger-feature-tour.md)
- [Risolvere i problemi relativi ai punti di interruzione nel debugger di Visual Studio](../debugger/troubleshooting-breakpoints.md)
