---
title: ActivityDesigner Progettazione flussi di lavoro-ActivityDesigner ParallelForEach &lt;T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b68cd543ed41408e7510708367c8e539c0702ea1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650095"
---
# <a name="parallelforeach-activity-designer"></a>ActivityDesigner ActivityDesigner ParallelForEach

L'attività <xref:System.Activities.Statements.ParallelForEach%601> enumera gli elementi di una raccolta ed esegue in parallelo un'istruzione incorporata per ogni elemento della raccolta, ovvero in modo asincrono sullo stesso thread. Usare questa attività di controllo del flusso anziché l'attività <xref:System.Activities.Statements.Sequence> se si prevede che le relative attività figlio diventeranno inattive.

L'attività <xref:System.Activities.Statements.ParallelForEach%601> dispone di una proprietà <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> che contiene un'espressione Visual Basic specificata dall'utente. L'attività <xref:System.Activities.Statements.ParallelForEach%601> valuta tale proprietà in seguito al completamento di ogni ramo. Se restituisce **true**, l'attività <xref:System.Activities.Statements.ParallelForEach%601> viene completata senza eseguire gli altri rami. Se il <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> non restituisce **true**, l'attività <xref:System.Activities.Statements.ParallelForEach%601> viene completata al completamento di tutte le relative attività figlio.

## <a name="the-parallelforeacht-activity"></a>Attività ActivityDesigner ParallelForEach < T \>

<xref:System.Activities.Statements.ParallelForEach%601> enumera i propri valori e pianifica l'elemento <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> per ogni valore in cui viene enumerata. Esegue la pianificazione solo per l'elemento <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. La modalità di esecuzione del corpo varia a seconda che <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> diventi o meno inattivo.

Se <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> non diventa inattivo, viene eseguito in ordine inverso in quanto le attività pianificate vengono gestite come uno stack, con l'ultima attività pianificata eseguita per prima. Ad esempio, se si dispone di una raccolta di {1,2,3,4}in <xref:System.Activities.Statements.ParallelForEach%601> e si utilizza un oggetto **WriteLine** come corpo per scrivere il valore. Si dispone di 4, 3, 2, 1 stampato nella console. Questo perché **WriteLine** non viene inattivo, quindi dopo che sono state pianificate 4 attività **WriteLine** sono state eseguite utilizzando un comportamento dello stack (primo nell'ultimo).

Il processo cambia se invece le attività incluse in <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> possono diventare inattive, come nel caso delle attività <xref:System.ServiceModel.Activities.Receive> o <xref:System.Activities.Statements.Delay>. Quindi non è necessario attenderne il completamento. <xref:System.Activities.Statements.ParallelForEach%601> passa all'attività corpo pianificata successiva e prova a eseguirla. Se anche questa attività diventa inattiva, <xref:System.Activities.Statements.ParallelForEach%601> passa ancora alla successiva attività Body.

### <a name="using-the-parallelforeacht-activity-designer"></a>Uso di ActivityDesigner ParallelForEach \<T > Activity Designer

Accedere all'ActivityDesigner **activitydesigner parallelforeach \<T >** nella categoria **flusso di controllo** della **casella degli strumenti**.

È possibile trascinare l'ActivityDesigner **activitydesigner parallelforeach \<T >** dalla **casella degli strumenti** e rilasciarlo nell'area di progettazione flussi di lavoro quando gli ActivityDesigner vengono normalmente posizionati, ad esempio all'interno di un'attività **Sequence** progettazione. Una volta rilasciata la Progettazione flussi di lavoro, viene creata un'attività <xref:System.Activities.Statements.ParallelForEach%601>, che per impostazione predefinita contiene un <xref:System.Activities.Activity.DisplayName%2A> di **activitydesigner parallelforeach < Int32 \>.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ActivityDesigner ParallelForEach < T \> proprietà nell'Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.ParallelForEach%601> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo visualizzato nell'intestazione dell'ActivityDesigner. Il valore predefinito è **activitydesigner parallelforeach \<Int32 >** . Facoltativamente, è possibile modificare il valore nella griglia **Proprietà** o direttamente nell'intestazione Activity Designer.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Attività da eseguire per ogni elemento della raccolta. Per aggiungere l'attività <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>, rilasciare un'attività dalla casella degli strumenti nella casella **corpo** dell'activitydesigner **ActivityDesigner ParallelForEach \<T >** con il testo del suggerimento "drop Activity here".|
|**TypeArgument**|True|Tipo degli elementi nella raccolta <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> specificata dal parametro generico *t*. Per impostazione predefinita, **TypeArgument** è impostato su **Int32**. Per modificare il tipo T nell'ActivityDesigner **activitydesigner parallelforeach < T \>** , modificare il valore della casella combinata **TypeArgument** nella griglia delle proprietà.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|Raccolta di elementi da scorrere. Per impostare il <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, digitare un'espressione Visual Basic nella casella **valori** dell'activitydesigner **ForEach < t \>** nella casella con il testo di suggerimento "immettere un'espressione VB" o nella casella **valori** nella finestra **Proprietà** .|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Valutato al termine di ogni iterazione. Se restituisce true, le iterazioni in sospeso pianificate vengono annullate. Se questa proprietà non è impostata, tutte le istruzioni pianificate vengono eseguite fino al completamento.|

Per impostazione predefinita, l'iteratore del ciclo è denominato item. È possibile modificare il nome della variabile iteratore nella casella **foreach** in **ActivityDesigner ParallelForEach \<T >** Activity Designer. L'iteratore del ciclo può essere usato nelle espressioni contenute in elementi figlio dell'attività <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>Vedere anche

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)