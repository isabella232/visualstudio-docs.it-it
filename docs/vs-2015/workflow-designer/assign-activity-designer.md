---
title: Activity Designer ASSIGN | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: c27d70f7dbff9d7f9d30d7dda34c5c2c98bfe891
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281268"
---
# <a name="assign-activity-designer"></a>ActivityDesigner Assign
Il **assegnare** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Assign> attività.  
  
## <a name="the-assign-activity"></a>Attività Assign  
 L'attività <xref:System.Activities.Statements.Assign> assegna un valore a una variabile o a un argomento.  
  
### <a name="using-the-assign-activity-designer"></a>Utilizzo dell'ActivityDesigner Assign  
 Il **assegnare** ActivityDesigner è reperibile nel **primitive** categoria del **della casella degli strumenti**, accessibile facendo clic di **della casella degli strumenti**scheda (in alternativa, selezionare **casella degli strumenti** dal **visualizzazione** menu o CTRL + ALT + X.)  
  
 Il **assegnare** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie in cui le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Ciò consente di creare un <xref:System.Activities.Statements.Assign> attività con un valore predefinito **DisplayName** ASSIGN. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **assegnare** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.  
  
### <a name="the-assign-properties"></a>Proprietà di Assign  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Assign> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Assign>. L'impostazione predefinita è Assign. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|La variabile o l'argomento cui è assegnata la proprietà <xref:System.Activities.Statements.Assign.Value%2A>. È necessario che sia un identificativo valido di Visual Basic. Per impostare la proprietà, digitare un'espressione Visual Basic nel **al** nella casella il **assegnare** attività della finestra di progettazione o nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Valore assegnato alla variabile. Per impostare il <xref:System.Activities.Statements.Assign.Value%2A>, digitare un'espressione Visual Basic nel **valore** nella casella il **assegnare** attività della finestra di progettazione o nella griglia delle proprietà.|  
  
## <a name="see-also"></a>Vedere anche  
 [Primitive](../workflow-designer/primitives-activity-designers.md)   
 [Ritardo](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)