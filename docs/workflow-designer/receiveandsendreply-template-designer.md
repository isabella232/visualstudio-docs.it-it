---
title: Finestra di progettazione del flusso di lavoro - finestra di progettazione modello ReceiveAndSendReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 657e14d968496c895f24038ca2db1e7f62846b75
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950201"
---
# <a name="receiveandsendreply-template-designer"></a>Finestra di progettazione del modello ReceiveAndSendReply

Il **ReceiveAndSendReply** modello viene utilizzato per creare una coppia di preconfigurati <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> attività. Le attività fanno parte di un <xref:System.Activities.Statements.Sequence> attività e sono correlati come parte di un modello di scambio di messaggi di richiesta/risposta sul server.

## <a name="the-receiveandsendreply-template"></a>Modello ReceiveAndSendReply

Aggiunta di un **ReceiveAndSendReply** modello effettua tre operazioni oltre alla creazione i <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> attività con un <xref:System.Activities.Statements.Sequence> attività:

- Consente di configurare il <xref:System.ServiceModel.Activities.Receive.OperationName%2A> e <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> delle proprietà del <xref:System.ServiceModel.Activities.Receive> attività.

- Associazione della proprietà <xref:System.ServiceModel.Activities.SendReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.Receive> all'attività <xref:System.ServiceModel.Activities.Send>.

- Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="use-the-receiveandsendreply-template-designer"></a>Usare la progettazione del modello ReceiveAndSendReply

Accesso di **ReceiveAndSendReply** ActivityDesigner nel **messaggistica** categoria del **della casella degli strumenti**. Il **ReceiveAndSendReply** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che vengono in genere posizionate le attività. La finestra di progettazione di attività di rilascio crea un <xref:System.ServiceModel.Activities.Receive> attività che può essere configurato con il **inviare** ActivityDesigner e un correlato <xref:System.ServiceModel.Activities.SendReply> che può essere configurato con la finestra di progettazione SendReplyToReceive.

Per altre informazioni sull'uso il **Receive** finestra di progettazione per configurare il <xref:System.ServiceModel.Activities.Receive> attività, vedere [ricezione ActivityDesigner](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Proprietà di SendReply

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.SendReply> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area di progettazione del flusso di lavoro.


| Nome proprietà | Obbligatorio | Utilizzo |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.SendReply>. Il valore predefinito è SendReplyToReceive.<br /><br /> Sebbene l'uso di un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A> non è strettamente necessaria, è consigliabile utilizzare tale valore. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Riferimento all'attività <xref:System.ServiceModel.Activities.Receive> correlata a questa attività <xref:System.ServiceModel.Activities.SendReply>. Questa proprietà non deve essere **null**. Le attività <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> sono usate insieme sul server per modellare un modello di messaggistica di richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione, è possibile modificare questa proprietà perché viene associata automaticamente per il <xref:System.ServiceModel.Activities.Send> attività da cui è stato creato il <xref:System.ServiceModel.Activities.SendReply> attività. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà facendo clic sul pulsante con puntini di sospensione accanto al **contenuti** campo nella griglia delle proprietà oppure facendo clic la **Definisci** accanto al **contenuto** etichetta sul  **Ricezione** superficie dell'ActivityDesigner. Entrambi visualizzano la **definizione del contenuto** finestra di dialogo. Per altre informazioni su come usare questa casella, vedere la [finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) argomento. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sui puntini di sospensione accanto al <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> proprietà nella griglia delle proprietà per aprire la **Aggiungi inizializzatori di correlazione** nella finestra di dialogo. Per altre informazioni sull'uso di questa casella, vedere la [finestra di dialogo Aggiungi inizializzatori di correlazione](../workflow-designer/add-correlationinitializers-dialog-box.md) argomento. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Specifica l'intestazione Action del messaggio. Se viene impostata in modo non esplicito, assume il valore predefinito per:<br /><br /> <strong>https://tempuri.org/{service spazio dei nomi del contratto} / {nome del contratto di servizio} / {nome dell'operazione}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Specifica se l'istanza di servizio del flusso di lavoro deve essere salvata in modo permanente prima di inviare il messaggio di risposta. Il valore predefinito è **false**. |

## <a name="see-also"></a>Vedere anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)