---
title: ActivityDesigner Progettazione flussi di lavoro-DoWhile
description: Informazioni sul modo in cui l'attività DoWhile esegue l'attività contenuta nel corpo almeno una volta, fino a quando una condizione specificata non restituisce false.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8385fe376f56738d76e066dc172e7b6b516f9a08
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438061"
---
# <a name="dowhile-activity-designer"></a>ActivityDesigner DoWhile

L' <xref:System.Activities.Statements.DoWhile> attività esegue l'attività contenuta in <xref:System.Activities.Statements.DoWhile.Body%2A> almeno una volta, fino a quando una condizione specificata non restituisce **false**. Se è necessario non eseguire l'attività contenuta in un corpo del ciclo o eseguirla più volte, usare l'attività alternativa <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Proprietà di DoWhile in Progettazione flussi di lavoro

Nella tabella seguente vengono illustrate le proprietà più utili dell' <xref:System.Activities.Statements.DoWhile> attività e viene descritto come utilizzarle nella finestra di progettazione:

|Nome proprietà|Obbligatoria|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Falso|L'attività da eseguire quando la condizione è **true**. Per aggiungere l' <xref:System.Activities.Statements.DoWhile.Body%2A> attività, rilasciare un'attività dalla casella degli strumenti nella casella **corpo** dell'ActivityDesigner **DoWhile** con il testo del suggerimento "drop Activity here".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Vero|Condizione da valutare prima di ogni iterazione del ciclo. Per impostare <xref:System.Activities.Statements.DoWhile.Condition%2A> , digitare un'espressione Visual Basic nella casella **condizione** nell'ActivityDesigner **DoWhile** o nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [While](../workflow-designer/while-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)