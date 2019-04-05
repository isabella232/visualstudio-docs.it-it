---
title: Se la finestra di progettazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3ab8c9a7f49302b2308f97855c022d8e8d5126e0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968713"
---
# <a name="if-activity-designer"></a>ActivityDesigner If
L'attività <xref:System.Activities.Statements.If> valuta una condizione ed esegue un'attività che dipende dai risultati di tale valutazione. Questa attività è molto utile in caso di utilizzo di un stile di modellazione procedurale della programmazione. Un'attività <xref:System.Activities.Statements.If> può essere ad esempio annidata in un'attività <xref:System.Activities.Statements.Sequence> o in un'attività <xref:System.Activities.Statements.Parallel>. Se si usa un'attività <xref:System.Activities.Statements.Flowchart>, si prenda in considerazione l'uso alternativo di un'attività <xref:System.Activities.Statements.FlowDecision>.  
  
## <a name="if-properties-in-the-workflow-designer"></a>Proprietà di If in Progettazione flussi di lavoro  
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.If> e ne viene descritto l'uso nella finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|La condizione che determina l'attività figlio da eseguire. Per impostare il <xref:System.Activities.Statements.If.Condition%2A>, digitare un [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] espressione nel **condizione** nella casella il **se** attività della finestra di progettazione o nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|L'attività da eseguire se il <xref:System.Activities.Statements.If.Condition%2A> viene **false**. Per aggiungere un'attività che viene eseguita dal <xref:System.Activities.Statements.If.Else%2A> creare un ramo, rilasciarla dal **della casella degli strumenti** nel **Else** casella il **se** ActivityDesigner con testo di suggerimento " Rilascia attività qui".|  
|<xref:System.Activities.Statements.If.Then%2A>|False|L'attività da eseguire se il <xref:System.Activities.Statements.If.Condition%2A> viene **true**. Per aggiungere un'attività che viene eseguita dal <xref:System.Activities.Statements.If.Then%2A> creare un ramo, rilasciarla dal **della casella degli strumenti** nel **quindi** casella il **se** ActivityDesigner con testo di suggerimento " Rilascia attività qui".|  
  
## <a name="see-also"></a>Vedere anche  
 [Sequenza](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)