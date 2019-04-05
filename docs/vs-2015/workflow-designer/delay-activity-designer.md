---
title: Ritardare l'ActivityDesigner | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 528317a97a9b2582442dacfcf9ba8a35943736e8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58970281"
---
# <a name="delay-activity-designer"></a>ActivityDesigner Delay
Il **ritardo** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Delay> attività.  
  
## <a name="the-delay-activity"></a>Attività Delay  
 L'attività <xref:System.Activities.Statements.Delay> ritarda l'esecuzione di un flusso di lavoro per una quantità di tempo specificata.  
  
### <a name="using-the-delay-activity-designer"></a>Utilizzo dell'ActivityDesigner Delay  
 Il **ritardo** ActivityDesigner è reperibile nel **primitive** categoria del **della casella degli strumenti**, accessibile facendo clic di **della casella degli strumenti**scheda della finestra di [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu oppure premere CTRL + ALT + X.)  
  
 Il **ritardo** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.Delay> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito Delay. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **ritardo** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.  
  
### <a name="the-delay-properties"></a>Proprietà di Delay  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Delay> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Delay>. Il valore predefinito è Delay. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Durata del ritardo del flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà. Per specificare tale durata, digitare un valore <xref:System.TimeSpan> letterale nel formato 00:00:00 o un'espressione Visual Basic.|  
  
## <a name="see-also"></a>Vedere anche  
 [Primitive](../workflow-designer/primitives-activity-designers.md)   
 [assegnare](../workflow-designer/assign-activity-designer.md)   
 [Activity Designer Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)