---
title: Uso della finestra Attività | Microsoft Docs
description: Le attività sono operazioni asincrone che possono essere eseguite contemporaneamente. È possibile eseguire più attività nello stesso thread. Usare Attività per visualizzare le informazioni sull'attività e sull'oggetto WinJS.Promise.
ms.custom: SEO-VS-2020
ms.date: 03/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: cfbb3faef7fa097114f66eafe8ea224c04d431b5019516f67e03bfa3947ad5c0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419260"
---
# <a name="using-the-tasks-window-c-visual-basic-c"></a>Uso della finestra Attività (C#, Visual Basic, C++)

La finestra **Attività** è simile alla finestra **Thread**, l'unica differenza è che mostra informazioni sugli oggetti <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](/cpp/parallel/concrt/reference/task-group-class) o [WinJS.Promise](/previous-versions/windows/apps/br211867(v=win.10)) e non su ogni thread. Analogamente ai thread, le attività rappresentano operazioni asincrone eseguibili simultaneamente; tuttavia, più attività possono essere eseguite nello stesso thread.

Nel codice gestito è possibile usare la finestra **Attività** quando si utilizzano gli oggetti <xref:System.Threading.Tasks.Task?displayProperty=fullName> o con le parole chiave **await** e **async** (**Await** e **Async** in Visual Basic). Per altre informazioni sulle attività nel codice gestito, vedere [Programmazione parallela.](/dotnet/standard/parallel-programming/index)

Nel codice nativo, è possibile usare la finestra **Attività** quando si utilizzano [gruppi di attività](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algoritmi paralleli](/cpp/parallel/concrt/parallel-algorithms), [agenti asincroni](/cpp/parallel/concrt/asynchronous-agents) e [attività leggere](/cpp/parallel/concrt/task-scheduler-concurrency-runtime). Per altre informazioni sulle attività nel codice nativo, vedere [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime).

In JavaScript è possibile usare la finestra Attività quando si usa il codice `.then` promise. Per altre informazioni, vedere Programmazione asincrona [in JavaScript (app UWP).](/previous-versions/windows/apps/hh700330(v=win.10))

La finestra **Attività** può essere usata ogni volta che ci si interrompe l'esecuzione nel debugger. È possibile accedere a esso nel menu **Debug** scegliendo **Finestre** e facendo clic su **Attività**. Nell'illustrazione seguente viene mostrata la finestra **Attività** nella modalità predefinita.

![Finestra Attività](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> Nel codice gestito un oggetto con stato <xref:System.Threading.Tasks.Task> [TaskStatus.Created](<xref:System.Threading.Tasks.TaskStatus.Created>), [TaskStatus.WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>)o [TaskStatus.WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>) potrebbe non essere visualizzato nella finestra Attività quando i thread gestiti sono in stato di sospensione o join. 

## <a name="tasks-column-information"></a>Informazioni nelle colonne della finestra Attività

Nelle colonne della finestra **Attività** vengono visualizzate le informazioni seguenti.

|Nome colonna|Descrizione|
|-----------------|-----------------|
|**Flag**|Mostra quali attività sono contrassegnate e consente di impostare o rimuovere un flag per un'attività.|
|**Icone**|Una freccia gialla indica l'attività corrente. L'attività corrente è l'attività in primo piano nel thread corrente.<br /><br /> Una freccia bianca indica l'attività di interruzione, vale a dire l'attività corrente al momento della chiamata del debugger.<br /><br /> L'icona di sospensione indica un'attività bloccata dall'utente. È possibile bloccare e sbloccare un'attività facendovi clic sopra con il pulsante destro del mouse nell'elenco.|
|**ID**|Numero fornito dal sistema per l'attività. Nel codice nativo, è l'indirizzo dell'attività.|
|**Status**|Stato corrente (pianificato, attivo, bloccato, deadlock, in attesa o completato) dell'attività. Un'attività pianificata è un'attività che non è stata ancora eseguita, pertanto non dispone ancora di uno stack di chiamate, un thread assegnato o informazioni correlate.<br /><br /> Un'attività attiva è un'attività che stava eseguendo codice prima dell'accesso al debugger.<br /><br /> Un'attività in attesa o bloccata è un'attività bloccata perché è in attesa della segnalazione di un evento, del rilascio di un blocco o del completamento di un'altra attività.<br /><br /> Un'attività in deadlock è un'attività in attesa il cui thread è in deadlock con un altro thread.<br /><br /> Passare il mouse **sulla cella Stato** per un'attività in deadlock o in attesa per visualizzare altre informazioni sul blocco. **Avviso:**  La **finestra Attività** segnala un deadlock solo per un'attività bloccata che usa una primitiva di sincronizzazione supportata da Wait Chain Traversal (WCT). Ad esempio, per un oggetto con deadlock, che <xref:System.Threading.Tasks.Task> usa WCT, il debugger segnala **Awaiting-deadlocked**. Per un'attività in deadlock gestita dal runtime di concorrenza, che non utilizza WCT, viene visualizzato il messaggio **In attesa**. Per altre informazioni su WCT, vedere [Wait Chain Traversal](/windows/desktop/Debug/wait-chain-traversal).|
|**Start Time**|Ora in cui l'attività è diventata attiva.|
|**Duration**|Numero di secondi durante i quali l'attività è rimasta attiva.|
|**Tempo di completamento**|Data e ora in cui è stata completata l'esecuzione dell'attività.|
|**Posizione**|Percorso corrente nello stack di chiamate dell'attività. Passare il mouse su questa cella per visualizzare l'intero stack di chiamate dell'attività. Le attività pianificate non presentano alcun valore in questa colonna.|
|**Attività**|Metodo iniziale ed eventuali argomenti passati all'attività quando è stata creata.|
|**AsyncState**|Per il codice gestito, lo stato dell'attività. Per impostazione predefinita, questa colonna è nascosta. Per visualizzarla, aprire il menu di scelta rapida per una delle intestazioni di colonna. Scegliere **Colonne**, **AsyncState**.|
|**Parent**|ID dell'attività che ha creato questa attività. Se la cella è vuota significa che l'attività non dispone di un'attività padre. Questo dato è applicabile ai soli programmi gestiti.|
|**Assegnazione thread**|ID e nome del thread nel quale viene eseguita l'attività.|
|**Appdomain**|Dominio applicazione nel quale viene eseguita l'attività, in caso di codice gestito.|
|**task_group**|Indirizzo dell'oggetto [task_group](/cpp/parallel/concrt/reference/task-group-class) che ha pianificato l'attività, in caso di codice nativo. Per gli agenti asincroni e le attività leggere, questa colonna viene impostata su 0.|
|**Processo**|ID del processo in cui viene eseguita l'attività.|

 Per aggiungere colonne alla visualizzazione, fare clic con il pulsante destro del mouse su un'intestazione di colonna e selezionare le colonne desiderate. Rimuovere le colonne deselezionando le selezioni. È anche possibile riordinare le colonne trascinandole verso sinistra o verso destra. Nell'illustrazione seguente viene mostrato il menu di scelta rapida delle colonne.

 ![Menu di scelta rapida nella finestra Attività](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>Ordinamento delle attività
 Per ordinare le attività in base ai criteri delle colonne, fare clic sull'intestazione di colonna. Ad esempio, facendo clic sull'intestazione di colonna **ID,** è possibile ordinare le attività in base all'ID attività: 1,2,3,4,5 e così via. Per invertire l'ordine, fare nuovamente clic sull'intestazione. La colonna di ordinamento e l'ordinamento correnti sono indicati da una freccia nella colonna.

## <a name="grouping-tasks"></a>Raggruppamento delle attività
 È possibile raggruppare le attività in base a una qualsiasi colonna nella visualizzazione elenco. Ad esempio, facendo clic con il pulsante destro del mouse sull'intestazione di colonna **Stato** e scegliendo **Raggruppa per** > **[*stato*]**, è possibile raggruppare tutte le attività con lo stesso stato. Ad esempio, è possibile visualizzare rapidamente le attività in attesa in modo da potersi concentrare sul motivo per cui sono bloccate. È possibile inoltre comprimere un gruppo di poco interesse durante la sessione di debug. Allo stesso modo, è possibile raggruppare in base alle altre colonne. Per contrassegnare o rimuovere il contrassegno di un gruppo, è sufficiente fare clic sul pulsante accanto all'intestazione del gruppo. Nell'illustrazione seguente viene mostrata la finestra **Attività** nella modalità raggruppata.

 ![Modalità raggruppata nella finestra Attività](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>Visualizzazione padre/figlio
 Questa visualizzazione è disponibile solo per il codice gestito. Facendo clic con  il pulsante destro del mouse sull'intestazione di colonna Stato e quindi scegliendo Raggruppa per padre , è possibile modificare l'elenco delle attività in una visualizzazione gerarchica, in cui ogni attività figlio è un sottonodo che può essere visualizzato o nascosto sotto il relativo nodo  >  padre.

## <a name="flagging-tasks"></a>Contrassegno delle attività
 È possibile contrassegnare il thread sull'attività in cui è in  esecuzione un'attività selezionando la voce dell'elenco attività e quindi scegliendo Contrassegna thread assegnato dal menu di scelta rapida oppure facendo clic sull'icona del flag nella prima colonna. Se si contrassegnano diverse attività, sarà successivamente possibile ordinare in base alla colonna del contrassegno in modo da portare tutte le attività contrassegnate in cima e potersi concentrare su di esse. È inoltre possibile usare la finestra **Stack in parallelo** per visualizzare solo le attività con contrassegno. In questo modo si possono filtrare le attività di poco interesse per il debug. I contrassegni non vengono salvati in modo permanente tra una sessione di debug e l'altra.

## <a name="freezing-and-thawing-tasks"></a>Blocco e sblocco delle attività
 Per bloccare il thread nel quale viene eseguita un'attività, fare clic con il pulsante destro del mouse sull'elemento dell'elenco di attività e scegliere **Blocca thread assegnato**. Se un'attività è già bloccata, il comando è **Thaw Assigned Thread**. Quando si blocca un thread, tale thread non verrà eseguito quando si esegue il codice un'istruzione alla volta dopo il punto di interruzione corrente. Il **comando Blocca tutti i thread ma questo comando** blocca tutti i thread tranne quello che esegue l'elemento dell'elenco attività.

 Nell'illustrazione seguente vengono mostrate le altre voci di menu per ogni attività.

 ![Menu thread di scelta rapida nella finestra Attività](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>Passaggio all'attività o al frame attivo

Il **comando Passa ad attività** rende l'attività corrente l'attività attiva. Il **comando Passa al** frame rende attiva la stack frame selezionata stack frame. Il contesto del debugger passa all'attività corrente o all'attività stack frame.

## <a name="see-also"></a>Vedi anche

- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
- [Programmazione parallela](/dotnet/standard/parallel-programming/index)
- [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime)
- [Utilizzo della finestra Stack in parallelo](../debugger/using-the-parallel-stacks-window.md)
- [Procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)