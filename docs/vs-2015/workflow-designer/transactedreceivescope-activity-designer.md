---
title: Activity Designer TransactedReceiveScope | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: e718aaf754e9b4617aeb733196a73aa1bc125a9e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245245"
---
# <a name="transactedreceivescope-activity-designer"></a>ActivityDesigner TransactedReceiveScope
Il **TransactedReceiveScope** designer viene utilizzato per creare e configurare un <xref:System.ServiceModel.Activities.TransactedReceiveScope> attività.  
  
## <a name="the-transactedreceivescope-activity"></a>Attività TransactedReceiveScope  
 L'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope> consente di propagare una transazione in transazioni server create da un flusso di lavoro o da un dispatcher.  
  
### <a name="using-the-transactedreceivescope-activity-designer"></a>Utilizzo dell'ActivityDesigner TransactedReceiveScope  
 Il **TransactedReceiveScope** ActivityDesigner è reperibile nel **messaggistica** categoria del **della casella degli strumenti**, accessibile facendo clic di **della casella degli strumenti**  scheda [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu oppure premere CTRL + ALT + X.)  
  
 Il **TransactedReceiveScope** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque vengono posizionate le attività in genere. Ciò consente di creare un <xref:System.ServiceModel.Activities.TransactedReceiveScope> attività con un valore predefinito **DisplayName** di TransactedReceiveScope. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **TransactedReceiveScope** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.  
  
 Il **TransactedReceiveScope** finestra di progettazione contiene **richiedere** e **Body** caselle. Tali caselle consentono di configurare la proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> che specifica un'attività <xref:System.ServiceModel.Activities.Receive> e una proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> che specifica un'altra <xref:System.Activities.Activity>. La proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crea una transazione. La transazione viene quindi resa ambiente per l'ambito della proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> in modo che qualsiasi attività interna a questo ambito venga eseguita in questa transazione.  
  
### <a name="the-transactedreceivescope-properties"></a>Proprietà di TransactedReceiveScope  
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.TransactedReceiveScope> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà di <xref:System.Activities.Activity.DisplayName%2A> possono essere modificate nella griglia delle proprietà oppure nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)], mentre le altre devono essere modificate nell'area di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Il valore predefinito è TransactedReceiveScope.<br /><br /> Sebbene il nome di <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatorio, se ne consiglia l'uso.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Elimina una <xref:System.ServiceModel.Activities.Receive> attività nel **richiedere** blocco sulla superficie dell'ActivityDesigner.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Elimina un' <xref:System.Activities.Activity> nella **corpo** blocco sulla superficie dell'ActivityDesigner.|  
  
## <a name="see-also"></a>Vedere anche  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Ricezione](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Invia](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)