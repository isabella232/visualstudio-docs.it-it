---
title: Finestra di progettazione del flusso di lavoro - finestra di progettazione modello SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6731f91544235c3011e458aea7c4c5b90f89908
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907555"
---
# <a name="sendandreceivereply-template-designer"></a>Finestra di progettazione del modello SendAndReceiveReply

Il **SendAndReceiveReply** modello viene utilizzato per creare una coppia di preconfigurati <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> attività. Le attività fanno parte di un <xref:System.Activities.Statements.Sequence> attività e sono correlati come parte di un modello di scambio di messaggi di richiesta/risposta sul client.

## <a name="the-sendandreceivereply-template"></a>Modello SendAndReceiveReply

Aggiunta la **SendAndReceiveReply** modello effettua tre operazioni oltre alla creazione di <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> attività all'interno di un <xref:System.Activities.Statements.Sequence> attività:

- Consente di configurare il <xref:System.ServiceModel.Activities.Send.OperationName%2A> e <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> delle proprietà del <xref:System.ServiceModel.Activities.Send> attività.

- Associazione della proprietà <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.ReceiveReply> all'attività <xref:System.ServiceModel.Activities.Send>.

- Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="use-the-sendandreceivereply-template-designer"></a>Utilizzare la finestra di progettazione del modello SendAndReceiveReply

Accesso di **SendAndReceiveReply** ActivityDesigner nel **messaggistica** categoria del **della casella degli strumenti**. Il **SendAndReceiveReply** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che vengono in genere posizionate le attività. La finestra di progettazione di attività di rilascio crea un <xref:System.ServiceModel.Activities.Send> attività che può essere configurato con il **inviare** ActivityDesigner e un correlati <xref:System.ServiceModel.Activities.ReceiveReply> che può essere configurato con il **ReceiveReplyForSend** finestra di progettazione.

Per altre informazioni sull'uso di **inviare** finestra di progettazione per configurare il <xref:System.ServiceModel.Activities.Send> attività, vedere [inviare](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Proprietà di ReceiveReply

La tabella seguente illustra il <xref:System.ServiceModel.Activities.ReceiveReply> proprietà e viene descritto l'utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area di progettazione del flusso di lavoro.


| Nome proprietà | Obbligatorio | Utilizzo |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.ReceiveReply>. L'impostazione predefinita è ReceiveReplyForSend.<br /><br /> Sebbene l'uso di un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A> non è strettamente necessaria, è consigliabile utilizzare tale valore. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Riferimento all'attività <xref:System.ServiceModel.Activities.Send> correlata a questa attività <xref:System.ServiceModel.Activities.ReceiveReply>. Questa proprietà non deve essere **null**. Le attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> sono usate insieme al client per modellare un modello di messaggistica di richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione, è possibile modificare questa proprietà perché viene associata automaticamente per il <xref:System.ServiceModel.Activities.Send> attività da cui è stato creato il <xref:System.ServiceModel.Activities.ReceiveReply> attività. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà facendo clic sul pulsante con puntini di sospensione accanto al **contenuto** campo nella griglia delle proprietà oppure facendo il **Definisci** accanto al **contenuto** etichetta nel **Ricezione** superficie dell'ActivityDesigner. Entrambi visualizzano la **definizione del contenuto** finestra di dialogo. Per altre informazioni su come usare questa casella, vedere [finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sui puntini di sospensione accanto al <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> proprietà nella griglia delle proprietà per aprire la **Aggiungi inizializzatori di correlazione** nella finestra di dialogo. Per altre informazioni sull'uso di questa casella, vedere [finestra di dialogo Aggiungi inizializzatori di correlazione](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Specifica l'intestazione Action del messaggio. Se viene impostata in modo non esplicito, assume il valore predefinito per:<br /><br /> <strong>https://tempuri.org/{service spazio dei nomi del contratto} / {nome del contratto di servizio} / {nome dell'operazione}.</strong> |

## <a name="see-also"></a>Vedere anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)