---
title: ActivityDesigner If | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6b35fe7f1b55dde25ec896f230f66cef00d24eed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659062"
---
# <a name="if-activity-designer"></a>ActivityDesigner If
L'attività <xref:System.Activities.Statements.If> valuta una condizione ed esegue un'attività che dipende dai risultati di tale valutazione. Questa attività è molto utile in caso di utilizzo di un stile di modellazione procedurale della programmazione. Un'attività <xref:System.Activities.Statements.If> può essere ad esempio annidata in un'attività <xref:System.Activities.Statements.Sequence> o in un'attività <xref:System.Activities.Statements.Parallel>. Se si usa un'attività <xref:System.Activities.Statements.Flowchart>, si prenda in considerazione l'uso alternativo di un'attività <xref:System.Activities.Statements.FlowDecision>.

## <a name="if-properties-in-the-workflow-designer"></a>Proprietà di If in Progettazione flussi di lavoro
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.If> e ne viene descritto l'uso nella finestra di progettazione.

|Nome proprietà|Richiesto|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.If.Condition%2A>|True|La condizione che determina l'attività figlio da eseguire. Per impostare il <xref:System.Activities.Statements.If.Condition%2A>, digitare un'espressione [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nella casella **condizione** nell'ActivityDesigner **if** o nella griglia delle proprietà.|
|<xref:System.Activities.Statements.If.Else%2A>|False|Attività da eseguire se la <xref:System.Activities.Statements.If.Condition%2A> è **false**. Per aggiungere un'attività eseguita dal ramo <xref:System.Activities.Statements.If.Else%2A>, rilasciare un'attività dalla **casella degli strumenti** nella casella **else** dell'ActivityDesigner **if** con il testo di suggerimento "drop Activity here".|
|<xref:System.Activities.Statements.If.Then%2A>|False|Attività da eseguire se la <xref:System.Activities.Statements.If.Condition%2A> è **true**. Per aggiungere un'attività che viene eseguita dal ramo di <xref:System.Activities.Statements.If.Then%2A>, rilasciare un'attività dalla casella **degli strumenti** nella casella **then** nell'ActivityDesigner **if** con il testo di suggerimento "drop Activity here".|

## <a name="see-also"></a>Vedere anche
 [Sequenza](../workflow-designer/sequence-activity-designer.md) del [flusso di controllo](../workflow-designer/control-flow-activity-designers.md) [parallelo](../workflow-designer/parallel-activity-designer.md)