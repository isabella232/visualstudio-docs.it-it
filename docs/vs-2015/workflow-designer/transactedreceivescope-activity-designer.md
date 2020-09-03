---
title: ActivityDesigner TransactedReceiveScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4230e4b598553f5fefbc3b97663fd42320ee1e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72607008"
---
# <a name="transactedreceivescope-activity-designer"></a>ActivityDesigner TransactedReceiveScope
**TransactedReceiveScope** Designer viene utilizzato per creare e configurare un' <xref:System.ServiceModel.Activities.TransactedReceiveScope> attività.

## <a name="the-transactedreceivescope-activity"></a>Attività TransactedReceiveScope
 L'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope> consente di propagare una transazione in transazioni server create da un flusso di lavoro o da un dispatcher.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Utilizzo dell'ActivityDesigner TransactedReceiveScope
 L'ActivityDesigner **TransactedReceiveScope** è disponibile nella categoria **messaggistica** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** in. [!INCLUDE[wfd2](../includes/wfd2-md.md)] in alternativa, scegliere **barra degli** strumenti dal menu **Visualizza** oppure premere CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **TransactedReceiveScope** dalla **casella degli strumenti** e rilasciarlo nell'area in cui [!INCLUDE[wfd2](../includes/wfd2-md.md)] vengono in genere posizionate le attività. Verrà creata un' <xref:System.ServiceModel.Activities.TransactedReceiveScope> attività con un valore **DisplayName** predefinito di TransactedReceiveScope. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **TransactedReceiveScope** o nella casella **DisplayName** della griglia delle proprietà.

 **TransactedReceiveScope** Designer contiene le caselle **richiesta** e **corpo** . Tali caselle consentono di configurare la proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> che specifica un'attività <xref:System.ServiceModel.Activities.Receive> e una proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> che specifica un'altra <xref:System.Activities.Activity>. La proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crea una transazione. La transazione viene quindi resa ambiente per l'ambito della proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> in modo che qualsiasi attività interna a questo ambito venga eseguita in questa transazione.

### <a name="the-transactedreceivescope-properties"></a>Proprietà di TransactedReceiveScope
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.TransactedReceiveScope> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà di <xref:System.Activities.Activity.DisplayName%2A> possono essere modificate nella griglia delle proprietà oppure nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)], mentre le altre devono essere modificate nell'area di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Il valore predefinito è TransactedReceiveScope.<br /><br /> Sebbene il nome di <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatorio, se ne consiglia l'uso.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Vero|Rilascia un' <xref:System.ServiceModel.Activities.Receive> attività nel blocco **Request** nell'area dell'ActivityDesigner.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Falso|Rilascia un oggetto <xref:System.Activities.Activity> nel blocco **Body** nella superficie dell'ActivityDesigner.|

## <a name="see-also"></a>Vedere anche
 [ActivityDesigner CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)