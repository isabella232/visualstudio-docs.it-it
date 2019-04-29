---
title: Activity Designer CorrelationScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 95c8422d53903c3c7b81db9f6ef042c5ea9ff1c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976757"
---
# <a name="correlationscope-activity-designer"></a>ActivityDesigner CorrelationScope
Il **CorrelationScope** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.ServiceModel.Activities.CorrelationScope> attività che fornisce la gestione implicita delle attività di messaggistica figlio mediante un <xref:System.ServiceModel.Activities.CorrelationHandle> oggetto.  
  
## <a name="the-correlationscope-activity"></a>Attività CancellationScope  
 La proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> specifica l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per gestire le attività di messaggistica figlio. Le attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> contenute in <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> sono configurate per usare la proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> dell'attività <xref:System.ServiceModel.Activities.CorrelationScope> contenitore per eseguire la correlazione.  
  
### <a name="using-the-correlationscope-activity-designer"></a>Utilizzo dell'ActivityDesigner CorrelationScope  
 Il **CorrelationScope** ActivityDesigner è reperibile nel **messaggistica** categoria del **della casella degli strumenti**, accessibile facendo clic di **dellacaselladeglistrumenti** sul lato sinistro della scheda il [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu oppure premere CTRL + ALT + X.)  
  
 Il **CorrelationScope** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie. Ciò consente di creare un <xref:System.ServiceModel.Activities.CorrelationScope> attività con un valore predefinito **DisplayName** correlationscope. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **CorrelationScope** ActivityDesigner o nel **DisplayName** finestra del **proprietà** finestra.  
  
 Per specificare il <xref:System.ServiceModel.Activities.CorrelationHandle> utilizzato dalle attività di messaggistica figlio, fare clic sul pulsante puntini di sospensione accanto al **CorrelatesWith** campo **delle proprietà** finestra per visualizzare il **Editor espressioni**  nella finestra di dialogo. È possibile impostare questa proprietà anche nell'area di progettazione dell'attività.  
  
 L'attività il cui ambito all'interno della correlazione vengono specificate rilasciando le finestre di progettazione all'interno di **corpo** finestra all'interno del **CorrelationScope** progettazione.  
  
### <a name="the-correlationscope-properties"></a>Proprietà di CancellationScope  
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.CorrelationScope> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificati in **delle proprietà** finestra o scegliere [!INCLUDE[wfd2](../includes/wfd2-md.md)] area designer e spesso in entrambe.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Consente di specificare l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per gestire le attività di messaggistica figlio. Se non si imposta questa proprietà, <xref:System.ServiceModel.Activities.CorrelationScope> crea automaticamente un oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> implicito.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Consente di specificare le attività all'interno dell'ambito della correlazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)