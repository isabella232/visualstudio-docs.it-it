---
title: Finestra di progettazione del flusso di lavoro - se la finestra di progettazione
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 762199906bbb84701c044b5fa9f3f3b8c6fdfdae
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55916973"
---
# <a name="if-activity-designer"></a>ActivityDesigner If

L'attività <xref:System.Activities.Statements.If> valuta una condizione ed esegue un'attività che dipende dai risultati di tale valutazione. Questa attività è molto utile in caso di utilizzo di un stile di modellazione procedurale della programmazione. Un'attività <xref:System.Activities.Statements.If> può essere ad esempio annidata in un'attività <xref:System.Activities.Statements.Sequence> o in un'attività <xref:System.Activities.Statements.Parallel>. Se si usa un'attività <xref:System.Activities.Statements.Flowchart>, si prenda in considerazione l'uso alternativo di un'attività <xref:System.Activities.Statements.FlowDecision>.

## <a name="if-properties-in-the-workflow-designer"></a>Proprietà di If in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.If> e ne viene descritto l'uso nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|True|La condizione che determina l'attività figlio da eseguire. Per impostare il <xref:System.Activities.Statements.If.Condition%2A>, digitare un'espressione Visual Basic nel **condizione** nella casella il **se** attività della finestra di progettazione o nella griglia delle proprietà.|
|<xref:System.Activities.Statements.If.Else%2A>|False|L'attività da eseguire se il <xref:System.Activities.Statements.If.Condition%2A> viene **false**. Per aggiungere un'attività che viene eseguita dal <xref:System.Activities.Statements.If.Else%2A> creare un ramo, rilasciarla dal **della casella degli strumenti** nel **Else** casella il **se** ActivityDesigner con testo di suggerimento " Rilascia attività qui".|
|<xref:System.Activities.Statements.If.Then%2A>|False|L'attività da eseguire se il <xref:System.Activities.Statements.If.Condition%2A> viene **true**. Per aggiungere un'attività che viene eseguita dal <xref:System.Activities.Statements.If.Then%2A> creare un ramo, rilasciarla dal **della casella degli strumenti** nel **quindi** casella il **se** ActivityDesigner con testo di suggerimento " Rilascia attività qui".|

## <a name="see-also"></a>Vedere anche

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)