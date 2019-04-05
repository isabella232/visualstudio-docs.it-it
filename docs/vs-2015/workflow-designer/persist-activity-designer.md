---
title: Activity Designer Persist | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f87997178f98e9e632b756b5a4440c19544b5c86
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966839"
---
# <a name="persist-activity-designer"></a>ActivityDesigner Persist
Il **Persist** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Persist> attività.  
  
## <a name="the-persist-activity"></a>Attività Persist  
 L'attività <xref:System.Activities.Statements.Persist> salva un flusso di lavoro su disco, se possibile. Non è possibile eseguire l'attività <xref:System.Activities.Statements.Persist> in un'area non permanente come, ad esempio, all'interno di un'attività <xref:System.Activities.Statements.TransactionScope>. Se si usa un'attività <xref:System.Activities.Statements.Persist> in un ambito non permanente, viene generata un'eccezione in fase di esecuzione.  
  
### <a name="using-the-persist-activity-designer"></a>Utilizzo dell'ActivityDesigner Persist  
 Il **Persist** ActivityDesigner è reperibile nella **Runtime** categoria del **della casella degli strumenti**, accessibile facendo clic la **casella degli strumenti** scheda (in alternativa, selezionare **casella degli strumenti** dalle **visualizzazione** menu o CTRL + ALT + X.)  
  
 Il **Persist** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Ciò consente di creare un <xref:System.Activities.Statements.Persist> attività con un valore predefinito **DisplayName** Persist. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **Persist** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.  
  
### <a name="the-persist-properties"></a>Proprietà di Persist  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Persist> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Persist>. Il valore predefinito è Persist. Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'uso.|  
  
## <a name="see-also"></a>Vedere anche  
 [Fase di esecuzione](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)