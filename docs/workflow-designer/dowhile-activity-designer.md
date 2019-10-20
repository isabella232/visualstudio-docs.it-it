---
title: ActivityDesigner Progettazione flussi di lavoro-DoWhile
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85f8d6c442982fff47a679e8fc2ccc04ee515a9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650522"
---
# <a name="dowhile-activity-designer"></a>ActivityDesigner DoWhile

L'attività <xref:System.Activities.Statements.DoWhile> esegue l'attività contenuta nel <xref:System.Activities.Statements.DoWhile.Body%2A> almeno una volta, fino a quando una condizione specificata non restituisce **false**. Se è necessario non eseguire l'attività contenuta in un corpo del ciclo o eseguirla più volte, usare l'attività alternativa <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Proprietà di DoWhile in Progettazione flussi di lavoro

Nella tabella seguente vengono illustrate le proprietà dell'attività <xref:System.Activities.Statements.DoWhile> più utili e viene descritto come utilizzarle nella finestra di progettazione:

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|L'attività da eseguire quando la condizione è **true**. Per aggiungere l'attività <xref:System.Activities.Statements.DoWhile.Body%2A>, rilasciare un'attività dalla casella degli strumenti nella casella **corpo** dell'ActivityDesigner **DoWhile** con il testo del suggerimento "drop Activity here".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Condizione da valutare prima di ogni iterazione del ciclo. Per impostare il <xref:System.Activities.Statements.DoWhile.Condition%2A>, digitare un'espressione Visual Basic nella casella **condizione** nell'ActivityDesigner **DoWhile** o nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [While](../workflow-designer/while-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)