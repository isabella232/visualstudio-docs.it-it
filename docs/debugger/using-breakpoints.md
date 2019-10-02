---
title: Usare i punti di interruzione nel debugger | Microsoft Docs
ms.custom: seodec18
ms.date: 10/15/2018
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
ms.openlocfilehash: b40c18c4b85b39e118ac59b97649253d27324854
ms.sourcegitcommit: 8a3545329a58e446672181cfed2083f850e1ad14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71814363"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Usare i punti di interruzione nel debugger di Visual Studio
I punti di interruzione rappresentano una delle tecniche di debug più importanti nella casella degli strumenti dello sviluppatore. Per sospendere l'esecuzione del debugger, impostare i punti di interruzione. Ad esempio, è possibile visualizzare lo stato delle variabili di codice o esaminare lo stack di chiamate in un determinato punto di interruzione. Se è la prima volta che si esegue il debug del codice, può essere utile leggere [Debug per principianti](../debugger/debugging-absolute-beginners.md) prima di procedere con questo articolo.

## <a name="BKMK_Overview"></a>Imposta punti di interruzione nel codice sorgente
 È possibile impostare un punto di interruzione in qualsiasi riga di codice eseguibile. Nel codice seguente C# , ad esempio, è possibile impostare un punto di interruzione nella dichiarazione di variabile, nel ciclo `for` o in qualsiasi codice all'interno del ciclo `for`. Non è possibile impostare un punto di interruzione nello spazio dei nomi o nelle dichiarazioni di classe o nella firma del metodo.

 Per impostare un punto di interruzione nel codice sorgente, fare clic sul margine a sinistra accanto a una riga di codice. È anche possibile selezionare la riga e premere **F9**, selezionare **debug** > **Imposta/Rimuovi**punto di interruzione oppure fare clic con il pulsante destro del mouse **e selezionare punto di interruzione @no__t**-5 Inserisci punto di**interruzione**. Il punto di interruzione viene visualizzato come un punto rosso nel margine sinistro.

Nel C# codice, i punti di interruzione e le righe di esecuzione correnti vengono evidenziati automaticamente. Per C++ il codice, è possibile attivare l'evidenziazione del punto di interruzione e delle righe correnti selezionando **strumenti** (o **debug**) > **Opzioni** > **debug** >  **evidenziare intera riga di origine per i punti di interruzione e corrente istruzione (C++ solo)** .

 ![Imposta un punto di](../debugger/media/basicbreakpoint.png "interruzione di base") del punto di interruzione

 Quando si esegue il debug, l'esecuzione viene sospesa in corrispondenza del punto di interruzione, prima dell'esecuzione del codice su tale riga. Il simbolo del punto di interruzione Mostra una freccia gialla.

 Nel punto di interruzione nell'esempio seguente, il valore di `testInt` è ancora 1.

 (../debugger/media/breakpointexecution.png "Esecuzione") del punto di interruzione ![arrestata esecuzione]punto di interruzione

 Quando il debugger si arresta in corrispondenza del punto di interruzione, è possibile esaminare lo stato corrente dell'app, inclusi i valori delle variabili e lo stack di chiamate. Per ulteriori informazioni sullo stack di chiamate, vedere [How per: Utilizzare la finestra stack di chiamate @ no__t-0.

- Il punto di interruzione è un elemento di attivazione. È possibile fare clic su di esso, premere **F9**oppure usare **debug** >  per impostare il punto di**interruzione** per eliminarlo o reinserirlo.

- Per disabilitare un punto di interruzione senza eliminarlo, passare il puntatore del mouse o fare clic con il pulsante destro del mouse su di esso e scegliere **Disabilita**punto I punti di interruzione disabilitati vengono visualizzati come punti vuoti nel margine sinistro o nella finestra punti di **interruzione** . Per riabilitare un punto di interruzione, passare il puntatore del mouse o fare clic con il pulsante destro del mouse su di esso e scegliere **Abilita**punto

- Impostare le condizioni e le azioni, aggiungere e modificare etichette oppure esportare un punto di interruzione facendo clic con il pulsante destro del mouse su di esso e selezionando il comando appropriato oppure passando il puntatore del mouse e selezionando l'icona **delle impostazioni** .

## <a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>Imposta punti di interruzione dalle finestre del debugger

È anche possibile impostare punti di interruzione dalle finestre **dello stack di chiamate** e del debugger **Disassembly** .

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Impostare un punto di interruzione nella finestra stack di chiamate

 Per interrompere l'istruzione o la riga restituita da una funzione chiamante, è possibile impostare un punto di interruzione nella finestra **stack di chiamate** .

**Per impostare un punto di interruzione nella finestra stack di chiamate:**

1. Per aprire la finestra **stack di chiamate** , è necessario essere sospesi durante il debug. Selezionare **Debug** > **Windows** > **stack di chiamate**oppure premere **CTRL**+**ALT**+**C**.

2. Nella finestra **stack di chiamate** fare clic con il pulsante destro del mouse sulla funzione chiamante e selezionare punto di **interruzione** >  Inserisci punto di**interruzione**oppure premere **F9**.

   Accanto al nome della chiamata di funzione sul margine sinistro dello stack di chiamate viene visualizzato un simbolo di punto di interruzione.

Il punto di interruzione dello stack di chiamate viene visualizzato nella finestra punti di **interruzione** come indirizzo, con una posizione di memoria corrispondente alla successiva istruzione eseguibile nella funzione.

Il debugger si interrompe in corrispondenza dell'istruzione.

Per ulteriori informazioni sullo stack di chiamate, vedere [How per: Utilizzare la finestra stack di chiamate @ no__t-0.

Per tracciare visivamente i punti di interruzione durante l'esecuzione del codice, vedere [eseguire il mapping dei metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Imposta un punto di interruzione nella finestra Disassembly

1. Per aprire la finestra **Disassembly** , è necessario sospenderla durante il debug. Selezionare **Debug** > **Windows** > **Disassembly**oppure premere **ALT**+**8**.

2. Nella finestra **Disassembly** fare clic sul margine sinistro dell'istruzione che si desidera interrompere. È anche possibile selezionarlo e premere **F9**oppure fare clic con il pulsante destro del mouse e selezionare punto di **interruzione** >  Inserisci punto di**interruzione**.

## <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Imposta punti di interruzione della funzione

  È possibile interrompere l'esecuzione quando viene chiamata una funzione.

**Per impostare un punto di interruzione della funzione:**

1. Selezionare **Debug** > **nuovo**punto di interruzione  >  punto di**interruzione della funzione**oppure premere **Alt**+**F9** > **CTRL**0**B**.

   È anche possibile selezionare **nuovo**punto di**interruzione della funzione**  >  nella finestra punti di **interruzione** .

1. Nella finestra di dialogo nuovo punto di **interruzione della funzione** immettere il nome della funzione nella casella **nome funzione** .

   Per restringere la specifica della funzione:

   - Usare il nome completo della funzione.

     Esempio: `Namespace1.ClassX.MethodA()`

   - Aggiungere i tipi di parametro di una funzione in overload.

     Esempio: `MethodA(int, string)`

   - Usare il simbolo '!' per specificare il modulo.

     Esempio: `App1.dll!MethodA`

   - Usare l'operatore di contesto in C++native.

     `{function, , [module]} [+<line offset from start of method>]`

     Esempio: `{MethodA, , App1.dll}+2`

1. Nell'elenco a discesa **lingua** scegliere la lingua della funzione.

1. Scegliere **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Impostare un punto di interruzione della funzione utilizzando un indirizzo C++ di memoria (solo nativo)
 È possibile utilizzare l'indirizzo di un oggetto per impostare un punto di interruzione della funzione in un metodo chiamato da un'istanza specifica di una classe.  Ad esempio, dato un oggetto indirizzabile di tipo `my_class`, è possibile impostare un punto di interruzione della funzione nel metodo `my_method` chiamato dall'istanza.

1. Impostare un punto di interruzione in un punto successivo alla creazione di un'istanza della classe.

2. Trovare l'indirizzo dell'istanza (ad esempio, `0xcccccccc`).

3. Selezionare **Debug** > **nuovo**punto di interruzione  >  punto di**interruzione della funzione**oppure premere **Alt**+**F9** > **CTRL**0**B**.

4. Aggiungere quanto segue alla casella **nome funzione** e selezionare **C++** lingua.

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="BKMK_set_a_data_breakpoint_managed"></a>Impostare i punti di interruzione dei dati (.NET Core 3,0 o versione successiva)

I punti di interruzione dei dati interrompono l'esecuzione quando la proprietà di un oggetto specifico viene modificata.

**Per impostare un punto di interruzione dei dati**

1. In un progetto .NET Core avviare il debug e attendere che venga raggiunto un punto di interruzione.

2. Nella finestra **auto**, **espressioni di controllo**o **variabili locali** , fare clic con il pulsante destro del mouse su una proprietà e scegliere **Interrompi quando valore cambia** nel menu di scelta rapida.

    Punto di interruzione(../debugger/media/managed-data-breakpoint.png "dati gestiti") punto di ![interruzione dati gestiti]

I punti di interruzione dei dati in .NET Core non funzionano per:

- Proprietà non espandibili nella descrizione comando, variabili locali, auto o finestra Espressioni di controllo
- Variabili statiche
- Classi con l'attributo DebuggerTypeProxy
- Campi all'interno di struct

::: moniker-end

## <a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Imposta punti di interruzione dei dati C++ (solo nativo)

 I punti di interruzione dei dati interrompono l'esecuzione quando un valore archiviato in un indirizzo di memoria specificato viene modificato. Se il valore viene letto ma non modificato, l'esecuzione non viene interrotta.

**Per impostare un punto di interruzione dei dati:**

1. In un C++ progetto avviare il debug e attendere che venga raggiunto un punto di interruzione. Dal menu **debug** scegliere **nuovo**punto di interruzione  >  punto di interruzione**dei dati**

    È anche possibile selezionare **nuovo**punto di**interruzione dei dati**  >  nella finestra punti di **interruzione** oppure fare clic con il pulsante destro del mouse su un elemento nella finestra **auto**, **espressioni di controllo**o **variabili locali** e selezionare **Interrompi quando il valore cambia** nel menu di scelta rapida.

2. Nella casella **Indirizzo** digitare un indirizzo di memoria o un'espressione che restituisca un indirizzo di memoria. Ad esempio, digitare `&avar` per eseguire l'interruzione quando viene modificato il contenuto della variabile `avar` .

3. Nell'elenco a discesa **Conteggio byte** selezionare il numero di byte che si desidera controllare tramite il debugger. Ad esempio, se si seleziona **4**, il debugger controllerà i quattro byte a partire da `&avar` e si interromperà se viene modificato il valore di uno di questi byte.

I punti di interruzione dei dati non funzionano nelle condizioni seguenti:
- Un processo di cui non viene eseguito il debug scrive nella posizione di memoria.
- La posizione di memoria è condivisa tra due o più processi.
- La posizione di memoria viene aggiornata all'interno del kernel. Se, ad esempio, la memoria viene passata alla funzione Windows `ReadFile` a 32 bit, la memoria verrà aggiornata dalla modalità kernel, in modo che il debugger non si interrompa sull'aggiornamento.
- Dove l'espressione Watch è maggiore di 4 byte su hardware a 32 bit e 8 byte su hardware a 64 bit. Si tratta di una limitazione dell'architettura x86.

> [!NOTE]
> - I punti di interruzione dei dati dipendono da indirizzi di memoria specifici. L'indirizzo di una variabile cambia da una sessione di debug a quella successiva, quindi i punti di interruzione dei dati vengono disabilitati automaticamente alla fine di ogni sessione di debug.
>
> - Se si imposta un punto di interruzione dei dati in una variabile locale, il punto di interruzione resta abilitato quando la funzione termina, ma l'indirizzo di memoria non è più applicabile, pertanto il comportamento del punto di interruzione è imprevedibile. Se si imposta un punto di interruzione dei dati su una variabile locale, è necessario eliminare o disabilitare il punto di interruzione prima che la funzione termini.

## <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Gestire i punti di interruzione nella finestra Punti di interruzione

 È possibile usare la finestra punti di **interruzione** per visualizzare e gestire tutti i punti di interruzione nella soluzione. Questa posizione centralizzata è particolarmente utile in una soluzione di grandi dimensioni o in scenari di debug complessi in cui i punti di interruzione sono cruciali.

Nella finestra punti di **interruzione** è possibile cercare, ordinare, filtrare, abilitare/disabilitare o eliminare punti di interruzione. È anche possibile impostare condizioni e azioni oppure aggiungere una nuova funzione o un nuovo punto di interruzione dei dati.

Per aprire la finestra punti di **interruzione** , **selezionare debug** > **Windows** >  punti di**interruzione**oppure **premere ALT**+**F9** o **CTRL**0**ALT**2**B**.

![](../debugger/media/breakpointswindow.png "Finestra") punti di interruzione finestra punti di interruzione

Per selezionare le colonne da visualizzare nella finestra punti di **interruzione** , selezionare **Mostra colonne**. Selezionare un'intestazione di colonna per ordinare l'elenco di punti di interruzione in base a tale colonna.

### <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Etichette dei punti di interruzione
È possibile utilizzare le etichette per ordinare e filtrare l'elenco dei punti di interruzione nella finestra punti di **interruzione** .

1. Per aggiungere un'etichetta a un punto di interruzione, fare clic con il pulsante destro del mouse sul punto di interruzione nel codice sorgente o nella finestra punti di **interruzione** , quindi scegliere **modifica etichette**. Aggiungere una nuova etichetta o sceglierne una esistente e quindi fare clic su **OK**.
2. Ordinare l'elenco dei punti di interruzione nella finestra punti di **interruzione** selezionando le **etichette**, le **condizioni**o altre intestazioni di colonna. È possibile selezionare le colonne da visualizzare selezionando **Mostra colonne** sulla barra degli strumenti.

### <a name="export-and-import-breakpoints"></a>Esportare e importare punti di interruzione
 Per salvare o condividere lo stato e la posizione dei punti di interruzione, è possibile esportarli o importarli.

- Per esportare un singolo punto di interruzione in un file XML, fare clic con il pulsante destro del mouse sul punto di interruzione nella finestra codice sorgente o punti di **interruzione** e selezionare **Esporta** o **Esporta selezionato**. Selezionare un percorso di esportazione e quindi fare clic su **Salva**. Il percorso predefinito è la cartella della soluzione.
- Per esportare diversi punti di interruzione, nella finestra punti di **interruzione** selezionare le caselle accanto ai punti di interruzione oppure immettere i criteri di ricerca nel campo di **ricerca** . Selezionare l'icona Esporta tutti i punti di **interruzione corrispondenti ai criteri di ricerca correnti** e salvare il file.
- Per esportare tutti i punti di interruzione, deselezionare tutte le caselle e lasciare vuoto il campo di **ricerca** . Selezionare l'icona Esporta tutti i punti di **interruzione corrispondenti ai criteri di ricerca correnti** e salvare il file.
- Per importare i punti di interruzione, nella finestra punti di **interruzione** selezionare l'icona **Importa punti di interruzione da un file** , passare al percorso del file XML e selezionare **Apri**.

## <a name="breakpoint-conditions"></a>Condizioni punto di interruzione
 È possibile controllare dove e quando un punto di interruzione viene eseguito impostando le condizioni. La condizione può essere qualsiasi espressione valida riconosciuta dal debugger. Per altre informazioni sulle espressioni valide, vedere [Espressioni nel debugger](../debugger/expressions-in-the-debugger.md).

**Per impostare una condizione del punto di interruzione:**

1. Fare clic con il pulsante destro del mouse sul simbolo e selezionare **condizioni**. In alternativa, passare il puntatore del mouse sul simbolo del punto di interruzione, selezionare l'icona **delle impostazioni** e quindi selezionare **condizioni** nella finestra impostazioni del punto di **interruzione** .

   È anche possibile impostare le condizioni nella finestra punti di **interruzione** facendo clic con il pulsante destro del mouse su un punto di interruzione e selezionando **Impostazioni**, quindi selezionando le **condizioni**.

   ![Impostazioni punto di interruzione](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. Nell'elenco a discesa selezionare **espressione condizionale**, **numero di passaggi**o **filtro**, quindi impostare il valore di conseguenza.

3. Selezionare **Chiudi** oppure premere **CTRL**+**invio** per chiudere la finestra **delle impostazioni** del punto di interruzione. In alternativa, nella finestra punti di **interruzione** selezionare **OK** per chiudere la finestra di dialogo.

I punti di interruzione con set di condizioni vengono visualizzati con un simbolo **+** nelle finestre del codice sorgente e dei punti di **interruzione** .

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="conditional-expression"></a>Espressione condizionale

Quando si seleziona **espressione condizionale**, è possibile scegliere tra due condizioni: **È true** o **se**è stato modificato. Scegliere **è true** per interrompere il tentativo quando l'espressione viene soddisfatta o **quando viene modificata** per interrompere l'intervallo quando il valore dell'espressione viene modificato.

 Nell'esempio seguente il punto di interruzione viene raggiunto solo quando il valore di `testInt` è **4**:

 La condizione del punto di ![interruzione è true](../debugger/media/breakpointconditionistrue.png "breakpoint è true")

 Nell'esempio seguente il punto di interruzione viene raggiunto solo quando il valore di `testInt` cambia:

 Punto di interruzione ![quando]viene modificato il punto di(../debugger/media/breakpointwhenchanged.png "interruzione")

 Se si imposta una condizione del punto di interruzione con sintassi non valida, viene visualizzato un messaggio di avviso. Se viene specificata una condizione del punto di interruzione con sintassi valida ma con semantica non valida, viene visualizzato un messaggio di avviso la prima volta che si raggiunge il punto di interruzione. In entrambi i casi, il debugger si interrompe quando raggiunge il punto di interruzione non valido. Il punto di interruzione viene ignorato solo se la condizione è valida e restituisce `false`.

 >[!NOTE]
 >Il comportamento del campo **Se modificato** è diverso per i diversi linguaggi di programmazione.
 >- Per il codice nativo, il debugger non considera la prima valutazione della condizione come una modifica, quindi non raggiunge il punto di interruzione alla prima valutazione.
 >- Per il codice gestito, il debugger raggiunge il punto di interruzione alla prima valutazione dopo la selezione di **modificato** .

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="using-object-ids-in-conditional-expressions-c-and-f-only"></a>Uso degli ID oggetto nelle espressioniC# condizionali F# (e solo)
 In alcuni casi è opportuno osservare il comportamento di un oggetto specifico. Ad esempio, potrebbe essere necessario individuare il motivo per cui un oggetto è stato inserito più volte in una raccolta. In C# e F# è possibile creare ID oggetto per istanze specifiche dei [tipi riferimento](/dotnet/csharp/language-reference/keywords/reference-types) e usarle nelle condizioni del punto di interruzione. L'ID oggetto viene generato dai servizi di debug di Common Language Runtime (CLR) e associato all'oggetto.

**Per creare un ID oggetto:**

1. Impostare un punto di interruzione nel codice dopo la creazione dell'oggetto.

2. Avviare il debug e quando l'esecuzione viene sospesa in corrispondenza del punto di interruzione, selezionare **Debug** > **Windows** > **locals** o **ALT**+**4** per aprire la finestra **variabili locali** .

   Individuare l'istanza specifica dell'oggetto nella finestra **variabili locali** , fare clic con il pulsante destro del mouse su di essa e scegliere **Crea ID oggetto**.

   Nella finestra **$** verrà visualizzato il simbolo **Variabili locali** . Si tratta dell'ID oggetto.

3. Aggiungere un nuovo punto di interruzione nel punto in cui si desidera esaminare; ad esempio, quando l'oggetto deve essere aggiunto alla raccolta. Fare clic con il pulsante destro del mouse sul punto di interruzione e scegliere **Condizioni**.

4. Usare l'ID oggetto nel campo **Espressione condizionale**. Se ad esempio la variabile `item` è l'oggetto da aggiungere alla raccolta, Select **è true** e Type **Item = = $ \<N >** , dove \<N > è il numero ID dell'oggetto.

   L'esecuzione si interromperà in corrispondenza del punto in cui l'oggetto deve essere aggiunto alla raccolta.

   Per eliminare l'ID oggetto, fare clic con il pulsante destro del mouse sulla variabile nella finestra variabili **locali** e scegliere **Elimina ID oggetto**.

>[!NOTE]
>Gli ID oggetto creano riferimenti deboli e non impediscono all'oggetto di essere sottoposto a Garbage Collection. Sono validi solo per la sessione di debug corrente.

### <a name="hit-count"></a>Numero di passaggi
 Se si ritiene che un ciclo nel codice inizi a presentare un comportamento errato dopo un certo numero di iterazioni, è possibile impostare un punto di interruzione per arrestare l'esecuzione dopo tale numero di riscontri, anziché premere ripetutamente **F5** per raggiungere tale iterazione.

 In **condizioni** nella finestra **Impostazioni** del punto di interruzione selezionare numero di **passaggi**, quindi specificare il numero di iterazioni. Nell'esempio seguente il punto di interruzione viene impostato in modo da essere raggiunto ogni altra iterazione:

 ![Numero di passaggi]del punto di interruzione(../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="filter"></a>Filtro
È possibile limitare un punto di interruzione da attivare solo su dispositivi specificati o in thread e processi specificati.

In **condizioni** nella finestra **Impostazioni** del punto di interruzione selezionare **filtro**, quindi immettere una o più delle espressioni seguenti:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Racchiudere i valori String tra virgolette doppie. È possibile combinare clausole usando `&` (AND), `||` (OR), `!` (NOT) e le parentesi.

## <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Azioni dei punti di interruzione e punti di analisi
 Un *punto di analisi* è un punto di interruzione che visualizza un messaggio nella finestra **Output**. Un punto di analisi può fungere da istruzione di analisi temporanea nel linguaggio di programmazione.

**Per impostare un punto di analisi:**

1. Fare clic con il pulsante destro del mouse sul punto di interruzione e scegliere **azioni**. In alternativa, nella finestra impostazioni del punto di **interruzione** passare il puntatore del mouse sul punto di interruzione, selezionare l'icona **delle impostazioni** e quindi selezionare **azioni**.

1. Immettere un messaggio nel campo **registra un messaggio nella finestra di output** . Il messaggio può includere stringhe di testo generico, valori di variabili o espressioni racchiuse tra parentesi graffe e identificatori di formato[C#](../debugger/format-specifiers-in-csharp.md) ( [C++](../debugger/format-specifiers-in-cpp.md)e) per i valori.

   Nel messaggio è inoltre possibile utilizzare le seguenti parole chiave speciali:

   - **$Address** -istruzione corrente
   - Nome della funzione di chiamata di **$Caller**
   - Stack di chiamate **$CallStack**
   - **$Function** -nome della funzione corrente
   - ID processo **$PID**
   - Nome del processo di **$pname**
   - ID thread di **$TID**
   - Nome del thread di **$tname**
   - **$Tick** -conteggio dei cicli (da Windows `GetTickCount`)

1. Per stampare il messaggio nella finestra di **output** senza interruzioni, selezionare la casella di controllo **continua esecuzione** . Per stampare il messaggio e interrompere l'esecuzione nel punto di analisi, deselezionare la casella di controllo.

Punti vengono visualizzati come diamanti rossi nel margine sinistro delle finestre del codice sorgente e dei punti di **interruzione** .

## <a name="see-also"></a>Vedere anche

- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Scrivere codice C# migliore con Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Esaminare prima di tutto il debug](../debugger/debugger-feature-tour.md)
- [Risolvere i problemi relativi ai punti di interruzione nel debugger di Visual Studio](../debugger/troubleshooting-breakpoints.md)
