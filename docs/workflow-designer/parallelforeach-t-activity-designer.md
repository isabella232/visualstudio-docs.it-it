---
title: Finestra di progettazione del flusso di lavoro - ParallelForEach&lt;T&gt; ActivityDesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfd7d3220bc67b764b96033ad516eb857bec6014
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="parallelforeach-activity-designer"></a>ActivityDesigner ParallelForEach

L'attività <xref:System.Activities.Statements.ParallelForEach%601> enumera gli elementi di una raccolta ed esegue in parallelo un'istruzione incorporata per ogni elemento della raccolta, ovvero in modo asincrono sullo stesso thread. Usare questa attività di controllo del flusso anziché l'attività <xref:System.Activities.Statements.Sequence> se si prevede che le relative attività figlio diventeranno inattive.

Il <xref:System.Activities.Statements.ParallelForEach%601> attività dispone di un <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> proprietà che contiene un utente specificato espressione Visual Basic. L'attività <xref:System.Activities.Statements.ParallelForEach%601> valuta tale proprietà in seguito al completamento di ogni ramo. Se restituisce **true**, quindi il <xref:System.Activities.Statements.ParallelForEach%601> attività viene completata senza eseguire gli altri rami. Se il <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> non restituisce **true**, quindi il <xref:System.Activities.Statements.ParallelForEach%601> attività viene completata quando tutte le relative attività figlio sono stati completati.

## <a name="the-parallelforeacht-activity"></a>L'attività ParallelForEach < T\> attività

<xref:System.Activities.Statements.ParallelForEach%601> enumera i propri valori e pianifica l'elemento <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> per ogni valore in cui viene enumerata. Esegue la pianificazione solo per l'elemento <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. La modalità di esecuzione del corpo varia a seconda che <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> diventi o meno inattivo.

Se <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> non diventa inattivo, viene eseguito in ordine inverso in quanto le attività pianificate vengono gestite come uno stack, con l'ultima attività pianificata eseguita per prima. Ad esempio, se si dispone di una raccolta di {1,2,3,4}in <xref:System.Activities.Statements.ParallelForEach%601> e utilizzare un **WriteLine** come corpo in cui scrivere il valore. Nella console l'ordine di stampa sarà 4, 3, 2, 1 In questo modo **WriteLine** non diventa inattivo e pertanto, dopo 4 **WriteLine** pianificazione delle quattro attività, queste vengono eseguite utilizzando un comportamento dello stack (first in last-out).

Il processo cambia se invece le attività incluse in <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> possono diventare inattive, come nel caso delle attività <xref:System.ServiceModel.Activities.Receive> o <xref:System.Activities.Statements.Delay>. Quindi non è necessario attenderne il completamento. <xref:System.Activities.Statements.ParallelForEach%601> passa all'attività corpo pianificata successiva e prova a eseguirla. Se anche questa attività diventa inattiva, <xref:System.Activities.Statements.ParallelForEach%601> passa ancora alla successiva attività Body.

### <a name="using-the-parallelforeacht-activity-designer"></a>Utilizzo di ParallelForEach\<T > ActivityDesigner

Il **ParallelForEach\<T >** ActivityDesigner sono reperibili il **flusso di controllo** categoria del **casella degli strumenti**, accessibile facendo clic il  **Casella degli strumenti** scheda sul lato sinistro della finestra di progettazione del flusso di lavoro (in alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

Il **ParallelForEach\<T >** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che vengono in genere posizionate le attività, per esempio, all'interno di un **sequenza** ActivityDesigner. Dopo averlo rilasciato in Progettazione flussi di lavoro, viene creato un <xref:System.Activities.Statements.ParallelForEach%601> attività, che per impostazione predefinita contiene una <xref:System.Activities.Activity.DisplayName%2A> dei **ParallelForEach < Int32\>.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach < T\> proprietà nella finestra di progettazione del flusso di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.ParallelForEach%601> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo visualizzato nell'intestazione dell'ActivityDesigner. Il valore predefinito è **ParallelForEach\<Int32 >**. Il valore può essere modificato facoltativamente nel **proprietà** griglia o direttamente nell'intestazione dell'ActivityDesigner.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Attività da eseguire per ogni elemento della raccolta. Per aggiungere il <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> attività, trascinare un'attività dalla casella degli strumenti nel **corpo** casella il **ParallelForEach\<T >** ActivityDesigner con testo di suggerimento "Rilasciare l'attività".|
|**TypeArgument**|True|Il tipo degli elementi di <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> raccolta specificata dal parametro generico *T*. Per impostazione predefinita, **TypeArgument** è impostato su **Int32**. Per modificare il tipo T nella **ParallelForEach < T\>**  ActivityDesigner, modificare il valore della **TypeArgument** casella combinata nella griglia delle proprietà.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|Raccolta di elementi da scorrere. Per impostare il <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, digitare un'espressione Visual Basic nel **valori** casella il **ForEach < T\>**  ActivityDesigner nella casella con il testo di suggerimento "Immettere un'espressione VB" o in  **I valori** casella il **proprietà** finestra.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Valutato al termine di ogni iterazione. Se restituisce true, le iterazioni in sospeso pianificate vengono annullate. Se questa proprietà non è impostata, tutte le istruzioni pianificate vengono eseguite fino al completamento.|

Per impostazione predefinita, l'iteratore del ciclo è denominato item. È possibile modificare il nome della variabile di iteratore nel **ForEach** casella **ParallelForEach\<T >** ActivityDesigner. L'iteratore del ciclo può essere usato nelle espressioni contenute in elementi figlio dell'attività <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>Vedere anche

- [sequenza](../workflow-designer/sequence-activity-designer.md)
- [Parallelo](../workflow-designer/parallel-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)