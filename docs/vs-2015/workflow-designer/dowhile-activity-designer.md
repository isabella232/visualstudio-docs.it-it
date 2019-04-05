---
title: Activity Designer DoWhile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d09954409baccfdc5d9eb083a15bd02f5d16cb85
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965490"
---
# <a name="dowhile-activity-designer"></a>ActivityDesigner DoWhile
Il <xref:System.Activities.Statements.DoWhile> attività viene eseguita l'attività contenuta nel relativo <xref:System.Activities.Statements.DoWhile.Body%2A> almeno una volta, fino a quando non viene valutata una condizione specificata **false**. Se è necessario non eseguire l'attività contenuta in un corpo del ciclo o eseguirla più volte, usare l'attività alternativa <xref:System.Activities.Statements.While>.  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>Proprietà di DoWhile in Progettazione flussi di lavoro  
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.DoWhile> e ne viene descritto l'uso nella finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|L'attività da eseguire se la condizione è **true**. Per aggiungere il <xref:System.Activities.Statements.DoWhile.Body%2A> attività, rilasciare un'attività dalla casella degli strumenti nel **corpo** nella casella il **DoWhile** ActivityDesigner con testo di suggerimento "Rilasciare l'attività".|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Condizione da valutare prima di ogni iterazione del ciclo. Per impostare il <xref:System.Activities.Statements.DoWhile.Condition%2A>, digitare un [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] espressione nel **condizione** nella casella il **DoWhile** attività della finestra di progettazione o nella griglia delle proprietà.|  
  
## <a name="see-also"></a>Vedere anche  
 [While](../workflow-designer/while-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)