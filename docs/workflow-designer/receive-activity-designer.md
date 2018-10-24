---
title: 'Activity Designer Receive di progettazione del flusso di lavoro:'
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb48c19befc3cf2c155248cfc33c01eedd16ce26
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950095"
---
# <a name="receive-activity-designer"></a>ActivityDesigner Receive

Il **Receive** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.ServiceModel.Activities.Receive> attività. Un'attività <xref:System.ServiceModel.Activities.Receive> è un'attività che riceve un messaggio che può essere un tipo incorporato, quale <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> o <xref:System.Xml.Linq.XElement>, o una classe XML, un contratto dati o un contratto di messaggio serializzabile definito dall'applicazione.

## <a name="the-receive-activity"></a>Attività Receive

L'attività <xref:System.ServiceModel.Activities.Receive> può ricevere un solo elemento o più elementi a seconda del tipo di contenuto di ricezione usato. È possibile associare un'attività <xref:System.ServiceModel.Activities.SendReply> a un'attività <xref:System.ServiceModel.Activities.Receive> che riceve un messaggio come parte di un modello di scambio di messaggi di richiesta/risposta nel servizio.

### <a name="using-the-receive-activity-designer"></a>Utilizzo dell'ActivityDesigner Receive

Accesso di **Receive** ActivityDesigner nel **messaggistica** categoria del **della casella degli strumenti**. Il **Receive** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che vengono in genere posizionate le attività. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **Receive** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.

Per creare un <xref:System.ServiceModel.Activities.SendReply> attività e lo associerà al <xref:System.ServiceModel.Activities.Receive> attività, fare doppio clic sui **ricezione** fare clic su progettazione, attività il **crea SendReply** elemento nel menu di scelta rapida e il **SendReplyToReceive** verrà visualizzata sotto il **ricezione** finestra di progettazione. L'attività <xref:System.ServiceModel.Activities.SendReply> è un'attività che invia il messaggio di risposta come parte di un modello di scambio di messaggi di richiesta/risposta nel servizio. Può essere configurato con il **SendReplyToReceive** finestra di progettazione.

In alternativa, il **ReceiveAndSendReply** Progettazione modelli nel **messaggistica** categoria del **della casella degli strumenti** utilizzabile per creare una coppia di preconfigurati <xref:System.ServiceModel.Activities.Receive>e <xref:System.ServiceModel.Activities.SendReply> attività. Per altre informazioni sull'uso del **ReceiveAndSendReply** e **SendReplyToReceive** modello, vedere il [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) argomento.

### <a name="the-receive-activity-properties"></a>Proprietà dell'attività Receive

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.Receive> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area di progettazione del flusso di lavoro. L'unica proprietà obbligatoria è la proprietà <xref:System.ServiceModel.Activities.Receive.OperationName%2A>.


| Nome proprietà | Obbligatorio | Utilizzo |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Specifica il nome descrittivo dell'attività <xref:System.ServiceModel.Activities.Receive>. Il valore predefinito è Receive.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | True | Specifica il nome dell'operazione del servizio implementata da questa attività <xref:System.ServiceModel.Activities.Receive>. Questa proprietà viene utilizzata per costruire il valore predefinito per il **azione** proprietà se il **azione** proprietà non è impostata in modo esplicito. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | False | Specifica il nome del contratto di servizio. Questa proprietà viene usata per raggruppare operazioni del servizio in contratti di servizio singoli. Tutte le attività <xref:System.ServiceModel.Activities.Receive> con lo stesso <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> vengono raggruppate nello stesso contratto di servizio (tipo di porta WSDL). Il valore predefinito è il nome completo CLR dell'attività di primo livello (radice). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | False | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà facendo clic sul pulsante con puntini di sospensione accanto al **contenuto** campo nella griglia delle proprietà oppure facendo clic di **definire...**  accanto al **contenuti** assegnare un'etichetta nel **ricezione** superficie dell'ActivityDesigner. Entrambi visualizzano la **definizione del contenuto** finestra di dialogo. Per altre informazioni su come usare questa casella, vedere la [finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) argomento. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | False | Specifica le correlazioni tra le attività <xref:System.ServiceModel.Activities.Receive> nelle operazioni del servizio di un flusso di lavoro con un oggetto <xref:System.ServiceModel.MessageQuerySet>. Fare clic sui puntini di sospensione accanto al <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> proprietà nella griglia delle proprietà per aprire la **definizione di CorrelatesOn** nella finestra di dialogo. Per altre informazioni sull'uso della finestra di dialogo, vedere la [finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) argomento. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | False | Specifica l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per indirizzare il messaggio all'istanza del flusso di lavoro appropriata.<br /><br /> Fare clic sui puntini di sospensione accanto al <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> proprietà nella griglia delle proprietà per aprire la **Editor espressioni** nella finestra di dialogo. Per altre informazioni sull'uso della finestra di dialogo, vedere la [procedura: utilizzare l'Editor espressioni](../workflow-designer/how-to-use-the-expression-editor.md) argomento. |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | False | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sui puntini di sospensione accanto al <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> proprietà nella griglia delle proprietà per aprire la **Aggiungi inizializzatori di correlazione** nella finestra di dialogo. Per altre informazioni sull'uso di questa casella, vedere la [finestra di dialogo Aggiungi inizializzatori di correlazione](../workflow-designer/add-correlationinitializers-dialog-box.md) argomento. |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | False | Specifica un valore che determina se viene creata una nuova istanza del flusso di lavoro per elaborare il messaggio se quest'ultimo non è correlato a un'istanza del flusso di lavoro esistente. Se il valore è impostato su **true**, viene creata una nuova istanza di flusso di lavoro per elaborare il messaggio quando il messaggio non sia correlato a un'istanza del flusso di lavoro esistente. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | False | Specifica una raccolta di tipi noti per l'operazione del servizio implementata da questa attività <xref:System.ServiceModel.Activities.Receive>. Questa proprietà deve essere usata insieme alla proprietà <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> impostata su <xref:System.Runtime.Serialization.DataContractSerializer>. Viene ignorata se viene usato <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Selezionare il pulsante con puntini di sospensione accanto ad il **KnownTypes** campo nella griglia delle proprietà per visualizzare i **Editor raccolta di tipi** finestra di dialogo in cui è possibile aggiungere i tipi appropriati. Per altre informazioni sull'uso di questa casella, vedere la [finestra di dialogo Editor raccolta di tipo](../workflow-designer/type-collection-editor-dialog-box.md) argomento. |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | False | Specifica il tipo di <xref:System.Net.Security.ProtectionLevel> applicato al messaggio.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> indica solo l'autenticazione.<br />2. <xref:System.Net.Security.ProtectionLevel> significa firma i dati al fine di garantire l'integrità dei dati trasmessi.<br />3. <xref:System.Net.Security.ProtectionLevel> significa crittografare e firmare i dati per garantire la riservatezza e integrità dei dati trasmessi. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | False | Specifica il tipo di serializzatore da usare per l'operazione del servizio implementata dall'attività <xref:System.ServiceModel.Activities.Receive>. Il valore predefinito è <xref:System.Runtime.Serialization.DataContractSerializer>, che serializza e deserializza un'istanza di un tipo in un documento o un flusso XML che usa un contratto dati fornito. È inoltre possibile usare <xref:System.Xml.Serialization.XmlSerializer> se è richiesto un maggiore controllo sul codice XML. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | False | Specifica l'intestazione Action del messaggio. Se non è esplicitamente impostata, il valore predefinito è: https://tempuri.org/{service dello spazio dei nomi del contratto} / {nome del contratto di servizio} / {nome dell'operazione}. |

## <a name="see-also"></a>Vedere anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)