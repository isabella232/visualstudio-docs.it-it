---
title: Activity Designer WriteLine | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f1085c7a8989ebfdecdf0e9782afeeaf1e9b4400
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528291"
---
# <a name="writeline-activity-designer"></a>ActivityDesigner WriteLine
Il **WriteLine** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.WriteLine> attività.  
  
## <a name="the-writeline-activity"></a>Attività WriteLine  
 L'attività <xref:System.Activities.Statements.WriteLine> scrive il testo in un oggetto <xref:System.IO.TextWriter> specificato. Se non è specificato alcun oggetto <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> scrive il testo sulla console.  
  
### <a name="using-the-writeline-activity-designer"></a>Utilizzo dell'ActivityDesigner WriteLine  
 Il **WriteLine** ActivityDesigner è reperibile nel **primitive** categoria del **della casella degli strumenti**, accessibile facendo clic di **della casella degli strumenti**scheda della finestra di [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu oppure premere CTRL + ALT + X.)  
  
 Il **WriteLine** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.WriteLine> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito WriteLine. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **WriteLine** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.  
  
### <a name="the-writeline-properties"></a>Proprietà di WriteLine  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.WriteLine> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.WriteLine>. Il valore predefinito è WriteLine. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Testo da scrivere. Per impostare la proprietà, digitare un'espressione Visual Basic nel **testo** nella casella il **WriteLine** attività della finestra di progettazione o nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|Oggetto <xref:System.IO.TextWriter> nel quale <xref:System.Activities.Statements.WriteLine> scrive <xref:System.Activities.Statements.WriteLine.Text%2A>. Il valore predefinito corrisponde alla console.|  
  
## <a name="see-also"></a>Vedere anche  
 [Primitive](../workflow-designer/primitives-activity-designers.md)   
 [assegnare](../workflow-designer/assign-activity-designer.md)   
 [Ritardo](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)