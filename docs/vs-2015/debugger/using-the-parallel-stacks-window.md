---
title: Uso della finestra stack in parallelo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e89125c8e1dea25ab02fe64c21b8166e9d65194a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542220"
---
# <a name="using-the-parallel-stacks-window"></a>Utilizzo della finestra Stack in parallelo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La finestra **stack in parallelo** è utile quando si esegue il debug di applicazioni multithread. La **visualizzazione thread** Mostra le informazioni sullo stack di chiamate per tutti i thread nell'applicazione. Consente di navigare tra i thread e gli stack frame nei thread. Nel codice gestito, la **visualizzazione attività** Mostra gli stack di chiamate degli <xref:System.Threading.Tasks.Task?displayProperty=fullName> oggetti. Nel codice nativo, la **visualizzazione attività** Mostra gli stack di chiamate [di gruppi di attività](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [algoritmi paralleli](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [agenti asincroni](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)e [attività leggere](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90).  
  
## <a name="threads-view"></a>Visualizzazione Thread  
 Nell'illustrazione seguente viene mostrato un thread passato da principale ad A, quindi a B, infine a codice esterno. Altri due thread sono partiti da codice esterno per poi passare ad A, ma uno dei thread ha proseguito fino a B, quindi a codice esterno, mentre l'altro thread ha proseguito fino a C, quindi ad AnonymousMethod.  
  
 ![Visualizzazione thread nella finestra Stack in parallelo](../debugger/media/parallel-stacksthread.png "Parallel_StacksThread")  
  
 Nell'illustrazione il percorso di chiamate del thread corrente è evidenziato in blu, mentre lo stack frame attivo è indicato dalla freccia gialla. È possibile modificare la stack frame corrente selezionando un metodo diverso nella finestra **stack in parallelo** . Ciò potrebbe comportare anche la modifica del thread corrente, a seconda che il metodo selezionato sia già parte del thread corrente o di un altro thread. Nella tabella seguente vengono descritte le principali funzionalità della finestra **stack in parallelo** , come illustrato nella figura.  
  
|Lettera di riferimento|Nome dell'elemento|Descrizione|  
|--------------------|------------------|-----------------|  
|A|Segmento o nodo dello stack di chiamate|Contiene una serie di contesti del metodo per uno o più thread. Se non vi sono righe della freccia connesse al nodo, questo rappresenta l'intero percorso di chiamate per i thread.|  
|B|Evidenziazione blu|Indica il percorso di chiamate del thread corrente.|  
|C|Righe della freccia|Connettono i nodi per costituire l'intero percorso di chiamate per i thread.|  
|D|Descrizione comandi nell'intestazione del nodo|Mostra l'ID e il nome definito dall'utente di ogni thread il cui percorso di chiamate condivide questo nodo.|  
|E|Contesto del metodo|Rappresenta uno o più stack frame nello stesso metodo.|  
|F|Descrizione comandi nel contesto del metodo|Nella visualizzazione thread vengono visualizzati tutti i thread in una tabella simile alla finestra **thread** . In visualizzazione attività vengono visualizzate tutte le attività in una tabella simile alla finestra **attività in parallelo** .|  
  
 Inoltre, la finestra stack in parallelo Mostra l'icona della **visualizzazione occhio** nel riquadro principale quando il grafico è troppo grande per essere inserito nella finestra. È possibile fare clic sull'icona per visualizzare l'intero grafico nella finestra.  
  
## <a name="method-context-icons"></a>Icone del contesto del metodo  
 Nella tabella seguente vengono descritte le icone che forniscono informazioni sugli stack frame attivi e correnti:  
  
|Icona|Descrizione|  
|-|-|
|![Freccia gialla in Stack in parallelo](../debugger/media/icon-parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Indica che il contesto del metodo contiene lo stack frame attivo del thread corrente.|  
|![Icona Thread in Stack in parallelo](../debugger/media/icon-parallelthreads.gif "Icon_ParallelThreads")|Indica che il contesto del metodo contiene lo stack frame attivo di un thread non corrente.|  
|![Freccia verde in Stack in parallelo](../debugger/media/icon-parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Indica che il contesto del metodo contiene lo stack frame corrente. Il nome del metodo appare in grassetto in tutti i nodi nei quali viene visualizzato.|  
  
## <a name="toolbar-controls"></a>Controlli della barra degli strumenti  
 Nell'illustrazione e nella tabella che seguono sono descritti i controlli disponibili nella barra degli strumenti della finestra Stack in parallelo.  
  
 ![Barra degli strumenti nella finestra Stack in parallelo](../debugger/media/parallel-stackstoolbar.png "Parallel_StacksToolbar")  
  
|Lettera di riferimento|Controllo|Descrizione|  
|--------------------|-------------|-----------------|  
|A|Casella combinata Thread/Attività|Consente di passare dalla visualizzazione degli stack di chiamate dei thread alla visualizzazione degli stack di chiamate delle attività e viceversa. Per altre informazioni, vedere Visualizzazione Attività e Visualizzazione Thread.|  
|B|Mostra solo con contrassegno|Mostra gli stack di chiamate solo per i thread contrassegnati in altre finestre di debug, ad esempio la finestra **thread GPU** e la finestra espressione di **controllo in parallelo** .|  
|C|Attiva/Disattiva visualizzazione metodo|Consente di passare dalla Visualizzazione stack alla Visualizzazione metodo e viceversa. Per ulteriori informazioni, vedere Visualizzazione metodo.|  
|D|Scorrimento automatico a stack frame corrente|Scorre automaticamente il diagramma in modo da visualizzare lo stack frame corrente. Questa funzionalità è utile quando si modifica lo stack frame corrente da altre finestre o quando si raggiunge un nuovo punto di interruzione nei diagrammi di grandi dimensioni.|  
|E|Attiva/Disattiva controllo zoom|Mostra o nasconde il controllo zoom. È anche possibile eseguire lo zoom premendo CTRL e ruotando la rotellina del mouse, indipendentemente dalla visibilità del controllo zoom oppure premendo **CTRL + MAIUSC +' +'** per eseguire lo zoom avanti e **CTRL + MAIUSC +'-'** per eseguire lo zoom indietro. Se si preme **CTRL + F8** , lo zoom si adatta allo schermo.|  
  
### <a name="context-menu-items"></a>Voci del menu di scelta rapida  
 Nell'illustrazione e nella tabella che seguono sono descritte le voci del menu di scelta rapida disponibili quando si fa clic con il pulsante destro del mouse su un contesto del metodo in Visualizzazione thread o Visualizzazione attività. Le ultime sei voci derivano direttamente dalla finestra Stack di chiamate e non introducono nuovi comportamenti.  
  
 ![Menu di scelta rapida nella finestra Stack in parallelo](../debugger/media/parallel-contmenu.png "Parallel_ContMenu")  
  
|MenuItem|Descrizione|  
|---------------|-----------------|  
|Flag|Contrassegna l'elemento selezionato.|  
|Rimuovi flag|Rimuove il flag dall'elemento selezionato.|  
|Freeze|Blocca l'elemento selezionato.|  
|Sblocca|Sblocca l'elemento selezionato.|  
|Passa ad attività (thread)|Esegue la stessa funzione della casella combinata nella barra degli strumenti, ma conserva lo stesso stack frame evidenziato.|  
|Vai a codice sorgente|Consente di passare al percorso nel codice sorgente che corrisponde allo stack frame sul quale l'utente ha fatto clic con il pulsante destro del mouse.|  
|Passa a frame|Uguale al comando di menu corrispondente nella finestra Stack di chiamate. Tuttavia, con Stack in parallelo, è possibile che più frame corrispondano a un unico contesto del metodo. La voce di menu dispone pertanto di sottomenu, ognuno dei quali rappresenta uno stack frame specifico. Se uno degli stack frame si trova nel thread corrente, verrà selezionato il menu che corrisponde a quello stack frame.|  
|Vai a disassembly|Consente di passare al percorso nella finestra Disassembly che corrisponde allo stack frame sul quale l'utente ha fatto clic con il pulsante destro del mouse.|  
|Mostra codice esterno|Mostra o nasconde il codice esterno.|  
|Visualizzazione esadecimale|Consente di passare dalla visualizzazione decimale a quella esadecimale e viceversa.|  
|Informazioni sul caricamento simboli|Consente di visualizzare la finestra di dialogo corrispondente.|  
|Impostazioni simboli|Consente di visualizzare la finestra di dialogo corrispondente.|  
  
## <a name="tasks-view"></a>Visualizzazione attività  
 Se l'applicazione usa <xref:System.Threading.Tasks.Task?displayProperty=fullName> oggetti (codice gestito) o `task_handle` oggetti (codice nativo) per esprimere il parallelismo, è possibile usare la casella combinata nella barra degli strumenti della finestra stack in parallelo per passare alla *visualizzazione attività*. La visualizzazione Attività mostra gli stack di chiamate delle attività anziché dei thread. La visualizzazione Attività presenta le seguenti differenze rispetto alla visualizzazione Thread:  
  
- Gli stack di chiamate dei thread che non eseguono attività non vengono visualizzati.  
  
- Gli stack di chiamate dei thread che eseguono attività sono visivamente tagliati nella parte superiore e nella parte inferiore per visualizzare i frame più rilevanti che riguardano le attività.  
  
- Quando più attività si trovano in un unico thread, gli stack di chiamate di tali attività vengono suddivisi in nodi separati.  
  
  Nell'illustrazione seguente vengono mostrate la visualizzazione Attività della finestra Stack in parallelo sulla destra e la corrispondente visualizzazione Thread sulla sinistra.  
  
  ![Visualizzazione attività nella finestra Stack in parallelo](../debugger/media/parallel-tasksview.png "Parallel_TasksView")  
  
  Per visualizzare l'intero stack di chiamate, è sufficiente tornare alla visualizzazione thread facendo clic con il pulsante destro del mouse su un stack frame e quindi scegliendo **Vai al thread**.  
  
  Come descritto nella tabella precedente, passando il mouse sul contesto del metodo è possibile visualizzare informazioni aggiuntive. Nell'immagine seguente sono mostrate le informazioni nella descrizione comandi per la visualizzazione Thread e la visualizzazione Attività.  
  
  ![Descrizioni comandi nella finestra Stack in parallelo](../debugger/media/parallel-stack-tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Visualizzazione metodo  
 Dalla visualizzazione Thread o Attività è possibile ruotare il grafico sul metodo corrente facendo clic sull'icona Visualizzazione metodo nella barra degli strumenti. La visualizzazione metodo mostra immediatamente tutti i metodi in tutti i thread che chiamano o sono chiamati dal metodo corrente. Nell'illustrazione seguente viene mostrata una visualizzazione Thread e viene illustrato come le stesse informazioni appaiono nella visualizzazione metodo.  
  
 ![Visualizzazione metodo nella finestra Stack in parallelo](../debugger/media/parallel-methodview.png "Parallel_MethodView")  
  
 Passando a un nuovo stack frame, quel metodo diventa il metodo corrente e nella finestra vengono visualizzati tutti i chiamanti e i chiamati per il nuovo metodo. È possibile che, in conseguenza a ciò, alcuni thread compaiano o scompaiano dalla visualizzazione, a seconda che il metodo sia visualizzato nei relativi stack di chiamate. Per tornare alla visualizzazione Stack, fare nuovamente clic sul pulsante della barra degli strumenti Visualizzazione metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Debug del codice gestito](../debugger/debugging-managed-code.md)   
 [Programmazione parallela](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Uso della finestra attività](../debugger/using-the-tasks-window.md)   
 [Procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Classe Task](../extensibility/debugger/task-class-internal-members.md)
