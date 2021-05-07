---
title: Usare punti di interruzione nel debugger | Microsoft Docs
description: Informazioni sui punti di interruzione, una delle tecniche di debug più importanti. L'articolo illustra le azioni dei punti di interruzione, i punti di analisi, le condizioni e molto altro ancora.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0865c71d2893203ca3af925da1d76946d882c4c4
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798583"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Usare punti di interruzione nel debugger di Visual Studio

I punti di interruzione sono una delle tecniche di debug più importanti nella casella degli strumenti dello sviluppatore. I punti di interruzione vengono impostati in qualsiasi punto in cui si vuole sospendere l'esecuzione del debugger. Ad esempio, può essere necessario visualizzare lo stato delle variabili di codice o esaminare lo stack di chiamate in corrispondenza di un determinato punto di interruzione.  Se si sta tentando di risolvere un avviso o un problema durante l'uso di punti di interruzione, vedere Risolvere i punti di interruzione [nel debugger Visual Studio .](../debugger/troubleshooting-breakpoints.md)

> [!NOTE]
> Se si conosce l'attività o il problema che si sta tentando di risolvere, ma è necessario conoscere il tipo di punto di interruzione da usare, vedere Domande frequenti - Trovare la funzionalità [di debug.](../debugger/find-your-debugging-task.yml#pause-running-code)

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> Impostare punti di interruzione nel codice sorgente

È possibile impostare un punto di interruzione in qualsiasi riga di codice eseguibile. Nel codice C# seguente, ad esempio, è possibile impostare un punto di interruzione sulla riga di codice con l'assegnazione di variabile ( ), il ciclo o qualsiasi codice all'interno `int testInt = 1` `for` del `for` ciclo. Non è possibile impostare un punto di interruzione su firme di metodo, dichiarazioni per uno spazio dei nomi o una classe o dichiarazioni di variabili se non è presente alcuna assegnazione e nessun metodo get/setter.

Per impostare un punto di interruzione nel codice sorgente, fare clic sul margine all'estrema sinistra accanto a una riga di codice. È anche possibile selezionare la riga e premere **F9,** selezionare **Debug** Attiva/Disattiva punto di interruzione oppure fare clic con il pulsante destro del mouse e scegliere Punto di  >     >  **interruzione Inserisci punto di interruzione**. Il punto di interruzione viene visualizzato come un punto rosso nel margine sinistro.

Per la maggior parte dei linguaggi, tra cui C#, i punti di interruzione e le righe di esecuzione correnti vengono evidenziati automaticamente. Per il codice C++, è possibile attivare l'evidenziazione del punto di interruzione e delle righe correnti selezionando Strumenti **(o** **Debug** **)**> Opzioni debug Evidenzia l'intera riga di origine per i punti di interruzione e l'istruzione corrente  >    >   **(solo C++).**

![Impostare un punto di interruzione](../debugger/media/basicbreakpoint.png "Punto di interruzione di base")

Quando si esegue il debug, l'esecuzione viene sospesa in corrispondenza del punto di interruzione, prima che venga eseguito il codice in tale riga. Il simbolo del punto di interruzione mostra una freccia gialla.

In corrispondenza del punto di interruzione nell'esempio seguente, il valore `testInt` di è ancora 1. Il valore non è stato quindi modificato dopo l'inizializzazione della variabile (impostata su 1) perché l'istruzione in giallo non è stata ancora eseguita.

![Esecuzione punto di interruzione arrestata](../debugger/media/breakpointexecution.png "Esecuzione del punto di interruzione")

Quando il debugger si arresta in corrispondenza del punto di interruzione, è possibile esaminare lo stato corrente dell'app, inclusi i valori delle variabili [e](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) lo stack [di chiamate](../debugger/how-to-use-the-call-stack-window.md).

Di seguito sono riportate alcune istruzioni generali per l'uso dei punti di interruzione.

- Il punto di interruzione è un interruttore. È possibile fare clic su di esso, premere **F9** o usare **Debug** Attiva/Disattiva punto di interruzione  >   per eliminarlo o reinserirlo.

- Per disabilitare un punto di interruzione senza eliminarlo, passare il puntatore del mouse o fare clic con il pulsante destro del mouse su di esso e **scegliere Disabilita punto di interruzione.** I punti di interruzione disabilitati vengono visualizzati come punti vuoti nel margine sinistro o nella **finestra Punti di** interruzione. Per abilitare nuovamente un punto di interruzione, passare il puntatore del mouse o fare clic con il pulsante destro del mouse su di esso e **scegliere Abilita punto di interruzione.**

- Impostare condizioni e azioni, aggiungere e modificare etichette oppure esportare un punto di interruzione facendo clic con il pulsante destro del mouse su di esso e selezionando il comando appropriato oppure passando il puntatore del mouse su di esso e selezionando **l'icona** Impostazioni.

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Azioni e punti di analisi dei punti di interruzione

Un *punto di analisi* è un punto di interruzione che stampa un messaggio nella finestra **Output.** Un punto di analisi può fungere da istruzione di traccia temporanea nel linguaggio di programmazione e non sospende l'esecuzione del codice. Per creare un punto di analisi, impostare un'azione speciale nella finestra **Impostazioni punto di** interruzione . Per istruzioni dettagliate, vedere [Usare punti di analisi nel debugger Visual Studio](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Condizioni punto di interruzione

È possibile controllare dove e quando un punto di interruzione viene eseguito impostando le condizioni. La condizione può essere qualsiasi espressione valida riconosciuta dal debugger. Per altre informazioni sulle espressioni valide, vedere [Espressioni nel debugger](../debugger/expressions-in-the-debugger.md).

**Per impostare una condizione del punto di interruzione:**

1. Fare clic con il pulsante destro del mouse sul simbolo del punto di interruzione e scegliere **Condizioni** (o **premere ALT**  +  **F9**, **C).** In caso contrario, passare il puntatore del mouse sul **simbolo** del punto di interruzione, selezionare l'icona Impostazioni e quindi **selezionare** Condizioni nella finestra Impostazioni **punto di** interruzione.

   È anche possibile impostare le condizioni nella finestra Punti **di** interruzione facendo clic con il pulsante destro del mouse su un punto di interruzione e scegliendo **Impostazioni** e quindi **condizioni**.

   ![Impostazioni del punto di interruzione](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. Nell'elenco a discesa selezionare **Espressione condizionale,** **Conteggio risultati** **o Filtro** e impostare il valore di conseguenza.

3. Selezionare **Chiudi o** premere CTRL **INVIO** per chiudere la finestra Impostazioni +  punto **di** interruzione. In caso contrario, nella **finestra Punti di** interruzione selezionare **OK** per chiudere la finestra di dialogo.

I punti di interruzione con condizioni impostate vengono visualizzati con un simbolo nelle finestre Del codice **+** sorgente **e Punti di** interruzione.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Creare un'espressione condizionale

Quando si seleziona **Espressione condizionale**, è possibile scegliere tra due condizioni: **è true** o Quando **viene modificato**. Scegliere **È true per** interrompere quando  l'espressione viene soddisfatta o Quando viene modificata per interrompere quando il valore dell'espressione è stato modificato.

Nell'esempio seguente il punto di interruzione viene raggiunto solo quando il valore `testInt` di è **4**:

![Condizione punto di interruzione true](../debugger/media/breakpointconditionistrue.png "Il punto di interruzione è true")

Nell'esempio seguente il punto di interruzione viene raggiunto solo quando cambia il `testInt` valore di :

![Punto di interruzione quando viene modificato](../debugger/media/breakpointwhenchanged.png "Punto di interruzione quando viene modificato")

Se si imposta una condizione del punto di interruzione con sintassi non valida, viene visualizzato un messaggio di avviso. Se viene specificata una condizione del punto di interruzione con sintassi valida ma con semantica non valida, viene visualizzato un messaggio di avviso la prima volta che si raggiunge il punto di interruzione. In entrambi i casi, il debugger si interrompe quando raggiunge il punto di interruzione non valido. Il punto di interruzione viene ignorato solo se la condizione è valida e restituisce `false`.

>[!NOTE]
> Per il **campo** Quando viene modificato, il debugger non considera la prima valutazione della condizione come una modifica, quindi non viene raggiunto il punto di interruzione alla prima valutazione.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Usare gli ID oggetto nelle espressioni condizionali (solo C# e F#)

 A volte si vuole osservare il comportamento di un oggetto specifico. Ad esempio, potrebbe essere necessario scoprire perché un oggetto è stato inserito in una raccolta più di una volta. In C# e F# è possibile creare ID oggetto per istanze specifiche dei [tipi riferimento](/dotnet/csharp/language-reference/keywords/reference-types) e usarle nelle condizioni del punto di interruzione. L'ID oggetto viene generato dai servizi di debug di Common Language Runtime (CLR) e associato all'oggetto.

**Per creare un ID oggetto:**

1. Impostare un punto di interruzione nel codice dopo la creazione dell'oggetto .

2. Avviare il debug e quando l'esecuzione viene sospesa in corrispondenza del punto di interruzione, selezionare Debug variabili locali di Windows (oppure premere  >    >   **CTRL**  +  **ALT+V,**  +   **L)** per aprire la **finestra** Variabili locali.

   Trovare l'istanza specifica dell'oggetto nella **finestra Variabili** locali, fare clic con il pulsante destro del mouse su di essa e scegliere Make Object **ID (Crea ID oggetto).**

   Nella finestra Variabili locali **$** verrà visualizzato un segno più **un** numero. Si tratta dell'ID oggetto.

3. Aggiungere un nuovo punto di interruzione nel punto da analizzare. ad esempio quando l'oggetto deve essere aggiunto all'insieme. Fare clic con il pulsante destro del mouse sul punto di interruzione e scegliere **Condizioni**.

4. Usare l'ID oggetto nel **campo Espressione** condizionale. Ad esempio, se la variabile è l'oggetto da aggiungere alla raccolta, selezionare è true e digitare `item` **item == $ \<n>**, dove è il numero ID  \<n> oggetto.

   L'esecuzione si interromperà in corrispondenza del punto in cui l'oggetto deve essere aggiunto alla raccolta.

   Per eliminare l'ID oggetto, fare clic con il pulsante destro del mouse sulla variabile nella **finestra** Variabili locali e **scegliere Elimina ID oggetto**.

> [!NOTE]
> Gli ID oggetto creano riferimenti deboli e non impediscono all'oggetto di essere sottoposto a Garbage Collection. Sono validi solo per la sessione di debug corrente.

### <a name="set-a-hit-count-condition"></a>Impostare una condizione di numero di risultati

Se si sospetta che un ciclo nel codice inizi a comportarsi in modo non valido dopo un determinato numero di iterazioni, è possibile impostare un punto di interruzione per arrestare l'esecuzione dopo tale numero di riscontri, anziché dover premere ripetutamente **F5** per raggiungere tale iterazione.

In **Condizioni** nella finestra **Impostazioni punto di** interruzione selezionare Numero di **passaggi** e quindi specificare il numero di iterazioni. Nell'esempio seguente il punto di interruzione viene impostato per essere raggiunto a ogni altra iterazione:

![Numero di passaggi del punto di interruzione](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Impostare una condizione di filtro

È possibile limitare un punto di interruzione da attivare solo su dispositivi specificati o in thread e processi specificati.

In **Condizioni** nella finestra **Impostazioni punto di** interruzione selezionare **Filtro** e quindi immettere una o più delle espressioni seguenti:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Racchiudere i valori String tra virgolette doppie. È possibile combinare clausole usando `&` (AND), `||` (OR), `!` (NOT) e le parentesi.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Impostare i punti di interruzione delle funzioni

È possibile interrompere l'esecuzione quando viene chiamata una funzione. Ciò è utile, ad esempio, quando si conosce il nome della funzione ma non la relativa posizione. È utile anche se sono presenti funzioni con lo stesso nome e si vuole interrompere tutte le funzioni, ad esempio funzioni in overload o funzioni in progetti diversi.

**Per impostare un punto di interruzione della funzione:**

1. Selezionare **Debug nuovo** punto di  >    >  **interruzione Punto di** interruzione funzione oppure premere **CTRL**  +  **K**, **B**.

   È anche possibile selezionare Nuovo **punto**  >  **di interruzione della** funzione nella finestra Punti **di** interruzione .

1. Nella finestra **di dialogo Nuovo punto di interruzione** funzione immettere il nome della funzione nella casella **Nome** funzione .

   Per restringere la specifica della funzione:

   - Usare il nome completo della funzione.

     Esempio: `Namespace1.ClassX.MethodA()`

   - Aggiungere i tipi di parametro di una funzione di overload.

     Esempio: `MethodA(int, string)`

   - Usare il simbolo '!' per specificare il modulo.

     Esempio: `App1.dll!MethodA`

   - Usare l'operatore context in C++ nativo.

     `{function, , [module]} [+<line offset from start of method>]`

     Esempio: `{MethodA, , App1.dll}+2`

1. **Nell'elenco a** discesa Lingua scegliere la lingua della funzione.

1. Selezionare **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Impostare un punto di interruzione di funzione usando un indirizzo di memoria (solo C++ nativo)
 È possibile usare l'indirizzo di un oggetto per impostare un punto di interruzione di funzione in un metodo chiamato da un'istanza specifica di una classe.  Ad esempio, dato un oggetto indirizzabile di tipo , è possibile impostare un punto di interruzione della `my_class` funzione sul metodo chiamato `my_method` dall'istanza.

1. Impostare un punto di interruzione in un punto qualsiasi dopo la creazione di un'istanza della classe .

2. Trovare l'indirizzo dell'istanza di , ad esempio `0xcccccccc` .

3. Selezionare **Debug nuovo** punto di  >    >  **interruzione funzione** punto di interruzione o premere **CTRL**  +  **K**, **B**.

4. Aggiungere quanto segue alla **casella Nome funzione** e selezionare **linguaggio C++.**

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Impostare punti di interruzione dei dati (.NET Core 3.0 o versione successiva)

I punti di interruzione dei dati interrompeno l'esecuzione quando cambia la proprietà di un oggetto specifico.

**Per impostare un punto di interruzione dei dati**

1. In un progetto .NET Core avviare il debug e attendere fino a quando non viene raggiunto un punto di interruzione.

2. Nella finestra Auto **,**  **Espressioni di controllo** o Variabili locali fare clic con il pulsante destro del mouse su una proprietà e scegliere Interrompi **quando** cambia il valore nel menu di scelta rapida.

    ![Punto di interruzione dei dati gestiti](../debugger/media/managed-data-breakpoint.png "Punto di interruzione dei dati gestiti")

I punti di interruzione dei dati in .NET Core non funzionano per:

- Proprietà non espandibili nella descrizione comando, variabili locali, auto o finestra Espressioni di controllo
- Variabili statiche
- Classi con l'attributo DebuggerTypeProxy
- Campi all'interno di struct

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Impostare punti di interruzione dei dati (solo C++ nativo)

 I punti di interruzione dei dati interrompno l'esecuzione quando viene modificato un valore archiviato in corrispondenza di un indirizzo di memoria specificato. Se il valore viene letto ma non modificato, l'esecuzione non viene interrotta.

**Per impostare un punto di interruzione dei dati:**

1. In un progetto C++ avviare il debug e attendere fino a quando non viene raggiunto un punto di interruzione. Scegliere Nuovo punto **di interruzione** punto **di interruzione** dal menu  >  **Debug**.

    È anche possibile selezionare Nuovo punto di interruzione dati nella finestra Punti di interruzione oppure fare clic con il pulsante destro del mouse su un elemento nella finestra Auto , Espressione di controllo o Variabili locali e scegliere Interrompi quando il valore cambia nel menu di scelta   >   rapida.     

2. Nella casella **Indirizzo** digitare un indirizzo di memoria o un'espressione che restituirà un indirizzo di memoria. Ad esempio, digitare `&avar` per eseguire l'interruzione quando viene modificato il contenuto della variabile `avar` .

3. Nell'elenco a discesa **Conteggio byte** selezionare il numero di byte che si desidera controllare tramite il debugger. Ad esempio, se si seleziona **4**, il debugger controllerà i quattro byte a partire da `&avar` e si interromperà se viene modificato il valore di uno di questi byte.

I punti di interruzione dei dati non funzionano nelle condizioni seguenti:
- Un processo di cui non viene eseguito il debug scrive nella posizione di memoria.
- La posizione di memoria è condivisa tra due o più processi.
- La posizione di memoria viene aggiornata all'interno del kernel. Ad esempio, se la memoria viene passata alla funzione di Windows a 32 bit, la memoria verrà aggiornata dalla modalità kernel, in modo che il debugger non si interrompa durante `ReadFile` l'aggiornamento.
- Dove l'espressione di controllo è maggiore di 4 byte nell'hardware a 32 bit e di 8 byte su hardware a 64 bit. Si tratta di una limitazione dell'architettura x86.

> [!NOTE]
> - I punti di interruzione dei dati dipendono da indirizzi di memoria specifici. L'indirizzo di una variabile cambia da una sessione di debug a quella successiva, pertanto i punti di interruzione dei dati vengono disabilitati automaticamente alla fine di ogni sessione di debug.
>
> - Se si imposta un punto di interruzione dei dati in una variabile locale, il punto di interruzione resta abilitato quando la funzione termina, ma l'indirizzo di memoria non è più applicabile, pertanto il comportamento del punto di interruzione è imprevedibile. Se si imposta un punto di interruzione dei dati in una variabile locale, è necessario eliminare o disabilitare il punto di interruzione prima del termine della funzione.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Gestire i punti di interruzione nella finestra Punti di interruzione

 È possibile usare la finestra **Punti di** interruzione per visualizzare e gestire tutti i punti di interruzione nella soluzione. Questa posizione centralizzata è particolarmente utile in una soluzione di grandi dimensioni o per scenari di debug complessi in cui i punti di interruzione sono critici.

Nella finestra **Punti di interruzione** è possibile cercare, ordinare, filtrare, abilitare/disabilitare o eliminare punti di interruzione. È anche possibile impostare condizioni e azioni o aggiungere una nuova funzione o un punto di interruzione dati.

Per aprire la finestra **Punti di** interruzione, selezionare **Debug** punti di interruzione di  >  **Windows** oppure  >  premere **CTRL** +  + **ALT+B.**

![Finestra Punti di interruzione](../debugger/media/breakpointswindow.png "finestra Punti di interruzione")

Per selezionare le colonne da visualizzare nella finestra **Punti di** interruzione, selezionare **Mostra colonne**. Selezionare un'intestazione di colonna per ordinare l'elenco dei punti di interruzione in base a tale colonna.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Etichette dei punti di interruzione
È possibile usare le etichette per ordinare e filtrare l'elenco dei punti di interruzione nella **finestra Punti di** interruzione.

1. Per aggiungere un'etichetta a un punto di interruzione, fare clic con il pulsante destro del mouse sul punto di interruzione nel codice sorgente o nella finestra **Punti** di interruzione e quindi scegliere **Modifica etichette**. Aggiungere una nuova etichetta o sceglierne una esistente e quindi selezionare **OK.**
2. Ordinare l'elenco dei punti **di** interruzione nella finestra Punti di interruzione selezionando **etichette**, **Condizioni** o altre intestazioni di colonna. È possibile selezionare le colonne da visualizzare selezionando **Mostra** colonne sulla barra degli strumenti.

### <a name="export-and-import-breakpoints"></a>Esportare e importare punti di interruzione
 Per salvare o condividere lo stato e il percorso dei punti di interruzione, è possibile esportarli o importarli.

- Per esportare un singolo punto di interruzione in un file XML, fare clic con il pulsante destro del mouse sul punto di interruzione nella finestra Del codice sorgente o **Punti** di interruzione e scegliere Esporta **o** Esporta **selezionato.** Selezionare un percorso di esportazione e quindi selezionare **Salva**. Il percorso predefinito è la cartella della soluzione.
- Per esportare diversi punti  di interruzione, nella finestra Punti di interruzione selezionare le caselle accanto ai punti di interruzione o immettere i criteri di ricerca nel **campo** Cerca. Selezionare **l'icona Esporta tutti i punti di interruzione** corrispondenti ai criteri di ricerca correnti e salvare il file.
- Per esportare tutti i punti di interruzione, deselezionare tutte le caselle e lasciare vuoto **il campo** Cerca. Selezionare **l'icona Esporta tutti i punti di interruzione** corrispondenti ai criteri di ricerca correnti e salvare il file.
- Per importare punti  di interruzione, nella finestra Punti di interruzione selezionare l'icona Importa punti di interruzione da **un file,** passare al percorso del file XML e selezionare **Apri**.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a> Impostare punti di interruzione dalle finestre del debugger

È anche possibile impostare punti di interruzione dalle **finestre del** debugger Stack di chiamate **e Disassembly.**

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Impostare un punto di interruzione nella finestra Stack di chiamate

 Per interrompere l'istruzione o la riga a cui viene restituita una funzione chiamante, è possibile impostare un punto di interruzione nella **finestra Stack di** chiamate.

**Per impostare un punto di interruzione nella finestra Stack di chiamate:**

1. Per aprire la finestra **Stack di** chiamate, è necessario essere sospesi durante il debug. Selezionare **Debug**  >  **Windows**  >  **Call Stack (Esegui debug stack** di chiamate Windows) o premere **CTRL** +  + **ALT+C.**

2. Nella finestra **Stack di chiamate fare** clic con il pulsante destro del mouse sulla funzione chiamante e scegliere Punto di interruzione Inserisci punto di  >  interruzione oppure **premere F9.**

   Viene visualizzato un simbolo del punto di interruzione accanto al nome della chiamata di funzione nel margine sinistro dello stack di chiamate.

Il punto di interruzione dello stack di chiamate viene visualizzato nella finestra Punti di interruzione come indirizzo, con un percorso di memoria corrispondente all'istruzione eseguibile successiva nella funzione. 

Il debugger si interrompe in corrispondenza dell'istruzione .

Per altre informazioni sullo stack di chiamate, [vedere Procedura: Usare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

Per tracciare visivamente i punti di interruzione durante l'esecuzione del codice, vedere Eseguire il mapping dei [metodi nello stack di chiamate durante il debug.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Impostare un punto di interruzione nella finestra Disassembly

1. Per aprire la **finestra Disassembly,** è necessario essere sospesi durante il debug. Selezionare **Debug**  >  **Windows**  >  **Disassembly** o premere **CTRL** + **ALT** + **D.**

2. Nella finestra **Disassembly** fare clic sul margine sinistro dell'istruzione in corrispondenza della quale si vuole interrompere l'istruzione. È anche possibile selezionarlo e premere **F9** oppure fare clic con il pulsante destro del mouse e scegliere Punto di   >  **interruzione Inserisci punto di interruzione**.

## <a name="see-also"></a>Vedi anche

- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Scrivere codice C# migliore usando Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Prima di tutto esaminare il debug](../debugger/debugger-feature-tour.md)
- [Risolvere i problemi relativi ai punti di interruzione Visual Studio debugger](../debugger/troubleshooting-breakpoints.md)
