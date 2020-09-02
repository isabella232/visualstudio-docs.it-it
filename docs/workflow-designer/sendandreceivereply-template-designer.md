---
title: Progettazione modelli Progettazione flussi di lavoro SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17512337b58fb394352ccaab153ca72badbb4652
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875904"
---
# <a name="sendandreceivereply-template-designer"></a>Finestra di progettazione del modello SendAndReceiveReply

Il modello **SendAndReceiveReply** viene usato per creare una coppia di attività e preconfigurate <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> . Le attività fanno parte di un' <xref:System.Activities.Statements.Sequence> attività e sono correlate come parte di un modello di scambio di messaggi di richiesta/risposta sul client.

## <a name="the-sendandreceivereply-template"></a>Modello SendAndReceiveReply

L'aggiunta del modello **SendAndReceiveReply** esegue tre operazioni oltre a creare le <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> attività e all'interno di un' <xref:System.Activities.Statements.Sequence> attività:

- Configura le <xref:System.ServiceModel.Activities.Send.OperationName%2A> proprietà e <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> dell' <xref:System.ServiceModel.Activities.Send> attività.

- Associazione della proprietà <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.ReceiveReply> all'attività <xref:System.ServiceModel.Activities.Send>.

- Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="use-the-sendandreceivereply-template-designer"></a>Usare la finestra di progettazione modelli SendAndReceiveReply

Accedere a **SendAndReceiveReply** Activity Designer nella categoria **messaggistica** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **SendAndReceiveReply** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando le attività vengono in genere posizionate. Quando si elimina l'ActivityDesigner, viene creata un' <xref:System.ServiceModel.Activities.Send> attività che può essere configurata con l'ActivityDesigner **Send** e un oggetto correlato <xref:System.ServiceModel.Activities.ReceiveReply> che può essere configurato con **ReceiveReplyForSend** designer.

Per ulteriori informazioni sull'utilizzo della finestra di progettazione **Send** per configurare l' <xref:System.ServiceModel.Activities.Send> attività, vedere [Send](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Proprietà di ReceiveReply

Nella tabella seguente sono illustrate le <xref:System.ServiceModel.Activities.ReceiveReply> proprietà e viene descritto come vengono utilizzate nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area di Progettazione flussi di lavoro.

| Nome proprietà | Obbligatoria | Utilizzo |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.ReceiveReply>. L'impostazione predefinita è ReceiveReplyForSend.<br /><br /> Sebbene l'uso di un valore non predefinito per friendly <xref:System.Activities.Activity.DisplayName%2A> non sia strettamente necessario, è preferibile usare tale valore. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | Vero | Riferimento all'attività <xref:System.ServiceModel.Activities.Send> correlata a questa attività <xref:System.ServiceModel.Activities.ReceiveReply>. Questa proprietà non può essere **null**. <xref:System.ServiceModel.Activities.Send><xref:System.ServiceModel.Activities.ReceiveReply>le attività e vengono utilizzate insieme sul client per modellare un modello di messaggistica di richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione non è possibile modificare questa proprietà perché viene associata automaticamente all' <xref:System.ServiceModel.Activities.Send> attività da cui è stata creata l' <xref:System.ServiceModel.Activities.ReceiveReply> attività. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | Falso | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Per modificare questa proprietà, fare clic sul pulsante con i puntini di sospensione accanto al campo **contenuto** nella griglia delle proprietà oppure fare clic sul pulsante **Definisci** accanto all'etichetta **contenuto** nell'area di progettazione dell'attività di **ricezione** . Entrambi visualizzano la finestra di dialogo **Definizione contenuto** . Per ulteriori informazioni sull'utilizzo di questa casella, vedere [finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | Falso | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con i puntini di sospensione accanto alla <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> proprietà nella griglia proprietà per aprire la finestra di dialogo **Aggiungi inizializzatori di correlazione** . Per ulteriori informazioni sull'utilizzo di questa casella, vedere la finestra di [dialogo Aggiungi CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | Falso | Specifica l'intestazione Action del messaggio. Se non è impostata in modo esplicito, il valore predefinito è:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Vedere anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)