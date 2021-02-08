---
title: ActivityDesigner Progettazione flussi di lavoro-while
description: Informazioni sul modo in cui l'attività While esegue l'attività contenuta nel corpo mentre la condizione specificata restituisce true.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9447d32f17283e7123e2f99490acc49c1613360d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837996"
---
# <a name="while-activity-designer"></a>ActivityDesigner While

L' <xref:System.Activities.Statements.While> attività esegue l'attività contenuta in <xref:System.Activities.Statements.While.Body%2A> mentre l'oggetto specificato <xref:System.Activities.Statements.While.Condition%2A> restituisce **true**. L'attività contenuta potrebbe non essere mai eseguita. Se si desidera eseguirla almeno una volta, usare l'attività <xref:System.Activities.Statements.DoWhile>.

## <a name="while-properties-in-workflow-designer"></a>Proprietà di While in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.While> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.While> nell'intestazione. Il valore predefinito è While. Il valore può essere modificato nella finestra **Proprietà** o direttamente nell'intestazione Activity Designer.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.While.Body%2A>|Falso|Contiene l'attività da eseguire mentre l'oggetto <xref:System.Activities.Statements.While.Condition%2A> restituisce **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|Vero|Contiene l'espressione Visual Basic che viene valutata per determinare se l'attività nell'oggetto <xref:System.Activities.Statements.While.Body%2A> deve essere eseguita.|

## <a name="see-also"></a>Vedi anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
