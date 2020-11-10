---
title: ActivityDesigner Progettazione flussi di lavoro-if
description: Informazioni sul modo in cui l'attività If valuta una condizione ed esegue un'attività in base ai risultati della valutazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2daa2ab6e3f41d5447204db573b8ae228d617fdf
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437814"
---
# <a name="if-activity-designer"></a>ActivityDesigner If

L'attività <xref:System.Activities.Statements.If> valuta una condizione ed esegue un'attività che dipende dai risultati di tale valutazione. Questa attività è molto utile in caso di utilizzo di un stile di modellazione procedurale della programmazione. Un'attività <xref:System.Activities.Statements.If> può essere ad esempio annidata in un'attività <xref:System.Activities.Statements.Sequence> o in un'attività <xref:System.Activities.Statements.Parallel>. Se si usa un'attività <xref:System.Activities.Statements.Flowchart>, si prenda in considerazione l'uso alternativo di un'attività <xref:System.Activities.Statements.FlowDecision>.

## <a name="if-properties-in-the-workflow-designer"></a>Proprietà di If in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.If> e ne viene descritto l'uso nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Vero|La condizione che determina l'attività figlio da eseguire. Per impostare <xref:System.Activities.Statements.If.Condition%2A> , digitare un'espressione Visual Basic nella casella **condizione** nell'ActivityDesigner **if** o nella griglia delle proprietà.|
|<xref:System.Activities.Statements.If.Else%2A>|Falso|Attività da eseguire se <xref:System.Activities.Statements.If.Condition%2A> è **false**. Per aggiungere un'attività che viene eseguita dal <xref:System.Activities.Statements.If.Else%2A> Branch, rilasciare un'attività dalla **casella degli strumenti** nella casella **else** nell'ActivityDesigner **if** con il testo di suggerimento "drop Activity here".|
|<xref:System.Activities.Statements.If.Then%2A>|Falso|Attività da eseguire se <xref:System.Activities.Statements.If.Condition%2A> è **true**. Per aggiungere un'attività che viene eseguita dal <xref:System.Activities.Statements.If.Then%2A> Branch, rilasciare un'attività dalla **casella degli strumenti** nella casella **then** nell'ActivityDesigner **if** con il testo di suggerimento "drop Activity here".|

## <a name="see-also"></a>Vedere anche

- [Sequenza](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
