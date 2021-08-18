---
title: ActivityDesigner TransactedReceiveScope
description: In Progettazione flussi di lavoro informazioni su come usare la finestra di progettazione TransactedReceiveScope per creare e configurare un'attività TransactedReceiveScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: cbdbd2ce46e5d9d6bf9f0f69c81c9bfdaa0b1d6d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135117"
---
# <a name="transactedreceivescope-activity-designer"></a>ActivityDesigner TransactedReceiveScope

La **finestra di progettazione TransactedReceiveScope** viene usata per creare e configurare un'attività. <xref:System.ServiceModel.Activities.TransactedReceiveScope>

## <a name="the-transactedreceivescope-activity"></a>Attività TransactedReceiveScope

L'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope> consente di propagare una transazione in transazioni server create da un flusso di lavoro o da un dispatcher.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Utilizzo dell'ActivityDesigner TransactedReceiveScope

Accedere **all'ActivityDesigner TransactedReceiveScope** nella **categoria Messaggistica** della Casella degli **strumenti**. L'ActivityDesigner **TransactedReceiveScope** può essere  trascinato dalla casella degli strumenti e rilasciato nell'area Progettazione flussi di lavoro in cui in genere si trovano le attività. Verrà creata <xref:System.ServiceModel.Activities.TransactedReceiveScope> un'attività con **un valore DisplayName predefinito** di TransactedReceiveScope. <xref:System.Activities.Activity.DisplayName%2A>L'oggetto può essere modificato nell'intestazione **dell'ActivityDesigner TransactedReceiveScope** o nella **casella DisplayName** della griglia delle proprietà.

La **finestra di progettazione TransactedReceiveScope** contiene le **caselle Request** e **Body.** Tali caselle consentono di configurare la proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> che specifica un'attività <xref:System.ServiceModel.Activities.Receive> e una proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> che specifica un'altra <xref:System.Activities.Activity>. La proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crea una transazione. La transazione viene quindi resa ambiente per l'ambito della proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> in modo che qualsiasi attività interna a questo ambito venga eseguita in questa transazione.

### <a name="the-transactedreceivescope-properties"></a>Proprietà di TransactedReceiveScope

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.TransactedReceiveScope> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà o nell'area Progettazione flussi di lavoro, ma le altre devono essere modificate <xref:System.Activities.Activity.DisplayName%2A> nell'area di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Il valore predefinito è TransactedReceiveScope.<br /><br /> Sebbene il nome di <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatorio, se ne consiglia l'uso.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Vero|Rilascia <xref:System.ServiceModel.Activities.Receive> un'attività nel blocco **Request** nell'area dell'ActivityDesigner.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Falso|Rilascia un oggetto <xref:System.Activities.Activity> nel blocco **Body** nell'area dell'ActivityDesigner.|

## <a name="see-also"></a>Vedi anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)