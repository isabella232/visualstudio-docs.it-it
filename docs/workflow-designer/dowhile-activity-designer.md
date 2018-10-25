---
title: Finestra di progettazione del flusso di lavoro - Activity Designer DoWhile
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 19817fb23bd8a22532df7d349262b689f632a3a7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839622"
---
# <a name="dowhile-activity-designer"></a>ActivityDesigner DoWhile

Il <xref:System.Activities.Statements.DoWhile> attività viene eseguita l'attività contenuta nel relativo <xref:System.Activities.Statements.DoWhile.Body%2A> almeno una volta, fino a quando non viene valutata una condizione specificata **false**. Se è necessario non eseguire l'attività contenuta in un corpo del ciclo o eseguirla più volte, usare l'attività alternativa <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Proprietà di DoWhile in Progettazione flussi di lavoro

La tabella seguente illustra il più utile <xref:System.Activities.Statements.DoWhile> proprietà dell'attività e viene spiegato come usarle nella finestra di progettazione:

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|L'attività da eseguire se la condizione è **true**. Per aggiungere il <xref:System.Activities.Statements.DoWhile.Body%2A> attività, rilasciare un'attività dalla casella degli strumenti nel **corpo** nella casella il **DoWhile** ActivityDesigner con testo di suggerimento "Rilasciare l'attività".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Condizione da valutare prima di ogni iterazione del ciclo. Per impostare il <xref:System.Activities.Statements.DoWhile.Condition%2A>, digitare un'espressione Visual Basic nel **condizione** nella casella il **DoWhile** attività della finestra di progettazione o nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [While](../workflow-designer/while-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)