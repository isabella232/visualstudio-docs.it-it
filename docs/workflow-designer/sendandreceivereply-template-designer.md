---
title: Finestra di progettazione del modello SendAndReceiveReply
description: Informazioni su come usare il modello SendAndReceiveReply in Progettazione flussi di lavoro per creare una coppia di attività Send e ReceiveReply preconfigurato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 6a6a91c562750898fd085f1b32d8c299a8604d93
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135286"
---
# <a name="sendandreceivereply-template-designer"></a>Finestra di progettazione del modello SendAndReceiveReply

Il **modello SendAndReceiveReply** viene usato per creare una coppia di attività e preconfigurato. <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> Le attività fanno parte di un'attività e sono correlate come parte di un modello di scambio di messaggi di <xref:System.Activities.Statements.Sequence> richiesta/risposta nel client.

## <a name="the-sendandreceivereply-template"></a>Modello SendAndReceiveReply

**L'aggiunta del modello SendAndReceiveReply** esegue tre operazioni oltre alla creazione delle <xref:System.ServiceModel.Activities.Send> attività e <xref:System.ServiceModel.Activities.ReceiveReply> all'interno di <xref:System.Activities.Statements.Sequence> un'attività:

- Configura le proprietà <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> e <xref:System.ServiceModel.Activities.Send> dell'attività.

- Associazione della proprietà <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.ReceiveReply> all'attività <xref:System.ServiceModel.Activities.Send>.

- Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="use-the-sendandreceivereply-template-designer"></a>Usare La finestra di progettazione modelli SendAndReceiveReply

Accedere **all'ActivityDesigner SendAndReceiveReply** nella **categoria Messaggistica** della Casella degli **strumenti**. L'ActivityDesigner **SendAndReceiveReply** può essere  trascinato dalla casella degli strumenti e rilasciato nell'area Progettazione flussi di lavoro in cui in genere si trovano le attività. L'eliminazione dell'ActivityDesigner crea un'attività che può essere configurata con l'ActivityDesigner Send e una classe correlata che può essere configurata con la finestra di <xref:System.ServiceModel.Activities.Send>  <xref:System.ServiceModel.Activities.ReceiveReply> progettazione **ReceiveReplyForSend.**

Per altre informazioni sull'uso della finestra **di** progettazione Di invio per configurare <xref:System.ServiceModel.Activities.Send> l'attività, vedere [Inviare](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Proprietà di ReceiveReply

La tabella seguente illustra le <xref:System.ServiceModel.Activities.ReceiveReply> proprietà e ne descrive l'uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area Progettazione flussi di lavoro proprietà.

| Nome proprietà | Obbligatoria | Utilizzo |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.ReceiveReply>. L'impostazione predefinita è ReceiveReplyForSend.<br /><br /> Anche se l'uso di un valore non predefinito per l'elemento descrittivo non è strettamente necessario, è meglio <xref:System.Activities.Activity.DisplayName%2A> usare tale valore. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | Vero | Riferimento all'attività <xref:System.ServiceModel.Activities.Send> correlata a questa attività <xref:System.ServiceModel.Activities.ReceiveReply>. Questa proprietà non deve essere **Null.** <xref:System.ServiceModel.Activities.Send> Le <xref:System.ServiceModel.Activities.ReceiveReply> attività e vengono usate insieme nel client per modellare un modello di messaggistica di richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione non è possibile modificare questa proprietà perché viene associata automaticamente all'attività da cui è <xref:System.ServiceModel.Activities.Send> stata creata <xref:System.ServiceModel.Activities.ReceiveReply> l'attività. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | Falso | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà facendo clic sul pulsante con i puntini di sospensione  accanto al campo **Contenuto** nella griglia delle proprietà oppure facendo clic sul pulsante Definisci accanto all'etichetta **Contenuto** nell'area dell'ActivityDesigner Receive.  Entrambi visualizzano la **finestra di dialogo Definizione** contenuto. Per altre informazioni sull'uso di questa casella, vedere [Finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | Falso | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con i puntini di sospensione accanto alla proprietà nella griglia delle proprietà per aprire la finestra di dialogo Aggiungi <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> **inizializzatori** di correlazione. Per altre informazioni sull'uso di questa casella, vedere Finestra di dialogo [Aggiungi inizializzatori di correlazione](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | Falso | Specifica l'intestazione Action del messaggio. Se non è impostato in modo esplicito, il valore predefinito è:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Vedi anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)