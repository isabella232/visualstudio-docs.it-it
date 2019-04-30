---
title: Uso della finestra attività | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdf7c5fe724ff4b043ca304eee3e5e0f31b0dd85
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437712"
---
# <a name="using-the-tasks-window"></a>Utilizzo della finestra Attività
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La finestra **Attività** è simile alla finestra **Thread**, l'unica differenza è che mostra informazioni sugli oggetti <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](http://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) o [WinJS.Promise](http://msdn.microsoft.com/library/windows/apps/br211867.aspx) e non su ogni thread. Analogamente ai thread, le attività rappresentano operazioni asincrone eseguibili simultaneamente; tuttavia, più attività possono essere eseguite nello stesso thread. Visualizzare [programmazione asincrona in JavaScript (app di Windows Store)](http://msdn.microsoft.com/library/windows/apps/hh700330.aspx) per altre informazioni.  
  
 Nel codice gestito è possibile usare la finestra **Attività** quando si utilizzano gli oggetti <xref:System.Threading.Tasks.Task?displayProperty=fullName> o con le parole chiave **await** e **async** (**Await** e **Async** in Visual Basic). Per altre informazioni sulle attività nel codice gestito, vedere [programmazione parallela](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d).  
  
 Nel codice nativo, è possibile usare la finestra **Attività** quando si utilizzano [gruppi di attività](http://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [algoritmi paralleli](http://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [agenti asincroni](http://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a) e [attività leggere](http://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90). Per altre informazioni sulle attività nel codice nativo, vedere [Runtime di concorrenza](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c).  
  
 In JavaScript è possibile utilizzare la finestra Attività quando si utilizza codice promise .then.  
  
 La finestra **Attività** può essere usata ogni volta che ci si interrompe l'esecuzione nel debugger. È possibile accedere a esso nel menu **Debug** scegliendo **Finestre** e facendo clic su **Attività**. Nell'illustrazione seguente viene mostrata la finestra **Attività** nella modalità predefinita.  
  
 ![Finestra attività in parallelo](../debugger/media/parallel-tasks-window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
> Nel codice gestito, un oggetto <xref:System.Threading.Tasks.Task> con lo stato <xref:System.Threading.Tasks.TaskStatus>, <xref:System.Threading.Tasks.TaskStatus> o <xref:System.Threading.Tasks.TaskStatus> potrebbe non essere visualizzato nella finestra Attività quando i thread gestiti si trovano nello stato sospensione o join.  
  
## <a name="tasks-column-information"></a>Informazioni nelle colonne della finestra Attività  
 Nelle colonne della finestra **Attività** vengono visualizzate le informazioni seguenti.  
  
|Nome colonna|Descrizione|  
|-----------------|-----------------|  
|**Flag**|Mostra quali attività sono contrassegnate e consente di impostare o rimuovere un flag per un'attività.|  
|**Icone**|Una freccia gialla indica l'attività corrente. L'attività corrente è l'attività in primo piano nel thread corrente.<br /><br /> Una freccia bianca indica l'attività di interruzione, vale a dire l'attività corrente al momento della chiamata del debugger.<br /><br /> L'icona di sospensione indica un'attività bloccata dall'utente. È possibile bloccare e sbloccare un'attività facendovi clic sopra con il pulsante destro del mouse nell'elenco.|  
|**ID**|Numero fornito dal sistema per l'attività. Nel codice nativo, è l'indirizzo dell'attività.|  
|**Status**|Stato corrente dell'attività (pianificata, attiva, in deadlock, in attesa o completata). Un'attività pianificata è un'attività che non è stata ancora eseguita, pertanto non dispone ancora di uno stack di chiamate, un thread assegnato o informazioni correlate.<br /><br /> Un'attività attiva è un'attività che stava eseguendo codice prima dell'accesso al debugger.<br /><br /> Un'attività in attesa è un'attività bloccata in quanto sta attendendo la segnalazione di un evento, il rilascio di un blocco o la conclusione di un'altra attività.<br /><br /> Un'attività in deadlock è un'attività in attesa il cui thread è in deadlock con un altro thread.<br /><br /> Passare il mouse sul **stato** cella di un'attività in deadlock o in attesa visualizzare altre informazioni sul blocco. **Avviso:**  La finestra **Attività** segnala un deadlock solo per un'attività bloccata che usa una primitiva di sincronizzazione supportata da WCT (Wait Chain Traversal). Ad esempio, per un deadlock <xref:System.Threading.Tasks.Task> oggetto, che utilizza WCT, il debugger viene segnalato **-in deadlock in attesa**. Per un'attività in deadlock gestita dal runtime di concorrenza, che non utilizza WCT, viene visualizzato il messaggio **In attesa**. Per altre informazioni su WCT, vedere [Wait Chain Traversal](http://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Ora di inizio**|Ora in cui l'attività è diventata attiva.|  
|**Durata**|Numero di secondi durante i quali l'attività è rimasta attiva.|  
|**Tempo di completamento**|Ora in cui l'attività è stata completata.|  
|**Posizione**|Percorso corrente nello stack di chiamate dell'attività. Passare il mouse su questa cella per visualizzare l'intero stack di chiamate dell'attività. Le attività pianificate non presentano alcun valore in questa colonna.|  
|**Task**|Metodo iniziale ed eventuali argomenti passati all'attività quando è stata creata.|  
|**Padre**|ID dell'attività che ha creato questa attività. Se la cella è vuota significa che l'attività non dispone di un'attività padre. Questo dato è applicabile ai soli programmi gestiti.|  
|**Assegnazione thread**|ID e nome del thread nel quale viene eseguita l'attività.|  
|**Stato restituito**|Stato dell'attività quando è stata completata. I valori di stato restituito sono **Success**, **Cancelled**, e **errore**.|  
|**AppDomain**|Dominio applicazione nel quale viene eseguita l'attività, in caso di codice gestito.|  
|**task_group**|Indirizzo dell'oggetto [task_group](http://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) che ha pianificato l'attività, in caso di codice nativo. Per gli agenti asincroni e le attività leggere, questa colonna viene impostata su 0.|  
|Process|ID del processo in cui viene eseguita l'attività.|  
|Stato Async|Per il codice gestito, lo stato dell'attività. Per impostazione predefinita, questa colonna è nascosta. Per visualizzarla, aprire il menu di scelta rapida per una delle intestazioni di colonna. Scegliere **Colonne**, **AsyncState**.|  
  
 Per aggiungere colonne alla visualizzazione, fare clic con il pulsante destro del mouse su un'intestazione di colonna e selezionare le colonne desiderate. Per rimuovere le colonne, annullare le selezioni. È possibile inoltre riordinare le colonne trascinandole a sinistra o a destra. Nell'illustrazione seguente viene mostrato il menu di scelta rapida delle colonne.  
  
 ![Menu di scelta rapida visualizza nella finestra attività in parallelo](../debugger/media/parallel-tasks-contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Ordinamento delle attività  
 Per ordinare le attività in base ai criteri delle colonne, fare clic sull'intestazione di colonna. Ad esempio, facendo i **ID** intestazione di colonna, è possibile ordinare le attività da un ID attività: 1,2,3,4,5 e così via. Per invertire l'ordine, fare nuovamente clic sull'intestazione. La colonna di ordinamento e l'ordinamento correnti sono indicati da una freccia nella colonna.  
  
## <a name="grouping-tasks"></a>Raggruppamento delle attività  
 È possibile raggruppare le attività in base a una qualsiasi colonna nella visualizzazione elenco. Ad esempio, facendo clic con il **lo stato** intestazione di colonna e scegliendo **Raggruppa per stato**, è possibile raggruppare tutte le attività con lo stesso stato. Tale operazione può risultare utile, ad esempio, per visualizzare rapidamente tutte le attività in attesa, così da concentrarsi sul motivo del blocco. È possibile inoltre comprimere un gruppo di poco interesse durante la sessione di debug. Allo stesso modo, è possibile raggruppare in base alle altre colonne. Per contrassegnare o rimuovere il contrassegno di un gruppo, è sufficiente fare clic sul pulsante accanto all'intestazione del gruppo. Nell'illustrazione seguente viene mostrata la finestra **Attività** nella modalità raggruppata.  
  
 ![Modalità raggruppata nella finestra attività in parallelo](../debugger/media/parallel-tasks-groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Visualizzazione padre/figlio  
 (Questa visualizzazione è disponibile solo per codice gestito). Facendo clic su un'intestazione di colonna e quindi scegliendo **visualizzazione padre / figlio**, è possibile modificare l'elenco di attività per una visualizzazione gerarchica, in ogni classe figlio, quali attività è un nodo secondario che può essere visualizzato o nascosto sotto il relativo elemento padre. Nell'illustrazione seguente vengono mostrate le attività nella visualizzazione padre/figlio.  
  
 ![Elemento padre&#45;visualizzazione figlio nella finestra attività in parallelo](../debugger/media/parallel-tasks-parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>Contrassegno delle attività  
 È possibile contrassegnare il thread di attività in cui viene eseguita un'attività selezionando l'attività elenco elemento e scegliendo **Flag** dal menu di scelta rapida oppure facendo clic sull'icona del flag nella prima colonna. Se si contrassegnano diverse attività, sarà successivamente possibile ordinare in base alla colonna del contrassegno in modo da portare tutte le attività contrassegnate in cima e potersi concentrare su di esse. È inoltre possibile usare la finestra **Stack in parallelo** per visualizzare solo le attività con contrassegno. In questo modo si possono filtrare le attività di poco interesse per il debug. I contrassegni non vengono salvati in modo permanente tra una sessione di debug e l'altra.  
  
## <a name="freezing-and-thawing-tasks"></a>Blocco e sblocco delle attività  
 Per bloccare il thread nel quale viene eseguita un'attività, fare clic con il pulsante destro del mouse sull'elemento dell'elenco di attività e scegliere **Blocca thread assegnato**. Se un'attività è già bloccata, il comando è **Sblocca thread assegnato**. Quando si blocca un thread, questo non verrà eseguito nel momento in cui si proseguirà con l'esecuzione del codice dopo il punto di interruzione corrente. Il **bloccare tutti i thread, ma questo** comando Blocca tutti i thread ad eccezione di quello che è in esecuzione l'elemento elenco attività.  
  
 Nell'illustrazione seguente vengono mostrate le altre voci di menu per ogni attività.  
  
 ![Menu thread collegamenti nella finestra attività in parallelo](../debugger/media/parallel-tasks-contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Programmazione parallela](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Runtime di concorrenza](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Uso della finestra Stack in parallelo](../debugger/using-the-parallel-stacks-window.md)   
 [Procedura dettagliata: Debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)
