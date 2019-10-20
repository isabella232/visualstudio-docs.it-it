---
title: Progettazione modelli Progettazione flussi di lavoro SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7c552e8bb94ed9035f25bdd40b7944458e61a11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649962"
---
# <a name="sendandreceivereply-template-designer"></a>Finestra di progettazione del modello SendAndReceiveReply

Il modello **SendAndReceiveReply** viene usato per creare una coppia di attività preconfigurate <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply>. Le attività fanno parte di un'attività <xref:System.Activities.Statements.Sequence> e sono correlate come parte di un modello di scambio di messaggi di richiesta/risposta sul client.

## <a name="the-sendandreceivereply-template"></a>Modello SendAndReceiveReply

L'aggiunta del modello **SendAndReceiveReply** esegue tre operazioni oltre a creare le attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> all'interno di un'attività <xref:System.Activities.Statements.Sequence>:

- Configura le proprietà <xref:System.ServiceModel.Activities.Send.OperationName%2A> e <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> dell'attività <xref:System.ServiceModel.Activities.Send>.

- Associazione della proprietà <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.ReceiveReply> all'attività <xref:System.ServiceModel.Activities.Send>.

- Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="use-the-sendandreceivereply-template-designer"></a>Usare la finestra di progettazione modelli SendAndReceiveReply

Accedere a **SendAndReceiveReply** Activity Designer nella categoria **messaggistica** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **SendAndReceiveReply** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando le attività vengono in genere posizionate. Se si elimina l'ActivityDesigner, viene creata un'attività <xref:System.ServiceModel.Activities.Send> che può essere configurata con l'ActivityDesigner **Send** e un <xref:System.ServiceModel.Activities.ReceiveReply> correlato che può essere configurato con **ReceiveReplyForSend** designer.

Per ulteriori informazioni sull'utilizzo della finestra di progettazione **Send** per configurare l'attività <xref:System.ServiceModel.Activities.Send>, vedere [Send](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Proprietà di ReceiveReply

Nella tabella seguente vengono illustrate le proprietà <xref:System.ServiceModel.Activities.ReceiveReply> e viene descritto il modo in cui vengono utilizzate nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area di Progettazione flussi di lavoro.

| Nome proprietà | Richiesto | Utilizzo |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.ReceiveReply>. L'impostazione predefinita è ReceiveReplyForSend.<br /><br /> Sebbene l'uso di un valore non predefinito per il <xref:System.Activities.Activity.DisplayName%2A> descrittivo non sia strettamente necessario, è preferibile usare tale valore. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Riferimento all'attività <xref:System.ServiceModel.Activities.Send> correlata a questa attività <xref:System.ServiceModel.Activities.ReceiveReply>. Questa proprietà non può essere **null**. Le attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> sono usate insieme al client per modellare un modello di messaggistica di richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione non è possibile modificare questa proprietà perché viene associata automaticamente all'attività <xref:System.ServiceModel.Activities.Send> da cui è stata creata l'attività <xref:System.ServiceModel.Activities.ReceiveReply>. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Per modificare questa proprietà, fare clic sul pulsante con i puntini di sospensione accanto al campo **contenuto** nella griglia delle proprietà oppure fare clic sul pulsante **Definisci** accanto all'etichetta **contenuto** nell'area di progettazione dell'attività di **ricezione** . Entrambi visualizzano la finestra di dialogo **Definizione contenuto** . Per ulteriori informazioni sull'utilizzo di questa casella, vedere [finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con i puntini di sospensione accanto alla proprietà <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> nella griglia proprietà per aprire la finestra di dialogo **Aggiungi inizializzatori di correlazione** . Per ulteriori informazioni sull'utilizzo di questa casella, vedere la finestra di [dialogo Aggiungi CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Specifica l'intestazione Action del messaggio. Se non è impostata in modo esplicito, il valore predefinito è:<br /><br /> <strong>https://tempuri.org/{service spazio dei nomi del contratto}/{nome nome contratto}/{nome operazione}.</strong> |

## <a name="see-also"></a>Vedere anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)