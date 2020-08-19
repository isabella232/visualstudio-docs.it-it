---
title: Esplorazione del codice con il debugger | Microsoft Docs
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
ms.openlocfilehash: f79ece781db19f2483ef1dd6cb0a81ff7cf78e06
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "88608937"
---
# <a name="navigating-through-code-with-the-debugger"></a>Spostarsi nel codice con il Debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Acquisire familiarità con i comandi e i tasti di scelta rapida per esplorare il codice nel debugger e rendere più veloce e semplice trovare e risolvere i problemi nell'app. Quando si Esplora il codice nel debugger, è possibile [controllare lo stato dell'app](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) o ottenere altre informazioni sul flusso di esecuzione.  
  
## <a name="start-debugging"></a>Consente di iniziare il debug  
 Spesso si avvia una sessione di debug usando **F5** (**debug**  /  **Avvia debug**). Questo comando avvia l'app con il debugger collegato.  
  
 La freccia verde avvia anche il debugger (uguale a **F5**).  
  
 ![&#95;di base di DBG&#95;avviare il debug&#95;](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Alcuni altri modi in cui è possibile avviare l'app con il debugger collegato includono **F11** (Esegui[istruzione del codice](#BKMK_Step_into__over__or_out_of_the_code)),  **F10** (Esegui[istruzione/](#BKMK_Step_over_Step_out)routine del codice) o usando **Esegui fino al cursore**.  Per informazioni sulle opzioni disponibili in questo argomento, vedere le altre sezioni di questo argomento.  
  
 Quando si esegue il debug, la riga gialla indica il codice che verrà eseguito successivamente.  
  
 ![&#95;di base di DBG&#95;interrompere la modalità&#95;](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Durante il debug, è possibile passare da un comando all'altro, ad esempio **F5**, **F11** , e usare altre funzionalità descritte in questo argomento, ad esempio i punti di interruzione, per accedere rapidamente al codice che si vuole esaminare.  
  
 La maggior parte delle funzionalità del debugger, ad esempio la visualizzazione dei valori delle variabili nella finestra variabili locali o la valutazione delle espressioni nella finestra Espressioni di controllo, sono disponibili solo quando il debugger è sospeso (chiamato anche *modalità di interruzione*). Quando il debugger viene sospeso, lo stato dell'app viene sospeso mentre le funzioni, le variabili e gli oggetti rimangono in memoria. In modalità di interruzioni è possibile esaminare le posizioni e gli Stati degli elementi per cercare violazioni o bug. Per alcuni tipi di progetto, è anche possibile apportare modifiche all'app in modalità di interruzioni.  
  
## <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> Esegui istruzione codice, riga per riga  
 Per arrestare ogni riga di codice (ogni istruzione) durante il debug, utilizzare il tasto di scelta rapida **F11** (oppure Esegui istruzione di **debug**  /  **nel** menu).  
  
> [!TIP]
> Quando si esegue ogni riga di codice, è possibile passare il mouse sulle variabili per visualizzarne i valori o usare le finestre variabili [locali](../debugger/autos-and-locals-windows.md) e [espressioni di controllo](../debugger/autos-and-locals-windows.md) per controllare la modifica dei valori.  
  
 Di seguito sono riportati alcuni dettagli sul comportamento di **Esegui istruzione**:  
  
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
  
  Per tracciare visivamente lo stack di chiamate durante l'esecuzione delle funzioni, vedere [eseguire il mapping dei metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="step-through-code-skipping-functions"></a><a name="BKMK_Step_over_Step_out"></a> Eseguire il codice istruzione per istruzione, ignorando le funzioni  
 Quando si esegue il codice nel debugger, spesso si noterà che non è necessario vedere cosa accade in una funzione specifica (non è rilevante o si sa che funziona, come il codice di libreria ben testato). Usare questi comandi per ignorare il codice (le funzioni ancora vengono eseguite, ovviamente, ma il debugger ne ignora).  
  
|Comando da tastiera|Comando di menu|Descrizione|  
|----------------------|------------------|-----------------|  
|**F10**|**Esegui istruzione/routine**|Se la riga corrente contiene una chiamata di funzione, Esegui **istruzione/** routine esegue il codice, quindi sospende l'esecuzione in corrispondenza della prima riga di codice dopo la restituzione della funzione chiamata.|  
|**MAIUSC + F11**|**Esci da istruzione/routine**|**Esci da istruzione/uscita** continua a eseguire il codice e sospende l'esecuzione quando la funzione corrente restituisce (il debugger ignora la funzione corrente).|  
  
> [!TIP]
> Se è necessario trovare il punto di ingresso nell'app, iniziare con **F10** o **F11**. Questi comandi sono spesso utili quando si controlla lo stato dell'app o si tenta di trovare altre informazioni sul flusso di esecuzione.  
  
## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Eseguire fino a una posizione o una funzione specifica  
 Spesso il metodo preferito per il debug del codice, questi metodi sono utili quando si conosce esattamente quale codice si vuole ispezionare o almeno si conosce la posizione in cui si vuole avviare il debug.  
  
- **Impostare punti di interruzione nel codice**  
  
     Per impostare un punto di interruzione semplice nel codice, aprire il file di origine nell'editor di Visual Studio. Impostare il cursore sulla riga di codice in cui si vuole sospendere l'esecuzione, quindi fare clic con il pulsante destro del mouse nella finestra del codice per visualizzare il menu di scelta rapida e scegliere punto di interruzione **/Inserisci** punto di interruzione (o premere **F9**). Il debugger sospende l'esecuzione immediatamente prima dell'esecuzione della riga.  
  
     ![Imposta un punto di interruzione](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     I punti di interruzione in Visual Studio forniscono un'ampia gamma di funzionalità aggiuntive, ad esempio punti di interruzione e punti di analisi condizionali. Vedere [utilizzo](../debugger/using-breakpoints.md)di punti di interruzione.  
  
- **Eseguire fino alla posizione del cursore.**  
  
     Per eseguire fino alla posizione del cursore, posizionare il cursore su una riga di codice eseguibile in una finestra di origine. Nel menu di scelta rapida dell'editor, fare clic con il pulsante destro del mouse nell'editor, scegliere **Esegui fino al cursore**. È come impostare un punto di interruzione temporaneo.  
  
- **Inserire un'interruzione nel codice manualmente**  
  
     Per inserire un'interruzione nella successiva riga di codice disponibile in un'applicazione in esecuzione, scegliere **Debug**, **Interrompi tutto** (tastiera: **Ctrl+Alt+Break**).  
  
     Se si interrompe l'esecuzione del codice senza file (con estensione pdb) di simboli o di origine corrispondenti, il debugger visualizza una pagina **File di origine non trovati** o **Simboli non trovati** che consente di trovare i file appropriati. Vedere [specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Se non è possibile accedere ai file di supporto, è comunque possibile eseguire il debug delle istruzioni di assembly nella finestra Disassembly.  
  
- **Eseguire fino a una funzione nello stack di chiamate**  
  
     Nella finestra **stack di chiamate** (disponibile durante il debug) selezionare la funzione, fare clic con il pulsante destro del mouse e scegliere **Esegui fino al cursore**. Per tracciare visivamente lo stack di chiamate, vedere [eseguire il mapping dei metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
- **Eseguire fino a una funzione specificata mediante il nome**  
  
     È possibile indicare al debugger di eseguire l'applicazione fino a quando non raggiunge una funzione specificata. È possibile specificare la funzione mediante il nome oppure sceglierla dallo stack di chiamate.  
  
     Per specificare una funzione mediante il nome, scegliere **Debug**, **Nuovo punto di interruzione**, **Interrompi alla funzione**, quindi immettere il nome della funzione e altre informazioni di identificazione.  
  
     ![Finestra di dialogo Nuovo punto di interruzione](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Se la funzione è sottoposta a overload o è disponibile nello spazio dei nomi, è possibile scegliere le funzioni desiderate nella finestra di dialogo **Seleziona punti di interruzione** .  
  
     ![Finestra di dialogo Scegli punti di interruzione](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> Spostare il puntatore per modificare il flusso di esecuzione  
 Quando il debugger è in pausa, è possibile spostare il puntatore all'istruzione per impostare l'istruzione successiva del codice da eseguire. La posizione dell'istruzione successiva da eseguire è contrassegnata da una freccia gialla visualizzata sul margine di una finestra di origine o di una finestra Disassembly. Mediante lo spostamento della freccia, è possibile ignorare un segmento di codice oppure tornare a una riga eseguita precedentemente. È possibile usare questa opzione in alcune situazioni, ad esempio quando si desidera ignorare una sezione di codice che contiene un bug noto.  
  
 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Per impostare l'istruzione successiva da eseguire, utilizzare una di queste procedure:  
  
- In una finestra di origine trascinare la freccia gialla nella posizione in cui si desidera impostare l'istruzione successiva all'interno dello stesso file di origine.  
  
- In una finestra di origine impostare il cursore sulla riga che si desidera eseguire successivamente, fare clic con il pulsante destro del mouse e scegliere **Imposta istruzione successiva**.  
  
- Nella finestra Disassembly impostare il cursore sull'istruzione dell'assembly che si desidera eseguire successivamente, fare clic con il pulsante destro del mouse su un oggetto e scegliere **Imposta istruzione successiva**.  
  
> [!CAUTION]
> Quando si imposta l'istruzione successiva, il contatore del programma passa direttamente alla nuova posizione. Usare questo comando con cautela:  
> 
> - Le istruzioni comprese tra il vecchio e il nuovo punto di esecuzione non verranno eseguite.  
>   - Se si sposta all'indietro il punto di esecuzione, le istruzioni comprese tra questo e il vecchio punto di interruzione non verranno annullate.  
>   - Lo spostamento dell'istruzione successiva in corrispondenza di un'altra funzione o ambito provoca in genere un errore dello stack di chiamate e, conseguentemente, un errore o un'eccezione di runtime. Se si sposta l'istruzione successiva in corrispondenza di un altro ambito, verrà visualizzata una finestra di dialogo contenente un avviso e in cui si può scegliere di annullare l'operazione. In Visual Basic non è possibile spostare l'istruzione successiva in corrispondenza di un altro ambito o di un'altra funzione.  
>   - Se in C++ nativo sono abilitati i controlli runtime, l'impostazione dell'istruzione successiva può causare la generazione di un'eccezione quando l'esecuzione raggiunge la fine del metodo.  
>   - Quando l'opzione Modifica e continuazione è abilitata, **Imposta istruzione successiva** avrà esito negativo se sono state effettuate modifiche per cui Modifica e continuazione non è immediatamente in grado di eseguire nuovamente il mapping. Ad esempio questo può accadere se è stato modificato del codice all'interno di un blocco catch. Quando succede, verrà visualizzato un messaggio di errore indicante che l'operazione non è supportata.  
> 
> [!NOTE]
> Nel codice gestito non è possibile spostare l'istruzione successiva in presenza delle seguenti condizioni:  
> 
> - L'istruzione successiva è inclusa in un metodo diverso da quello dell'istruzione corrente.  
>   - Il debug è stato avviato utilizzando il debug JIT.  
>   - È in corso la rimozione di uno stack di chiamate.  
>   - È stata generata un'eccezione System.StackOverflowException or System.Threading.ThreadAbortException.  
  
 Non è possibile impostare l'istruzione successiva mentre l'applicazione è in esecuzione. Per impostare l'istruzione successiva, è necessario che il debugger sia in modalità di interruzione.  
  
## <a name="step-into-non-user-code"></a>Esegui istruzione nel codice non utente  
 Per impostazione predefinita, il debugger tenta di visualizzare solo il codice dell'app durante il debug, determinato da un'impostazione del debugger denominata *Just My Code*. Vedere [Just My Code](../debugger/just-my-code.md) per vedere come funziona per diversi tipi di progetto e linguaggi e come è possibile personalizzare il comportamento. Tuttavia, a volte durante il debug, potrebbe essere necessario esaminare il codice del Framework, il codice della libreria di terze parti o le chiamate al sistema operativo (chiamate di sistema).  
  
 È possibile disattivare Just My Code passando a **strumenti**  /  **Opzioni**  /  **debug** e deselezionare la casella di controllo **Abilita Just My Code** .  
  
 Quando Just My Code è disabilitato, il debugger può eseguire un'istruzione nel codice non utente e il codice non utente viene visualizzato nelle finestre del debugger.  
  
> [!NOTE]
> Just My Code non è supportato per progetti per dispositivi.  
  
 **Eseguire le chiamate di sistema**  
  
 Se sono stati caricati i simboli di debug per il codice di sistema e Just My Code non è abilitato, è possibile eseguire un'istruzione in una chiamata di sistema proprio come qualsiasi altra chiamata.  
  
 Per accedere ai file di simboli Microsoft, vedere [usare i server di simboli per trovare i file di simboli non presenti nel computer locale](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) nell'argomento specificare i file di simboli [(con estensione pdb) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) .  
  
 Per caricare i simboli per un componente di sistema specifico durante il debug:  
  
1. Aprire la finestra Moduli (tastiera: **Ctrl+Alt+U**).  
  
2. Selezionare il modulo per cui si desidera caricare i simboli.  
  
     I moduli con i simboli caricati sono presenti nella colonna **Stato simboli** .  
  
3. Scegliere **Carica simboli** dal menu di scelta rapida.  
  
## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Eseguire istruzioni di proprietà e operatori nel codice gestito  
 Il debugger esegue le istruzioni/routine di proprietà e operatori nel codice gestito per impostazione predefinita. Nella maggior parte dei casi, l'esperienza di debug risulta notevolmente migliorata. Per abilitare l'esecuzione di un'istruzione in proprietà o operatori, scegliere Opzioni di **debug**  /  **Options**. Nella pagina **debug**  /  **generale** deselezionare la casella di controllo Esegui istruzione/routine di **proprietà e operatori (solo gestito)**
