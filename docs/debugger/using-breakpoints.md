---
title: Usare i punti di interruzione nel debugger di Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.choose
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a84c87ecc3c5ca0ab1d2fe52e1ff56265c9365d
ms.sourcegitcommit: e680e8ac675f003ebcc8f8c86e27f54ff38da662
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356808"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Usare i punti di interruzione nel debugger di Visual Studio
I punti di interruzione rappresentano una delle tecniche di debug più importanti nella casella degli strumenti dello sviluppatore. Ogni volta che si vuole sospendere l'esecuzione del debugger, impostare punti di interruzione. Ad esempio, si desidera visualizzare lo stato delle variabili di codice o esaminare lo stack di chiamate in un determinato punto di interruzione.  
  
##  <a name="BKMK_Overview"></a> Impostare punti di interruzione nel codice sorgente  
 È possibile impostare un punto di interruzione in qualsiasi riga di codice eseguibile. Nel seguente codice c#, ad esempio, è possibile impostare un punto di interruzione nella dichiarazione di variabile, il `for` ciclo o in qualsiasi codice all'interno di `for` ciclo. È possibile impostare un punto di interruzione, le dichiarazioni dello spazio dei nomi o una classe o nella firma del metodo.  

 Per impostare un punto di interruzione nel codice sorgente, fare clic nel margine di estrema sinistra accanto a una riga di codice. È anche possibile selezionare la riga e premere **F9**, selezionare **Debug** > **Attiva/Disattiva punto di interruzione**, o fare doppio clic e selezionare **puntodiinterruzione**  >  **Inserisci punto di interruzione**. Il punto di interruzione viene visualizzato come un punto rosso nel margine sinistro.  
  
 ![Impostare un punto di interruzione](../debugger/media/basicbreakpoint.png "base punto di interruzione")  
  
 Quando esegue il debug, esecuzione viene sospesa nel punto di interruzione, prima che venga eseguito il codice per tale riga. Il simbolo di punto di interruzione Visualizza una freccia gialla. 

 Nel punto di interruzione nell'esempio seguente, il valore di `testInt` è ancora 1.  
  
 ![Esecuzione punto di interruzione arrestata](../debugger/media/breakpointexecution.png "esecuzione punto di interruzione")  
  
 Quando il debugger si arresta nel punto di interruzione, è possibile esaminare lo stato corrente dell'app, inclusi i valori delle variabili e lo stack di chiamate. Per altre informazioni sullo stack di chiamate, vedere [procedura: utilizzare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).  

- Il punto di interruzione è un elemento toggle. È possibile selezionarlo, premere **F9**, oppure utilizzare **Debug** > **Attiva/Disattiva punto di interruzione** eliminare o reinserirla.
  
- Per disabilitare un punto di interruzione senza eliminarla, passare il mouse sul pulsante destro del mouse e selezionare **disabilita punto di interruzione**. Punti di interruzione disabilitati sono visualizzati come punti vuoti nel margine sinistro o il **i punti di interruzione** finestra. Per riabilitare un punto di interruzione, passare il puntatore sul pulsante destro del mouse e selezionare **Abilita punto di interruzione**. 
  
- Impostare le condizioni e azioni, aggiungere e modificare etichette o esportare un punto di interruzione facendo clic destro e selezionando il comando appropriato, o al passaggio del mouse su di esso e selezionando il **impostazioni** icona.

##  <a name="BKMK_Set_a_breakpoint_in_a_function"></a> Impostare punti di interruzione dal debugger di windows 

È anche possibile impostare i punti di interruzione dal **Stack di chiamate** e **Disassembly** finestre del debugger.  
  
### <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a> Impostare un punto di interruzione nella finestra Stack di chiamate  

 Per interrompere in corrispondenza l'istruzione o la riga restituita da una funzione chiama, è possibile impostare un punto di interruzione nella **Stack di chiamate** finestra. 
  
**Per impostare un punto di interruzione nella finestra Stack di chiamate:**

1. Per aprire la **Stack di chiamate** finestra, è necessario essere messo in pausa durante il debug. Selezionare **Debug** > **Windows** > **Stack di chiamate**, o premere **Ctrl** + **Alt**+**C**.  
   
2. Nel **Stack di chiamate** finestra, la funzione chiamante e scegliere **punto di interruzione** > **Inserisci punto di interruzione**, o premere **F9**.  
   
   Un simbolo di punto di interruzione viene visualizzato accanto al nome della chiamata di funzione nel margine sinistro dello stack di chiamate.
   
Il punto di interruzione dello stack di chiamate viene visualizzato nei **i punti di interruzione** finestra come un indirizzo, con una posizione di memoria corrispondente alla successiva istruzione eseguibile nella funzione. 

Il debugger si interrompe all'istruzione.  

Per altre informazioni sullo stack di chiamate, vedere [procedura: utilizzare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md). 

Visivamente traccia dei punti di interruzione durante l'esecuzione di codice, vedere [mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md). 
  
### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Impostare un punto di interruzione nella finestra Disassembly  
   
1. Per aprire la **Disassembly** finestra, è necessario essere messo in pausa durante il debug. Selezionare **Debug** > **Windows** > **Disassembly**, o premere **Alt** + **8**.  
   
2. Nel **Disassembly** finestra, fare clic sul margine sinistro dell'istruzione di cui si desidera interrompere l'esecuzione. È anche possibile selezionarlo e premere **F9**, o fare doppio clic e selezionare **punto di interruzione** > **Inserisci punto di interruzione**. 

##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Impostare punti di interruzione (funzione)  

  È possibile interrompere l'esecuzione quando viene chiamata una funzione. 

**Per impostare un punto di interruzione di funzione:**
  
1. Selezionare **Debug** > **nuovo punto di interruzione** > **punto di interruzione di funzione**, o premere **Alt** + **F9** > **Ctrl**+**B**. 
   
   È anche possibile selezionare **New** > **punto di interruzione di funzione** nel **i punti di interruzione** finestra.
   
1. Nel **nuovo punto di interruzione di funzione** finestra di dialogo immettere il nome della funzione nel **nome della funzione** casella. 

   Per restringere la specifica della funzione:
   
   - Usare il nome completo di funzione. 
     
     Esempio:  `Namespace1.ClassX.MethodA()`
     
   - Aggiungere i tipi di parametro di una funzione in overload. 
     
     Esempio:  `MethodA(int, string)`
     
   - Uso di '!' simbolo per specificare il modulo.
     
     Esempio: `App1.dll!MethodA`
     
   - Usare l'operatore di contesto in C++ nativo.
     
     `{function, , [module]} [+<line offset from start of method>]`
     
     Esempio: `{MethodA, , App1.dll}+2`
   
1. Nel **linguaggio** elenco a discesa, scegliere la lingua della funzione.
   
1. Scegliere **OK**.
  
### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Impostare un punto di interruzione di funzione utilizzando un indirizzo di memoria (solo C++ nativo)  
 È possibile usare l'indirizzo di un oggetto per impostare un punto di interruzione di funzione in un metodo chiamato da un'istanza specifica di una classe.  Ad esempio, dato un oggetto indirizzabile di tipo `my_class`, è possibile impostare un punto di interruzione di funzione per il `my_method` metodo che le chiamate dell'istanza. 
  
1.  Impostare un punto di interruzione in un punto dopo che viene creata un'istanza della classe.  
    
2.  Trovare l'indirizzo dell'istanza (ad esempio, `0xcccccccc`). 
    
3.  Selezionare **Debug** > **nuovo punto di interruzione** > **punto di interruzione di funzione**, o premere **Alt** + **F9** > **Ctrl**+**B**.  
    
4.  Aggiungere il codice seguente per il **nome della funzione** e selezionare **C++** language.  
    
    ```C++  
    ((my_class *) 0xcccccccc)->my_method  
    ```  

## <a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Impostare punti di interruzione dei dati (solo C++ nativo) 
 
 I punti di interruzione dei dati interrompono l'esecuzione quando un valore archiviato in delle modifiche indirizzo di memoria specificato. Se il valore viene letto ma non modificato, l'esecuzione non viene interrotta.  
  
**Per impostare un punto di interruzione dei dati:**

1.  In un progetto C++, avviare il debug e attendere finché non viene raggiunto un punto di interruzione. Nel **Debug** menu, scegliere **nuovo punto di interruzione** > **interruzione dei dati** 

    È anche possibile selezionare **New** > **interruzione dei dati** nel **i punti di interruzione** finestra.
  
2.  Nel **indirizzo** , digitare un indirizzo di memoria o un'espressione che restituisca un indirizzo di memoria. Ad esempio, digitare `&avar` per eseguire l'interruzione quando viene modificato il contenuto della variabile `avar` .  
  
3.  Nell'elenco a discesa **Conteggio byte** selezionare il numero di byte che si desidera controllare tramite il debugger. Ad esempio, se si seleziona **4**, il debugger controllerà i quattro byte a partire da `&avar` e si interromperà se viene modificato il valore di uno di questi byte.  

Punti di interruzione non funzionano nelle condizioni seguenti:  
-   Un processo che non è in corso il debug scrive nella posizione di memoria.  
-   La posizione di memoria è condivisa tra due o più processi.  
-   La posizione di memoria viene aggiornata all'interno del kernel. Ad esempio, se passata per il Windows 32-bit `ReadFile` (funzione), la memoria viene aggiornata dalla modalità kernel, in modo che il debugger non interrompe l'esecuzione dell'aggiornamento.  

>[!NOTE]
>- I punti di interruzione dei dati dipendono da indirizzi di memoria specifica. L'indirizzo di una variabile cambia da una sessione di debug a quella successiva, in modo che i punti di interruzione dei dati vengono disabilitati automaticamente alla fine di ogni sessione di debug.  
>  
>- Se si imposta un punto di interruzione dei dati su una variabile locale, il punto di interruzione resta abilitato quando la funzione termina, ma l'indirizzo di memoria non è più applicabile, in modo che il comportamento del punto di interruzione è imprevedibile. Se si imposta un punto di interruzione dei dati su una variabile locale, è consigliabile eliminare o disabilitare il punto di interruzione prima che la funzione termini.  

##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Gestire i punti di interruzione nella finestra di punti di interruzione 

 È possibile usare la **i punti di interruzione** finestra per visualizzare e gestire tutti i punti di interruzione nella soluzione. Questa posizione centralizzata è particolarmente utile in una soluzione di grandi dimensioni o per scenari di debug complessi in cui i punti di interruzione sono cruciali. 

Nel **i punti di interruzione** finestra, si può cercare, ordinare, filtrare, abilitare o disabilitare o eliminare i punti di interruzione. È anche possibile impostare le condizioni e azioni o aggiungere una nuova funzione o un punto di interruzione dei dati.
  
Per aprire la **i punti di interruzione** finestra, seleziona **Debug** > **Windows** > **i punti di interruzione**, oppure premere  **ALT**+**F9** oppure **Ctrl**+**Alt**+**B**.
  
![Finestra punti di interruzione](../debugger/media/breakpointswindow.png "finestra punti di interruzione")  
  
Per selezionare le colonne da visualizzare nella **i punti di interruzione** finestra, seleziona **Mostra colonne**. Selezionare un'intestazione di colonna per ordinare l'elenco di punti di interruzione in base alla colonna. 

###  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Etichette dei punti di interruzione  
È possibile usare le etichette per ordinare e filtrare l'elenco di punti di interruzione per il **i punti di interruzione** finestra. 

1. Per aggiungere un'etichetta a un punto di interruzione, fare clic sul punto di interruzione nel codice sorgente o il **i punti di interruzione** finestra e quindi selezionare **modificare etichette**. Aggiungere una nuova etichetta o sceglierne uno esistente e quindi selezionare **OK**.
2. Ordinare l'elenco di punti di interruzione nel **i punti di interruzione** finestra selezionando il **etichette**, **condizioni**, o altre intestazioni di colonna. È possibile selezionare le colonne da visualizzare selezionando **Mostra colonne** sulla barra degli strumenti. 
  
### <a name="export-and-import-breakpoints"></a>Esportare e importare punti di interruzione  
 Per salvare o condividere lo stato e posizione dei punti di interruzione, è possibile esportare o importarle. 

- Per esportare un singolo punto di interruzione in un file XML, fare clic sul punto di interruzione nel codice sorgente o **i punti di interruzione** finestra e selezionare **esportare** oppure **Esporta selezionata**. Selezionare un percorso di esportazione e quindi selezionare **salvare**. Il percorso predefinito è la cartella della soluzione. 
- Per esportare più punti di interruzione, nella **i punti di interruzione** finestra, selezionare le caselle accanto i punti di interruzione o immettere i criteri di ricerca nel **ricerca** campo. Selezionare il **esportare tutti i punti di interruzione corrispondenti al criterio di ricerca corrente** icona, salvare il file. 
- Per esportare tutti i punti di interruzione, deselezionare tutte le finestre e lasciare il **ricerca** campo vuoto. Selezionare il **esportare tutti i punti di interruzione corrispondenti al criterio di ricerca corrente** icona, salvare il file.  
- Per importare i punti di interruzione, nelle **i punti di interruzione** finestra, seleziona la **importare i punti di interruzione da un file** icona, passare al percorso del file XML e selezionare **Open**. 

##  <a name="breakpoint-conditions"></a>Condizioni punto di interruzione  
 È possibile controllare dove e quando un punto di interruzione viene eseguito impostando le condizioni. La condizione può essere qualsiasi espressione valida che riconosce il debugger. Per altre informazioni sulle espressioni valide, vedere [espressioni nel debugger](../debugger/expressions-in-the-debugger.md).  

**Per impostare una condizione di punto di interruzione:**

1.  Il simbolo di punto di interruzione e scegliere **condizioni**. O del mouse il simbolo di punto di interruzione, seleziona la **le impostazioni** icona e quindi selezionare **condizioni** nel **impostazioni punto di interruzione** finestra.  

    È anche possibile impostare le condizioni **i punti di interruzione** finestra facendo clic su un punto di interruzione e selezionando **impostazioni**, quindi selezionando **condizioni**. 
  
  ![Impostazioni punto di interruzione](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
1. Nell'elenco a discesa, selezionare **espressioni condizionali**, **passaggi**, o **filtro**e impostare il valore di conseguenza. 
  
1. Selezionare **chiudere** o premere **Ctrl**+**invio** per chiudere la **impostazioni punto di interruzione** finestra. E viceversa, il **i punti di interruzione** finestra, seleziona **OK** per chiudere la finestra di dialogo. 

I punti di interruzione con set di condizioni vengono visualizzati con un **+** simbolo nel codice sorgente e **i punti di interruzione** windows. 

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="conditional-expression"></a>Espressione condizionale

Quando si seleziona **espressione condizionale**, è possibile scegliere tra due condizioni: **vale** oppure **quando modificato**. Scegliere **vale** per interrompere l'esecuzione quando l'espressione viene soddisfatta, oppure **quando modificato** per interrompere l'esecuzione quando viene modificato il valore dell'espressione.  
  
 Nell'esempio seguente viene raggiunto il punto di interruzione solo quando il valore di `testInt` viene **4**:  
  
 ![Condizione punto di interruzione è true](../debugger/media/breakpointconditionistrue.png "punto di interruzione è true")  
  
 Nell'esempio seguente viene raggiunto il punto di interruzione solo quando il valore di `testInt` modifiche:  
  
 ![Punto di interruzione quando modificato](../debugger/media/breakpointwhenchanged.png "punto di interruzione quando modificato")  
  
 Se si imposta una condizione del punto di interruzione con sintassi non valida, viene visualizzato un messaggio di avviso. Se viene specificata una condizione del punto di interruzione con sintassi valida ma con semantica non valida, viene visualizzato un messaggio di avviso la prima volta che si raggiunge il punto di interruzione. In entrambi i casi, il debugger si interrompe quando raggiunge il punto di interruzione non valido. Il punto di interruzione viene ignorato solo se la condizione è valida e restituisce `false`.  
  
 >[!NOTE]
 >Il comportamento dei **quando modificato** campo è diverso per diversi linguaggi di programmazione. 
 >- Per il codice nativo, il debugger non considera la prima valutazione della condizione di una modifica, pertanto non viene raggiunto il punto di interruzione alla prima valutazione. 
 >- Per codice gestito, il debugger raggiunge il punto di interruzione alla prima valutazione dopo **quando modificato** sia selezionata.  
  
### <a name="using-object-ids-in-conditional-expressions-c-and-f-only"></a>Uso degli ID oggetto nelle espressioni condizionali (c# e F # solo)  
 Esistono situazioni quando si vuole osservare il comportamento di un oggetto specifico. Ad esempio, voler scoprire il motivo per cui un oggetto è stato inserito in una raccolta più volte. In c# e F #, è possibile creare ID oggetto per istanze specifiche dei [fanno riferimento ai tipi](/dotnet/csharp/language-reference/keywords/reference-types)e usarle nelle condizioni punto di interruzione. L'ID oggetto viene generato dai servizi di debug di Common Language Runtime (CLR) e associato all'oggetto.  

**Per creare un ID di oggetto:** 
  
1. Impostare un punto di interruzione il codice in luoghi dopo aver creato l'oggetto.  
   
2. Avviare il debug e quando si mette in pausa l'esecuzione nel punto di interruzione, selezionare **Debug** > **Windows** > **variabili locali** o **Alt** + **4** per aprire la **variabili locali** finestra.
   
   Trovare il punto di interruzione il **variabili locali** finestra, pulsante destro del mouse e selezionare **Crea ID oggetto**.  
   
   Nella finestra **$** verrà visualizzato il simbolo **Variabili locali** . Si tratta dell'ID oggetto.  
   
3. Aggiungere un nuovo punto di interruzione in corrispondenza del punto in cui che si desidera ricercare; ad esempio, quando l'oggetto deve essere aggiunto alla raccolta. Il punto di interruzione e scegliere **condizioni**.  
   
4. Usare l'ID di oggetto nel **espressione condizionale** campo. Ad esempio, se la variabile `item` è l'oggetto da aggiungere alla raccolta, seleziona **vale** e digitare **item = = $\<n >**, dove \<n > è il numero di ID oggetto .  
   
   L'esecuzione si interromperà in corrispondenza del punto in cui l'oggetto deve essere aggiunto alla raccolta.  
   
   Per eliminare l'ID di oggetto, fare doppio clic la variabile nel **variabili locali** finestra e selezionare **Elimina ID oggetto**.  

>[!NOTE]
>Gli ID oggetto creano riferimenti deboli e non impediscono all'oggetto di essere sottoposto a Garbage Collection. Sono validi solo per la sessione di debug corrente.  
  
### <a name="hit-count"></a>Numero di passaggi  
 Se si sospetta che un ciclo nel codice inizi a presentare un comportamento errato dopo alcune iterazioni, è possibile impostare un punto di interruzione per arrestare l'esecuzione dopo il numero di riscontri, anziché premere ripetutamente **F5** per raggiungere tale iterazione.  
  
 Sotto **condizioni** nel **impostazioni punto di interruzione** finestra, seleziona **passaggi**, quindi specificare il numero di iterazioni. Nell'esempio seguente, è impostato il punto di interruzione venga raggiunto con qualsiasi altra iterazione:  
  
 ![Numero di passaggi punto di interruzione](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
### <a name="filter"></a>Filtro  
È possibile limitare un punto di interruzione da attivare solo su dispositivi specificati o in thread e processi specificati.  
  
Sotto **condizioni** nel **impostazioni punto di interruzione** finestra, seleziona **filtro**, quindi immettere uno o più delle seguenti espressioni:  
  
-   MachineName = "name"  
-   ProcessId = value  
-   ProcessName = "name"  
-   ThreadId = value  
-   ThreadName = "name"  

Racchiudere i valori String tra virgolette doppie. È possibile combinare clausole usando `&` (AND), `||` (OR), `!` (NOT) e le parentesi.  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Le azioni di punto di interruzione e punti di analisi  
 Oggetto *punto di analisi* è un punto di interruzione che visualizza un messaggio per il **Output** finestra. Un punto di analisi può fungere da istruzione di analisi temporanea nel linguaggio di programmazione.  
  
**Per impostare un punto di analisi:**

1. Fare doppio clic su un punto di interruzione e scegliere **azioni**. O, nelle **impostazioni punto di interruzione** della finestra, passare il mouse sul punto di interruzione, selezionare la **impostazioni** icona e quindi selezionare **azioni**.  
   
1. Immettere un messaggio nel **registra un messaggio alla finestra di Output** campo. Il messaggio può includere stringhe di testo generico, i valori delle variabili o espressioni racchiuse tra parentesi graffe e gli identificatori di formato ([c#](../debugger/format-specifiers-in-csharp.md) e [C++](../debugger/format-specifiers-in-cpp.md)) per i valori.
   
   È anche possibile usare le seguenti parole chiave speciali nel messaggio:  
   
   - **$ADDRESS** -istruzione corrente  
   - **$CALLER** -nome della funzione chiamante  
   - **$CALLSTACK** -stack di chiamate 
   - **$FUNCTION** -nome della funzione corrente  
   - **$PID** -id processo  
   - **$PNAME** -nome del processo  
   - **$TID** -id thread  
   - **$TNAME** -nome thread  
   - **$TICK** -numero di graduazione (da Windows `GetTickCount`)  
   
1. Per stampare il messaggio per il **Output** finestra senza interruzioni, selezionare la **continua esecuzione** casella di controllo. Per stampare il messaggio e interromperà l'esecuzione al punto di analisi, deselezionare la casella di controllo. 

I punti di traccia vengono visualizzati come forma di rombo rosso nel margine sinistro del codice sorgente e **i punti di interruzione** windows. 
  
## <a name="see-also"></a>Vedere anche  
[Risolvere i punti di interruzione nel debugger di Visual Studio](../debugger/troubleshooting-breakpoints.md)  
[Spostarsi nel codice con il debugger](../debugger/navigating-through-code-with-the-debugger.md)
