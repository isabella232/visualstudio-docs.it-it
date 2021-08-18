---
title: Finestra di progettazione del modello ReceiveAndSendReply
description: Informazioni su come usare il modello ReceiveAndSendReply in Progettazione flussi di lavoro creare una coppia di attività Receive e SendReply preconfigurato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: ba89478dcbc69104c89788708afe32e338ef7071
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135299"
---
# <a name="receiveandsendreply-template-designer"></a>Finestra di progettazione del modello ReceiveAndSendReply

Il **modello ReceiveAndSendReply** viene usato per creare una coppia di attività e preconfigurato. <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> Le attività fanno parte di un'attività e sono correlate come parte di un modello di scambio di messaggi di <xref:System.Activities.Statements.Sequence> richiesta/risposta nel server.

## <a name="the-receiveandsendreply-template"></a>Modello ReceiveAndSendReply

**L'aggiunta di un modello ReceiveAndSendReply** esegue tre operazioni oltre alla creazione delle attività e con <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> <xref:System.Activities.Statements.Sequence> un'attività:

- Configura le proprietà <xref:System.ServiceModel.Activities.Receive.OperationName%2A> e <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> <xref:System.ServiceModel.Activities.Receive> dell'attività.

- Associazione della proprietà <xref:System.ServiceModel.Activities.SendReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.Receive> all'attività <xref:System.ServiceModel.Activities.Send>.

- Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="use-the-receiveandsendreply-template-designer"></a>Usare la finestra di progettazione modelli ReceiveAndSendReply

Accedere **all'ActivityDesigner ReceiveAndSendReply** nella **categoria Messaggistica** della Casella **degli strumenti**. L'ActivityDesigner **ReceiveAndSendReply** può essere  trascinato dalla casella degli strumenti e rilasciato nell'area di Progettazione flussi di lavoro in cui vengono in genere posizionate le attività. L'eliminazione dell'ActivityDesigner crea un'attività che può essere configurata con l'ActivityDesigner di invio e un elemento correlato che può essere configurato con la finestra di progettazione <xref:System.ServiceModel.Activities.Receive>  <xref:System.ServiceModel.Activities.SendReply> SendReplyToReceive.

Per altre informazioni sull'uso della **finestra di** progettazione di ricezione per configurare <xref:System.ServiceModel.Activities.Receive> l'attività, vedere Receive [ActivityDesigner](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Proprietà di SendReply

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.SendReply> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nella Progettazione flussi di lavoro superficie.

| Nome proprietà | Obbligatoria | Utilizzo |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.SendReply>. Il valore predefinito è SendReplyToReceive.<br /><br /> Anche se l'uso di un valore non predefinito per il tipo descrittivo non è strettamente necessario, è meglio <xref:System.Activities.Activity.DisplayName%2A> usare tale valore. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | Vero | Riferimento all'attività <xref:System.ServiceModel.Activities.Receive> correlata a questa attività <xref:System.ServiceModel.Activities.SendReply>. Questa proprietà non deve essere **Null.** <xref:System.ServiceModel.Activities.Receive> le <xref:System.ServiceModel.Activities.SendReply> attività e vengono usate insieme nel server per modellare un modello di messaggistica di richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione non è possibile modificare questa proprietà perché è associata automaticamente <xref:System.ServiceModel.Activities.Send> all'attività da cui è stata creata l'attività. <xref:System.ServiceModel.Activities.SendReply> |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | Falso | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà facendo clic sul pulsante con i puntini di sospensione  accanto al  campo **Contenuto** nella griglia delle proprietà oppure facendo clic sul pulsante Definisci accanto all'etichetta Contenuto nell'area **di** ActivityDesigner ricezione. Entrambi visualizzano la **finestra di dialogo Definizione** contenuto. Per altre informazioni su come usare questa casella, vedere l'argomento [Finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | Falso | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con i puntini di sospensione accanto alla proprietà nella griglia delle proprietà per aprire la finestra di dialogo Aggiungi <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> **inizializzatori** di correlazione . Per altre informazioni sull'uso di questa casella, vedere [l'argomento Aggiungi correlationInitializers Dialog Box.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | Falso | Specifica l'intestazione Action del messaggio. Se non è impostato in modo esplicito, il valore predefinito è:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | Falso | Specifica se l'istanza di servizio del flusso di lavoro deve essere salvata in modo permanente prima di inviare il messaggio di risposta. Il valore predefinito è **false**. |

## <a name="see-also"></a>Vedi anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)