---
title: Activity Designer DoWhile | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ec9bc21095905f373cf302deedd73bbce678a6de
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227656"
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
 [periodo di tempo](../workflow-designer/while-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)