---
title: Progettazione flussi di lavoro - ReceiveAndSendReply Progettazione modelli
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 042032efe745a9cb38bbf4e362cb5ad8440129ba
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395291"
---
# <a name="receiveandsendreply-template-designer"></a>Finestra di progettazione del modello ReceiveAndSendReply

Il **receiveAndSendReply** modello viene utilizzato per creare <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> una coppia di preconfigurato e attività. Le attività fanno <xref:System.Activities.Statements.Sequence> parte di un'attività e sono correlate come parte di un modello di scambio di messaggi di richiesta/risposta sul server.

## <a name="the-receiveandsendreply-template"></a>Il modello ReceiveAndSendReplyThe ReceiveAndSendReply template

L'aggiunta di un modello ReceiveAndSendReply <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> esegue tre <xref:System.Activities.Statements.Sequence> operazioni oltre a creare le attività e con un'attività:Adding a ReceiveAndSendReply template does three things oltre a creare le attività e con un'attività:Adding a **ReceiveAndSendReply** template does three things oltre a creare le attività e con

- Configura le <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> proprietà e <xref:System.ServiceModel.Activities.Receive> dell'attività.

- Associazione della proprietà <xref:System.ServiceModel.Activities.SendReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.Receive> all'attività <xref:System.ServiceModel.Activities.Send>.

- Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="use-the-receiveandsendreply-template-designer"></a>Usare la finestra di progettazione del modello ReceiveAndSendReplyUse the ReceiveAndSendReply template designer

Accedere all'ActivityDesigner **ReceiveAndSendReply** nella categoria **Messaggistica** della **Casella degli strumenti**. Il **ReceiveAndSendReply** ActivityDesigner può essere trascinato dalla **casella degli strumenti** e rilasciato nell'area di progettazione del flusso di lavoro in cui vengono in genere inserite le attività. L'eliminazione dell'ActivityDesigner crea un'attività <xref:System.ServiceModel.Activities.Receive> che può essere configurata con l'ActivityDesigner Send e una correlazione con la finestra di progettazione SendReplyToReceive.Dropping the activity designer creates a activity that can be configured with the **Send** activity designer and a correlated <xref:System.ServiceModel.Activities.SendReply> that can be configured with the SendReplyToReceive designer.

Per ulteriori informazioni **Receive** sull'utilizzo di <xref:System.ServiceModel.Activities.Receive> Receive Designer per configurare l'attività, vedere [Receive Activity Designer](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Proprietà di SendReply

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.SendReply> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area di Progettazione flussi di lavoro.

| Nome proprietà | Obbligatoria | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.SendReply>. Il valore predefinito è SendReplyToReceive.<br /><br /> Anche se l'uso di un <xref:System.Activities.Activity.DisplayName%2A> valore non predefinito per il amichevole non è strettamente richiesto, è meglio usare tale valore. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Riferimento all'attività <xref:System.ServiceModel.Activities.Receive> correlata a questa attività <xref:System.ServiceModel.Activities.SendReply>. Questa proprietà non deve essere **null.** <xref:System.ServiceModel.Activities.Receive>e <xref:System.ServiceModel.Activities.SendReply> le attività vengono utilizzate insieme sul server per modellare un modello di messaggistica di richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione non è possibile modificare questa <xref:System.ServiceModel.Activities.Send> proprietà perché è <xref:System.ServiceModel.Activities.SendReply> associata automaticamente all'attività da cui è stata creata l'attività. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà facendo clic sul pulsante con i segusini accanto al **contenuto** campo nella griglia delle proprietà o facendo clic sul **Definisci** pulsante accanto al **contenuto** etichetta nell'area dell'ActivityDesigner **ricezione.** Entrambi visualizzano la finestra di dialogo **Definizione contenuto.** Per altre informazioni su come usare questa casella, vedere l'argomento Finestra di [dialogo Definizione contenuto.](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> i coniatori a i solcanto risciacqua accanto alla proprietà nella griglia delle proprietà per aprire la finestra di dialogo **Aggiungi inizializzatori di correlazione.** Per altre informazioni sull'uso di questa casella, vedere l'argomento Finestra di [dialogo Aggiungi CorrelationInitializers.For](../workflow-designer/add-correlationinitializers-dialog-box.md) more information about using this box, see the Add CorrelationInitializers Dialog Box topic. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Specifica l'intestazione Action del messaggio. Se non è impostato in modo esplicito, il valore predefinito è:If it's not explicitly set, its value defaults to:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Specifica se l'istanza di servizio del flusso di lavoro deve essere salvata in modo permanente prima di inviare il messaggio di risposta. Il valore predefinito è **false**. |

## <a name="see-also"></a>Vedere anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)