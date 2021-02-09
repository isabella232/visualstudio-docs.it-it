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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e117fcbea0488c4b6a42125971984b86cf78251
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894257"
---
# <a name="dowhile-activity-designer"></a>ActivityDesigner DoWhile

L' <xref:System.Activities.Statements.DoWhile> attività esegue l'attività contenuta in <xref:System.Activities.Statements.DoWhile.Body%2A> almeno una volta, fino a quando una condizione specificata non restituisce **false**. Se è necessario non eseguire l'attività contenuta in un corpo del ciclo o eseguirla più volte, usare l'attività alternativa <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Proprietà di DoWhile in Progettazione flussi di lavoro

Nella tabella seguente vengono illustrate le proprietà più utili dell' <xref:System.Activities.Statements.DoWhile> attività e viene descritto come utilizzarle nella finestra di progettazione:

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Falso|L'attività da eseguire quando la condizione è **true**. Per aggiungere l' <xref:System.Activities.Statements.DoWhile.Body%2A> attività, rilasciare un'attività dalla casella degli strumenti nella casella **corpo** dell'ActivityDesigner **DoWhile** con il testo del suggerimento "drop Activity here".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Vero|Condizione da valutare prima di ogni iterazione del ciclo. Per impostare <xref:System.Activities.Statements.DoWhile.Condition%2A> , digitare un'espressione Visual Basic nella casella **condizione** nell'ActivityDesigner **DoWhile** o nella griglia delle proprietà.|

## <a name="see-also"></a>Vedi anche

- [While](../workflow-designer/while-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)