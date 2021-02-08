---
title: ActivityDesigner TransactedReceiveScope
description: In Progettazione flussi di lavoro, informazioni su come è possibile usare TransactedReceiveScope designer per creare e configurare un'attività TransactedReceiveScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eceb0776fd1cb5e850dab2b97ab6e7e56a684ebd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838022"
---
# <a name="transactedreceivescope-activity-designer"></a>ActivityDesigner TransactedReceiveScope

**TransactedReceiveScope** Designer viene utilizzato per creare e configurare un' <xref:System.ServiceModel.Activities.TransactedReceiveScope> attività.

## <a name="the-transactedreceivescope-activity"></a>Attività TransactedReceiveScope

L'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope> consente di propagare una transazione in transazioni server create da un flusso di lavoro o da un dispatcher.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Utilizzo dell'ActivityDesigner TransactedReceiveScope

Accedere a **TransactedReceiveScope** Activity Designer nella categoria **messaggistica** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **TransactedReceiveScope** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando le attività vengono in genere posizionate. Verrà creata un' <xref:System.ServiceModel.Activities.TransactedReceiveScope> attività con un valore **DisplayName** predefinito di TransactedReceiveScope. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **TransactedReceiveScope** o nella casella **DisplayName** della griglia delle proprietà.

**TransactedReceiveScope** Designer contiene le caselle **richiesta** e **corpo** . Tali caselle consentono di configurare la proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> che specifica un'attività <xref:System.ServiceModel.Activities.Receive> e una proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> che specifica un'altra <xref:System.Activities.Activity>. La proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crea una transazione. La transazione viene quindi resa ambiente per l'ambito della proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> in modo che qualsiasi attività interna a questo ambito venga eseguita in questa transazione.

### <a name="the-transactedreceivescope-properties"></a>Proprietà di TransactedReceiveScope

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.TransactedReceiveScope> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali <xref:System.Activities.Activity.DisplayName%2A> proprietà possono essere modificate nella griglia delle proprietà o nell'area di progettazione flussi di lavoro, ma le altre devono essere modificate nell'area di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Il valore predefinito è TransactedReceiveScope.<br /><br /> Sebbene il nome di <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatorio, se ne consiglia l'uso.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Vero|Rilascia un' <xref:System.ServiceModel.Activities.Receive> attività nel blocco **Request** nell'area dell'ActivityDesigner.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Falso|Rilascia un oggetto <xref:System.Activities.Activity> nel blocco **Body** nella superficie dell'ActivityDesigner.|

## <a name="see-also"></a>Vedi anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)