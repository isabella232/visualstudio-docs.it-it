---
title: Finestra di progettazione del flusso di lavoro - ActivityDesigner Parallel
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79e1e7e48f7ed7e8cd4084805dfae2018a886a82
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002769"
---
# <a name="parallel-activity-designer"></a>ActivityDesigner Parallel

L'attività <xref:System.Activities.Statements.Parallel> esegue contemporaneamente una raccolta delle attività figlio.

## <a name="the-parallel-activity"></a>Attività Parallel

L'attività <xref:System.Activities.Statements.Parallel> archivia le relative attività figlio in una raccolta <xref:System.Activities.Statements.Parallel.Branches%2A>. Usare l'attività <xref:System.Activities.Statements.Parallel> anziché l'attività <xref:System.Activities.Statements.Sequence> se alcune delle attività figlio possono diventare inattive.

Il <xref:System.Activities.Statements.Parallel> attività presenta un <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> proprietà che contiene un utente specificato espressione Visual Basic. L'attività <xref:System.Activities.Statements.Parallel> valuta tale proprietà in seguito al completamento di ogni ramo. Se viene restituito **True**, quindi il <xref:System.Activities.Statements.Parallel> attività viene completata senza eseguire gli altri rami. Se il <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> non restituisce **True**, quindi il <xref:System.Activities.Statements.Parallel> attività viene completata al completamento di tutte le relative attività figlio.

### <a name="using-the-parallel-activity-designer"></a>Utilizzo dell'ActivityDesigner Parallel

Accesso di **parallele** ActivityDesigner nel **flusso di controllo** categoria del **della casella degli strumenti**.

Il **parallele** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che vengono in genere posizionate le attività, ad esempio, all'interno di un **Sequenza** ActivityDesigner. Dopo averlo rilasciato in Progettazione flussi di lavoro, viene creato un <xref:System.Activities.Statements.Parallel> attività, che per impostazione predefinita contiene un <xref:System.Activities.Activity.DisplayName%2A> di **parallele**

Per aggiungere un'attività per il <xref:System.Activities.Statements.Parallel.Branches%2A> raccolta di attività parallel, trascinare un altro ActivityDesigner dal **della casella degli strumenti** e rilasciarla sul triangolo all'interno di **parallele** ActivityDesigner. I triangoli si trovano di fianco alle attività contenute nei rami. È possibile aggiungere ulteriori attività ripetendo questa procedura. Le attività possono essere riordinate trascinandoli e rilasciandoli all'interno di **parallele** ActivityDesigner.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Proprietà di ParallelActivity in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà dell'attività Parallel e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo visualizzato nell'intestazione dell'ActivityDesigner. Il valore predefinito è **parallele**. Il valore può essere modificato facoltativamente nel **proprietà** griglia o direttamente nell'intestazione dell'ActivityDesigner.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contiene la raccolta di attività figlio da eseguire.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Restituisce il risultato dopo il completamento di un ramo. Se viene restituito **True**, quindi pianificati rami in sospeso vengono annullate. Se questa proprietà non è impostata o restituisce **False**, l'attività viene completata al completamento di tutte le relative attività figlio. Il valore predefinito è **null**.|

## <a name="see-also"></a>Vedere anche

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)