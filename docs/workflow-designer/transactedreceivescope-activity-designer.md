---
title: Finestra di progettazione del flusso di lavoro, ActivityDesigner TransactedReceiveScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a42c1cc9dac8e71bfe71f684232fdbf67fadb710
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929543"
---
# <a name="transactedreceivescope-activity-designer"></a>ActivityDesigner TransactedReceiveScope

Il **TransactedReceiveScope** designer viene utilizzato per creare e configurare un <xref:System.ServiceModel.Activities.TransactedReceiveScope> attività.

## <a name="the-transactedreceivescope-activity"></a>Attività TransactedReceiveScope

L'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope> consente di propagare una transazione in transazioni server create da un flusso di lavoro o da un dispatcher.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Utilizzo dell'ActivityDesigner TransactedReceiveScope

Accesso di **TransactedReceiveScope** ActivityDesigner nel **messaggistica** categoria del **della casella degli strumenti**. Il **TransactedReceiveScope** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che vengono in genere posizionate le attività. Ciò consente di creare un <xref:System.ServiceModel.Activities.TransactedReceiveScope> attività con un valore predefinito **DisplayName** di TransactedReceiveScope. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **TransactedReceiveScope** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.

Il **TransactedReceiveScope** finestra di progettazione contiene **richiedere** e **Body** caselle. Tali caselle consentono di configurare la proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> che specifica un'attività <xref:System.ServiceModel.Activities.Receive> e una proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> che specifica un'altra <xref:System.Activities.Activity>. La proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crea una transazione. La transazione viene quindi resa ambiente per l'ambito della proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> in modo che qualsiasi attività interna a questo ambito venga eseguita in questa transazione.

### <a name="the-transactedreceivescope-properties"></a>Proprietà di TransactedReceiveScope

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.TransactedReceiveScope> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Questi <xref:System.Activities.Activity.DisplayName%2A> proprietà può essere modificata nella griglia delle proprietà o nell'area di progettazione del flusso di lavoro, ma gli altri devono essere modificati nell'area di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Il valore predefinito è TransactedReceiveScope.<br /><br /> Sebbene il nome di <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatorio, se ne consiglia l'uso.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Elimina una <xref:System.ServiceModel.Activities.Receive> attività nel **richiedere** blocco sulla superficie dell'ActivityDesigner.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Elimina un' <xref:System.Activities.Activity> nella **corpo** blocco sulla superficie dell'ActivityDesigner.|

## <a name="see-also"></a>Vedere anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)