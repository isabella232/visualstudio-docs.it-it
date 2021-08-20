---
title: Progettazione flussi di lavoro- ActivityDesigner If
description: Informazioni su come l'attività If valuta una condizione ed esegue un'attività a seconda dei risultati di tale valutazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 6abacbe5f5212a062c9f23cdc7cfab3e27d7cb6b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155161"
---
# <a name="if-activity-designer"></a>ActivityDesigner If

L'attività <xref:System.Activities.Statements.If> valuta una condizione ed esegue un'attività che dipende dai risultati di tale valutazione. Questa attività è molto utile in caso di utilizzo di un stile di modellazione procedurale della programmazione. Un'attività <xref:System.Activities.Statements.If> può essere ad esempio annidata in un'attività <xref:System.Activities.Statements.Sequence> o in un'attività <xref:System.Activities.Statements.Parallel>. Se si usa un'attività <xref:System.Activities.Statements.Flowchart>, si prenda in considerazione l'uso alternativo di un'attività <xref:System.Activities.Statements.FlowDecision>.

## <a name="if-properties-in-the-workflow-designer"></a>Proprietà di If in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.If> e ne viene descritto l'uso nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Vero|La condizione che determina l'attività figlio da eseguire. Per impostare <xref:System.Activities.Statements.If.Condition%2A> , digitare un'Visual Basic nella casella **Condizione** dell'ActivityDesigner **If** o nella griglia delle proprietà.|
|<xref:System.Activities.Statements.If.Else%2A>|Falso|Attività da eseguire se è <xref:System.Activities.Statements.If.Condition%2A> **false.** Per aggiungere un'attività eseguita dal ramo , rilasciare un'attività dalla casella degli strumenti nella casella Else dell'ActivityDesigner If con il testo del suggerimento <xref:System.Activities.Statements.If.Else%2A> "Drop Activity  Here".  |
|<xref:System.Activities.Statements.If.Then%2A>|Falso|Attività da eseguire se è <xref:System.Activities.Statements.If.Condition%2A> **true.** Per aggiungere un'attività eseguita dal ramo , rilasciare un'attività dalla casella degli strumenti nella casella Then dell'ActivityDesigner If con il testo del suggerimento <xref:System.Activities.Statements.If.Then%2A> "Drop Activity  Here".  |

## <a name="see-also"></a>Vedi anche

- [Sequenza](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
