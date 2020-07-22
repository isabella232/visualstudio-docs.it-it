---
title: Progettazione modelli Progettazione flussi di lavoro ReceiveAndSendReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66822664766ac64e466882fda27906f56ebb4aad
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876008"
---
# <a name="receiveandsendreply-template-designer"></a>Finestra di progettazione del modello ReceiveAndSendReply

Il modello **ReceiveAndSendReply** viene usato per creare una coppia di attività e preconfigurate <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> . Le attività fanno parte di un' <xref:System.Activities.Statements.Sequence> attività e sono correlate come parte di un modello di scambio di messaggi di richiesta/risposta sul server.

## <a name="the-receiveandsendreply-template"></a>Modello ReceiveAndSendReply

L'aggiunta di un modello **ReceiveAndSendReply** esegue tre operazioni oltre a creare le <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> attività e con un' <xref:System.Activities.Statements.Sequence> attività:

- Configura le <xref:System.ServiceModel.Activities.Receive.OperationName%2A> proprietà e <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> dell' <xref:System.ServiceModel.Activities.Receive> attività.

- Associazione della proprietà <xref:System.ServiceModel.Activities.SendReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.Receive> all'attività <xref:System.ServiceModel.Activities.Send>.

- Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="use-the-receiveandsendreply-template-designer"></a>Usare la finestra di progettazione modelli ReceiveAndSendReply

Accedere a **ReceiveAndSendReply** Activity Designer nella categoria **messaggistica** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **ReceiveAndSendReply** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando le attività vengono in genere posizionate. Quando si elimina l'ActivityDesigner, viene creata un' <xref:System.ServiceModel.Activities.Receive> attività che può essere configurata con l'ActivityDesigner **Send** e un oggetto correlato <xref:System.ServiceModel.Activities.SendReply> che può essere configurato con SendReplyToReceive designer.

Per ulteriori informazioni sull'utilizzo di progettazione **ricezione** per configurare l' <xref:System.ServiceModel.Activities.Receive> attività, vedere [Receive Activity Designer](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Proprietà di SendReply

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.SendReply> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area di Progettazione flussi di lavoro.

| Nome proprietà | Obbligatoria | Utilizzo |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.SendReply>. Il valore predefinito è SendReplyToReceive.<br /><br /> Sebbene l'uso di un valore non predefinito per friendly <xref:System.Activities.Activity.DisplayName%2A> non sia strettamente necessario, è preferibile usare tale valore. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | Vero | Riferimento all'attività <xref:System.ServiceModel.Activities.Receive> correlata a questa attività <xref:System.ServiceModel.Activities.SendReply>. Questa proprietà non può essere **null**. <xref:System.ServiceModel.Activities.Receive><xref:System.ServiceModel.Activities.SendReply>le attività e vengono utilizzate insieme sul server per modellare un modello di messaggistica di richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione non è possibile modificare questa proprietà perché viene associata automaticamente all' <xref:System.ServiceModel.Activities.Send> attività da cui è stata creata l' <xref:System.ServiceModel.Activities.SendReply> attività. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | Falso | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Per modificare questa proprietà, fare clic sul pulsante con i puntini di sospensione accanto al campo **contenuto** nella griglia delle proprietà oppure fare clic sul pulsante **Definisci** accanto all'etichetta **contenuto** nell'area di progettazione dell'attività di **ricezione** . Entrambi visualizzano la finestra di dialogo **Definizione contenuto** . Per ulteriori informazioni sull'utilizzo di questa casella, vedere l'argomento relativo alla finestra di [dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | Falso | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con i puntini di sospensione accanto alla <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> proprietà nella griglia proprietà per aprire la finestra di dialogo **Aggiungi inizializzatori di correlazione** . Per ulteriori informazioni sull'utilizzo di questa casella, vedere l'argomento relativo alla finestra di [dialogo Aggiungi CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | Falso | Specifica l'intestazione Action del messaggio. Se non è impostata in modo esplicito, il valore predefinito è:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | Falso | Specifica se l'istanza di servizio del flusso di lavoro deve essere salvata in modo permanente prima di inviare il messaggio di risposta. Il valore predefinito è **false**. |

## <a name="see-also"></a>Vedi anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)