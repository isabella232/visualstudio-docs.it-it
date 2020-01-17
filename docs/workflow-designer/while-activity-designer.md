---
title: ActivityDesigner Progettazione flussi di lavoro-while
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77954925533c51885a056f7156121e68851ad769
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115171"
---
# <a name="while-activity-designer"></a>ActivityDesigner While

L'attività <xref:System.Activities.Statements.While> esegue l'attività contenuta nel relativo <xref:System.Activities.Statements.While.Body%2A> mentre il <xref:System.Activities.Statements.While.Condition%2A> specificato restituisce **true**. L'attività contenuta potrebbe non essere mai eseguita. Se si desidera eseguirla almeno una volta, usare l'attività <xref:System.Activities.Statements.DoWhile>.

## <a name="while-properties-in-workflow-designer"></a>Proprietà di While in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.While> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà:|Richiesto|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.While> nell'intestazione. Il valore predefinito è While. Il valore può essere modificato nella finestra **Proprietà** o direttamente nell'intestazione Activity Designer.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.While.Body%2A>|Falso|Contiene l'attività da eseguire mentre l'<xref:System.Activities.Statements.While.Condition%2A> restituisce **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Contiene l'espressione Visual Basic che viene valutata per determinare se l'attività nel <xref:System.Activities.Statements.While.Body%2A> deve essere eseguita.|

## <a name="see-also"></a>Vedere anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
