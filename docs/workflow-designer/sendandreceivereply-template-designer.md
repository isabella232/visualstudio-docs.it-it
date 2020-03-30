---
title: Progettazione flussi di lavoro - SendAndReceiveReply Progettazione modelli
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
ms.openlocfilehash: 2067ee92883d0c4ad3003f23032a88f5da3fa710
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395250"
---
# <a name="sendandreceivereply-template-designer"></a>Finestra di progettazione del modello SendAndReceiveReply

Il **modello SendAndReceiveReply** viene utilizzato per creare <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> una coppia di attività e preconfigurate. Le attività fanno <xref:System.Activities.Statements.Sequence> parte di un'attività e sono correlate come parte di un modello di scambio di messaggi di richiesta/risposta sul client.

## <a name="the-sendandreceivereply-template"></a>Il modello SendAndReceiveReply

L'aggiunta del modello SendAndReceiveReply esegue <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> tre operazioni oltre alla creazione di attività e all'interno di un'attività:Adding the SendAndReceiveReply template does three things oltre a creare le attività e all'interno di un'attività:Adding <xref:System.Activities.Statements.Sequence> the **SendAndReceiveReply** template does three things oltre a

- Configura le <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> proprietà e <xref:System.ServiceModel.Activities.Send> dell'attività.

- Associazione della proprietà <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.ReceiveReply> all'attività <xref:System.ServiceModel.Activities.Send>.

- Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="use-the-sendandreceivereply-template-designer"></a>Utilizzare la finestra di progettazione di modelli SendAndReceiveReplyUse the SendAndReceiveReply Template Designer

Accedere all'ActivityDesigner **SendAndReceiveReply** nella categoria **Messaggistica** della **Casella degli strumenti**. Il **SendAndReceiveReply** ActivityDesigner può essere trascinato dalla **casella degli strumenti** e rilasciato nell'area di progettazione del flusso di lavoro in cui vengono in genere inserite le attività. L'eliminazione <xref:System.ServiceModel.Activities.Send> dell'ActivityDesigner crea un'attività che può essere configurata con l'ActivityDesigner Send e una correlazione che può essere configurata con la finestra di progettazione **ReceiveReplyForSend.Dropping** the activity designer creates a activity that can be configured with the **Send** activity designer and a correlated <xref:System.ServiceModel.Activities.ReceiveReply> that can be configured with the ReceiveReplyForSend designer.

Per ulteriori informazioni **Send** sull'utilizzo di <xref:System.ServiceModel.Activities.Send> Invia finestra di progettazione per configurare l'attività, vedere [Invia](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Proprietà di ReceiveReply

Nella tabella seguente <xref:System.ServiceModel.Activities.ReceiveReply> vengono illustrate le proprietà e viene descritto come vengono utilizzate nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area di Progettazione flussi di lavoro.

| Nome proprietà | Obbligatoria | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.ReceiveReply>. L'impostazione predefinita è ReceiveReplyForSend.<br /><br /> Anche se l'uso di un <xref:System.Activities.Activity.DisplayName%2A> valore non predefinito per il amichevole non è strettamente richiesto, è meglio usare tale valore. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Riferimento all'attività <xref:System.ServiceModel.Activities.Send> correlata a questa attività <xref:System.ServiceModel.Activities.ReceiveReply>. Questa proprietà non deve essere **null.** <xref:System.ServiceModel.Activities.Send>e <xref:System.ServiceModel.Activities.ReceiveReply> le attività vengono utilizzate insieme sul client per modellare un modello di messaggistica richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione non è possibile modificare questa <xref:System.ServiceModel.Activities.Send> proprietà perché è <xref:System.ServiceModel.Activities.ReceiveReply> associata automaticamente all'attività da cui è stata creata l'attività. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà facendo clic sul pulsante con i segusini accanto al **contenuto** campo nella griglia delle proprietà o facendo clic sul **Definisci** pulsante accanto al **contenuto** etichetta nell'area dell'ActivityDesigner **ricezione.** Entrambi visualizzano la finestra di dialogo **Definizione contenuto.** Per ulteriori informazioni sull'utilizzo di questa casella, vedere Finestra di [dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> i coniatori a i solcanto risciacqua accanto alla proprietà nella griglia delle proprietà per aprire la finestra di dialogo **Aggiungi inizializzatori di correlazione.** Per ulteriori informazioni sull'utilizzo di questa casella, vedere Finestra di [dialogo Aggiungi CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Specifica l'intestazione Action del messaggio. Se non è impostato in modo esplicito, il valore predefinito è:If it's not explicitly set, its value defaults to:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Vedere anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)