---
title: Finestra di progettazione del flusso di lavoro - attività ParallelForEach&lt;T&gt; ActivityDesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f584a7f22c4501aef4488b7e2be48b23e99f842b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070820"
---
# <a name="parallelforeach-activity-designer"></a>ActivityDesigner ParallelForEach

L'attività <xref:System.Activities.Statements.ParallelForEach%601> enumera gli elementi di una raccolta ed esegue in parallelo un'istruzione incorporata per ogni elemento della raccolta, ovvero in modo asincrono sullo stesso thread. Usare questa attività di controllo del flusso anziché l'attività <xref:System.Activities.Statements.Sequence> se si prevede che le relative attività figlio diventeranno inattive.

Il <xref:System.Activities.Statements.ParallelForEach%601> attività presenta un <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> proprietà che contiene un utente specificato espressione Visual Basic. L'attività <xref:System.Activities.Statements.ParallelForEach%601> valuta tale proprietà in seguito al completamento di ogni ramo. Se viene restituito **true**, quindi il <xref:System.Activities.Statements.ParallelForEach%601> attività viene completata senza eseguire gli altri rami. Se il <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> non restituisce **true**, quindi il <xref:System.Activities.Statements.ParallelForEach%601> attività viene completata al completamento di tutte le relative attività figlio.

## <a name="the-parallelforeacht-activity"></a>L'attività ParallelForEach < T\> attività

<xref:System.Activities.Statements.ParallelForEach%601> enumera i propri valori e pianifica l'elemento <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> per ogni valore in cui viene enumerata. Esegue la pianificazione solo per l'elemento <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. La modalità di esecuzione del corpo varia a seconda che <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> diventi o meno inattivo.

Se <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> non diventa inattivo, viene eseguito in ordine inverso in quanto le attività pianificate vengono gestite come uno stack, con l'ultima attività pianificata eseguita per prima. Ad esempio, se si dispone di una raccolta di {1,2,3,4}nelle <xref:System.Activities.Statements.ParallelForEach%601> e usare un **WriteLine** come corpo in cui scrivere il valore. Nella console l'ordine di stampa sarà 4, 3, 2, 1 Infatti **WriteLine** non diventa inattivo e pertanto, dopo 4 **WriteLine** attività è state pianificate, queste vengono eseguite utilizzando un comportamento dello stack (first in last-out).

Il processo cambia se invece le attività incluse in <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> possono diventare inattive, come nel caso delle attività <xref:System.ServiceModel.Activities.Receive> o <xref:System.Activities.Statements.Delay>. Quindi non è necessario attenderne il completamento. <xref:System.Activities.Statements.ParallelForEach%601> passa all'attività corpo pianificata successiva e prova a eseguirla. Se anche questa attività diventa inattiva, <xref:System.Activities.Statements.ParallelForEach%601> passa ancora alla successiva attività Body.

### <a name="using-the-parallelforeacht-activity-designer"></a>Utilizzo di ParallelForEach\<T > ActivityDesigner

Accesso di **ParallelForEach\<T >** ActivityDesigner nel **flusso di controllo** categoria del **casella degli strumenti**.

Il **ParallelForEach\<T >** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che vengono in genere posizionate le attività, per esempio, all'interno di un **sequenza** ActivityDesigner. Dopo averlo rilasciato in Progettazione flussi di lavoro, viene creato un <xref:System.Activities.Statements.ParallelForEach%601> attività, che per impostazione predefinita contiene un <xref:System.Activities.Activity.DisplayName%2A> dei **ParallelForEach < Int32\>.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>Attività ParallelForEach < T\> proprietà nella finestra di progettazione del flusso di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.ParallelForEach%601> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo visualizzato nell'intestazione dell'ActivityDesigner. Il valore predefinito è **ParallelForEach\<Int32 >**. Il valore può essere modificato facoltativamente nel **proprietà** griglia o direttamente nell'intestazione dell'ActivityDesigner.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Attività da eseguire per ogni elemento della raccolta. Per aggiungere il <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> attività, rilasciare un'attività dalla casella degli strumenti nel **corpo** nella casella il **ParallelForEach\<T >** ActivityDesigner con testo di suggerimento "Rilasciare l'attività".|
|**TypeArgument**|True|Il tipo degli elementi di <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> raccolta specificata dal parametro generico *T*. Per impostazione predefinita **TypeArgument** è impostata su **Int32**. Per modificare il tipo T nel **ParallelForEach < T\>**  ActivityDesigner, modificare il valore della **TypeArgument** casella combinata nella griglia delle proprietà.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|Raccolta di elementi da scorrere. Per impostare il <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, digitare un'espressione Visual Basic nel **valori** nella casella il **ForEach < T\>**  ActivityDesigner nella casella con il testo di suggerimento "Immettere un'espressione VB" o in  **I valori** nella casella il **proprietà** finestra.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Valutato al termine di ogni iterazione. Se restituisce true, le iterazioni in sospeso pianificate vengono annullate. Se questa proprietà non è impostata, tutte le istruzioni pianificate vengono eseguite fino al completamento.|

Per impostazione predefinita, l'iteratore del ciclo è denominato item. È possibile modificare il nome della variabile di iteratore nella **ForEach** nella casella **ParallelForEach\<T >** ActivityDesigner. L'iteratore del ciclo può essere usato nelle espressioni contenute in elementi figlio dell'attività <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>Vedere anche

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)