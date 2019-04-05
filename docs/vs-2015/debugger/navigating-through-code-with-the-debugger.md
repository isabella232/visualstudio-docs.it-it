---
title: Spostarsi nel codice con il Debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a38d078356acf4e78aeeb97687126616d027351f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965588"
---
# <a name="navigating-through-code-with-the-debugger"></a>Spostarsi nel codice con il Debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Acquisire familiarità con i comandi e tasti di scelta rapida per esplorare il codice nel debugger e in questo modo sarà più veloce e semplice trovare e risolvere i problemi nell'app. Esplorare il codice nel debugger, ma è possibile [controllare lo stato dell'app](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) o altre informazioni sul relativo flusso di esecuzione.  
  
## <a name="start-debugging"></a>Avvia debug  
 Spesso, si avvia una sessione debug usando **F5** (**Debug** / **Avvia debug**). Questo comando avvia l'app con il debugger collegato.  
  
 La freccia verde viene inoltre avviato il debugger (equivale **F5**).  
  
 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Alcuni altri metodi che è possibile avviare l'app con il debugger collegato comprendono **F11** ([istruzioni nel codice](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([Esegui istruzione/routine codice](#BKMK_Step_over_Step_out)), o da usando **Esegui fino al cursore**.  Vedere le altre sezioni in questo argomento per informazioni sulle funzionalità di queste opzioni.  
  
 Quando esegue il debug, la linea gialla esempi di codice che verrà eseguita successivamente.  
  
 ![DBG&#95;Basics&#95;Break&#95;Mode](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Durante il debug, è possibile spostarsi tra i comandi, ad esempio **F5**, **F11** e usare altre funzionalità descritte in questo argomento (ad esempio, i punti di interruzione) per accedere rapidamente al codice che si desidera esaminare.  
  
 La maggior parte delle funzionalità del debugger, ad esempio visualizzando i valori delle variabili nella finestra variabili locali o la valutazione delle espressioni nella finestra Espressioni di controllo, sono disponibili solo mentre il debugger viene sospeso (chiamato anche *modalità di interruzione*). Quando il debugger viene sospesa, lo stato dell'app viene sospesa durante le funzioni, variabili e oggetti restano in memoria. In modalità di interruzione, è possibile esaminare la posizione degli elementi e gli stati per individuare le violazioni o bug. Per alcuni tipi di progetto, è anche possibile apportare modifiche all'app in modalità di interruzione.  
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> L'istruzione nel codice, di una riga  
 Per arrestare in ogni riga del codice (ogni istruzione) durante il debug, usare il **F11** tasti di scelta rapida (o **Debug** / **Esegui istruzione** nel menu).  
  
> [!TIP]
>  Quando si esegue ogni riga di codice, è possibile passare il mouse sulle variabili per visualizzare i relativi valori oppure usare il [variabili locali](../debugger/autos-and-locals-windows.md) e [Watch](../debugger/autos-and-locals-windows.md) windows per verificare i relativi valori di passaggio.  
  
 Ecco alcuni dettagli sul comportamento dei **Esegui istruzione**:  
  
- In una chiamata di funzione annidata, scegliendo **Esegui istruzione** verrà eseguita la funzione annidata più interna. Se si usa **Esegui istruzione** con una chiamata del tipo `Func1(Func2())`, il debugger eseguirà l'istruzione della funzione `Func2`.  
  
- Il debugger esegue il codice un'istruzione alla volta anziché le righe fisiche. Ad esempio una clausola `if` può essere scritta in una riga:  
  
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
  
   Quando si esegue l'istruzione in questa riga, il debugger esegue la condizione come un unico passaggio e la conseguenza come un altro (in questo esempio, la condizione è true).  
  
  Per tracciare visivamente lo stack di chiamate durante l'esecuzione di funzioni, vedere [mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Step_over_Step_out"></a> Esaminare il codice, ignorando le funzioni  
 Quando si esegue codice nel debugger, spesso si noterà che non è necessario comprendere cosa avviene in una particolare funzione (non è rilevante, o si conosce funziona, come il codice della libreria ben collaudato). Usare i comandi seguenti da ignorare tramite codice (le funzioni comunque possibile eseguirli, naturalmente, ma li ignora il debugger).  
  
|Comando di tasti|Comando di menu|Descrizione|  
|----------------------|------------------|-----------------|  
|**F10**|**Esegui istruzione/routine**|Se la riga corrente contiene una chiamata di funzione **Esegui istruzione/routine** esegue il codice quindi sospesa alla prima riga del codice dopo che la funzione chiamata viene restituita.|  
|**MAIUSC+F11**|**Esci da istruzione/routine**|**Esci da istruzione /** continua l'esecuzione di codice e sospende l'esecuzione quando la funzione corrente viene restituito (ignora il debugger tramite la funzione corrente).|  
  
> [!TIP]
>  Se è necessario trovare il punto di ingresso nell'app, iniziare con **F10** oppure **F11**. Questi comandi sono spesso utili quando si esaminare lo stato dell'app o il tentativo di ottenere maggiori informazioni sul relativo flusso di esecuzione.  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Eseguire fino a un percorso specifico o (funzione)  
 Spesso il metodo preferito di debug del codice, questi metodi sono utili quando si sa esattamente quale codice si desidera controllare o almeno si conosce in cui si desidera avviare il debug.  
  
-   **Impostare punti di interruzione nel codice**  
  
     Per impostare un punto di interruzione semplice nel codice, aprire il file di origine nell'editor di Visual Studio. Impostare il cursore sulla riga di codice in cui si desidera sospendere l'esecuzione e quindi fare doppio clic nella finestra del codice per visualizzare il menu di scelta rapida e scegliere **punto di interruzione / Inserisci punto di interruzione** (o premere **F9**). Il debugger sospende il diritto di esecuzione prima che venga eseguita la riga.  
  
     ![Impostare un punto di interruzione](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     I punti di interruzione in Visual Studio forniscono un'ampia gamma di funzionalità aggiuntive, ad esempio punti di interruzione e punti di analisi condizionali. Visualizzare [usando i punti di interruzione](../debugger/using-breakpoints.md).  
  
-   **Eseguire fino alla posizione del cursore.**  
  
     Per eseguire fino alla posizione del cursore, posizionare il cursore su una riga di codice eseguibile in una finestra di origine. Nel menu di scelta rapida dell'editor (pulsante destro del mouse nell'editor), scegliere **Esegui fino al cursore**. Si tratta, ad esempio impostando un punto di interruzione temporaneo.  
  
-   **Inserire un'interruzione nel codice manualmente**  
  
     Per inserire un'interruzione nella successiva riga disponibile di codice in un'applicazione in esecuzione, scegliere **Debug**, **Interrompi tutto** (tastiera: **Ctrl + Alt + INTERR**).  
  
     Se si interrompe l'esecuzione del codice senza file (con estensione pdb) di simboli o di origine corrispondenti, il debugger visualizza una pagina **File di origine non trovati** o **Simboli non trovati** che consente di trovare i file appropriati. Vedere [Specificare file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Se non è possibile accedere ai file di supporto, è comunque possibile eseguire il debug delle istruzioni di assembly nella finestra Disassembly.  
  
-   **Eseguire fino a una funzione nello stack di chiamate**  
  
     Nel **Stack di chiamate** , disponibile durante il debug, finestra selezionare la funzione, pulsante destro del mouse e scegliere **Esegui fino al cursore**. Per tracciare visivamente lo stack di chiamate, vedere [mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
-   **Eseguire fino a una funzione specificata mediante il nome**  
  
     È possibile impostare il debugger per eseguire l'applicazione fino a quando non raggiunge una funzione specificata. È possibile specificare la funzione mediante il nome oppure sceglierla dallo stack di chiamate.  
  
     Per specificare una funzione mediante il nome, scegliere **Debug**, **Nuovo punto di interruzione**, **Interrompi alla funzione**, quindi immettere il nome della funzione e altre informazioni di identificazione.  
  
     ![Finestra di dialogo Nuovo punto di interruzione](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Se la funzione è sottoposta a overload o è disponibile nello spazio dei nomi, è possibile scegliere le funzioni desiderate nella finestra di dialogo **Seleziona punti di interruzione** .  
  
     ![I punti di interruzione, finestra di dialogo Scegli](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Spostare il puntatore del mouse per modificare il flusso di esecuzione  
 Mentre il debugger è in pausa, è possibile spostare il puntatore all'istruzione per impostare la successiva istruzione di codice da eseguire. La posizione dell'istruzione successiva da eseguire è contrassegnata da una freccia gialla visualizzata sul margine di una finestra di origine o di una finestra Disassembly. Mediante lo spostamento della freccia, è possibile ignorare un segmento di codice oppure tornare a una riga eseguita precedentemente. È possibile usare questa opzione in alcune situazioni, ad esempio quando si desidera ignorare una sezione di codice che contiene un bug noto.  
  
 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Per impostare l'istruzione successiva da eseguire, utilizzare una di queste procedure:  
  
-   In una finestra di origine trascinare la freccia gialla nella posizione in cui si desidera impostare l'istruzione successiva all'interno dello stesso file di origine.  
  
-   In una finestra di origine, impostare il cursore sulla riga che si desidera eseguire successivamente, pulsante destro del mouse e scegliere **Imposta istruzione successiva**.  
  
-   Nella finestra Disassembly impostare il cursore sull'istruzione dell'assembly che si desidera eseguire successivamente, fare doppio clic su un e scegliere **Imposta istruzione successiva**.  
  
> [!CAUTION]
>  Quando si imposta l'istruzione successiva, il contatore del programma passa direttamente alla nuova posizione. Usare questo comando con cautela:  
> 
> - Le istruzioni comprese tra il vecchio e il nuovo punto di esecuzione non verranno eseguite.  
>   -   Se si sposta all'indietro il punto di esecuzione, le istruzioni comprese tra questo e il vecchio punto di interruzione non verranno annullate.  
>   -   Lo spostamento dell'istruzione successiva in corrispondenza di un'altra funzione o ambito provoca in genere un errore dello stack di chiamate e, conseguentemente, un errore o un'eccezione di runtime. Se si sposta l'istruzione successiva in corrispondenza di un altro ambito, verrà visualizzata una finestra di dialogo contenente un avviso e in cui si può scegliere di annullare l'operazione. In Visual Basic non è possibile spostare l'istruzione successiva in corrispondenza di un altro ambito o di un'altra funzione.  
>   -   Se in C++ nativo sono abilitati i controlli runtime, l'impostazione dell'istruzione successiva può causare la generazione di un'eccezione quando l'esecuzione raggiunge la fine del metodo.  
>   -   Quando l'opzione Modifica e continuazione è abilitata, **Imposta istruzione successiva** avrà esito negativo se sono state effettuate modifiche per cui Modifica e continuazione non è immediatamente in grado di eseguire nuovamente il mapping. Ad esempio questo può accadere se è stato modificato del codice all'interno di un blocco catch. Quando succede, verrà visualizzato un messaggio di errore indicante che l'operazione non è supportata.  
> 
> [!NOTE]
>  Nel codice gestito non è possibile spostare l'istruzione successiva in presenza delle seguenti condizioni:  
> 
> - L'istruzione successiva è inclusa in un metodo diverso da quello dell'istruzione corrente.  
>   -   Il debug è stato avviato utilizzando il debug JIT.  
>   -   È in corso la rimozione di uno stack di chiamate.  
>   -   È stata generata un'eccezione System.StackOverflowException or System.Threading.ThreadAbortException.  
  
 Non è possibile impostare l'istruzione successiva mentre l'applicazione è in esecuzione. Per impostare l'istruzione successiva, è necessario che il debugger sia in modalità di interruzione.  
  
## <a name="step-into-non-user-code"></a>L'istruzione nel codice non utente  
 Per impostazione predefinita, il debugger tenta di mostrare è solo il codice dell'app durante il debug, che viene determinato da un debugger denominata *Just My Code*. (Vedere [Just My Code](../debugger/just-my-code.md) per verificare il funzionamento per diversi tipi di progetto e i linguaggi e come è possibile personalizzare il comportamento.) Tuttavia, a volte durante il debug, si potrebbe voler esaminare il codice di framework, il codice della libreria di terze parti o le chiamate al sistema operativo (chiamate di sistema).  
  
 È possibile disattivare Just My Code visitando **strumenti** / **opzioni** / **debug** e deselezionare il **Abilita Just My Code** casella di controllo.  
  
 Quando Just My Code è disabilitato, il debugger può eseguire istruzioni nel codice non utente e codice non utente viene visualizzato nelle finestre del debugger.  
  
> [!NOTE]
>  Just My Code non è supportato per progetti per dispositivi.  
  
 **Eseguire le chiamate di sistema**  
  
 Se sono stati caricati simboli di debug per codice di sistema e Just My Code non è abilitato, è possibile eseguire una chiamata di sistema esattamente come qualsiasi altra chiamata.  
  
 Per accedere ai file di simboli Microsoft, vedere [utilizzare server dei simboli per trovare i file di simboli non nel computer locale](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) nel [specifica simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) argomento.  
  
 Per caricare i simboli per un componente di sistema specifico durante il debug:  
  
1.  Aprire la finestra moduli (tastiera: **Ctrl + Alt + U**).  
  
2.  Selezionare il modulo per cui si desidera caricare i simboli.  
  
     I moduli con i simboli caricati sono presenti nella colonna **Stato simboli** .  
  
3.  Scegliere **Carica simboli** dal menu di scelta rapida.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Eseguire istruzioni di proprietà e operatori nel codice gestito  
 Il debugger esegue le istruzioni/routine di proprietà e operatori nel codice gestito per impostazione predefinita. Nella maggior parte dei casi, l'esperienza di debug risulta notevolmente migliorata. Per abilitare l'esecuzione di operatori o proprietà, scegliere **Debug** / **opzioni**. Nella pagina **Debug** / **Generale** deselezionare la casella di controllo **Esegui istruzione/routine di proprietà e operatori (solo gestito)** 
