---
title: ActivityDesigner Progettazione flussi di lavoro-Receive
description: Informazioni sull'attività Receive e su come usare l'ActivityDesigner Receive per creare e configurare un'attività Receive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6414d92cea867a1235d73a39b6415ab884651ec
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434194"
---
# <a name="receive-activity-designer"></a>ActivityDesigner Receive

L'ActivityDesigner **Receive** viene utilizzato per creare e configurare un' <xref:System.ServiceModel.Activities.Receive> attività. Un'attività <xref:System.ServiceModel.Activities.Receive> è un'attività che riceve un messaggio che può essere un tipo incorporato, quale <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> o <xref:System.Xml.Linq.XElement>, o una classe XML, un contratto dati o un contratto di messaggio serializzabile definito dall'applicazione.

## <a name="the-receive-activity"></a>Attività Receive

L'attività <xref:System.ServiceModel.Activities.Receive> può ricevere un solo elemento o più elementi a seconda del tipo di contenuto di ricezione usato. È possibile associare un'attività <xref:System.ServiceModel.Activities.SendReply> a un'attività <xref:System.ServiceModel.Activities.Receive> che riceve un messaggio come parte di un modello di scambio di messaggi di richiesta/risposta nel servizio.

### <a name="using-the-receive-activity-designer"></a>Utilizzo dell'ActivityDesigner Receive

Accedere all'ActivityDesigner **Receive** nella categoria **messaggistica** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **Receive** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando le attività vengono in genere posizionate. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **Receive** o nella casella **DisplayName** della griglia delle proprietà.

Per creare un' <xref:System.ServiceModel.Activities.SendReply> attività e associarla all'attività selezionata <xref:System.ServiceModel.Activities.Receive> , fare clic con il pulsante destro del mouse sull'ActivityDesigner **Receive** , scegliere l'elemento **Crea SendReply** dal menu di scelta rapida e **SendReplyToReceive** Designer viene visualizzato sotto la finestra di progettazione **ricezione** . L'attività <xref:System.ServiceModel.Activities.SendReply> è un'attività che invia il messaggio di risposta come parte di un modello di scambio di messaggi di richiesta/risposta nel servizio. Può essere configurato con **SendReplyToReceive** designer.

In alternativa, è possibile usare la finestra di progettazione del modello **ReceiveAndSendReply** nella categoria **messaggistica** della **casella degli strumenti** per creare una coppia di <xref:System.ServiceModel.Activities.Receive> attività e preconfigurate <xref:System.ServiceModel.Activities.SendReply> . Per ulteriori informazioni sull'utilizzo del modello **ReceiveAndSendReply** e **SendReplyToReceive** , vedere l'argomento [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) .

### <a name="the-receive-activity-properties"></a>Proprietà dell'attività Receive

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.Receive> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà o nell'area di Progettazione flussi di lavoro. L'unica proprietà obbligatoria è la proprietà <xref:System.ServiceModel.Activities.Receive.OperationName%2A>.

| Nome proprietà | Obbligatoria | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | Specifica il nome descrittivo dell'attività <xref:System.ServiceModel.Activities.Receive>. Il valore predefinito è Receive.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | Vero | Specifica il nome dell'operazione del servizio implementata da questa attività <xref:System.ServiceModel.Activities.Receive>. Questa proprietà viene utilizzata per costruire il valore predefinito per la proprietà **Action** se la proprietà **Action** non è impostata in modo esplicito. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | Falso | Specifica il nome del contratto di servizio. Questa proprietà viene usata per raggruppare operazioni del servizio in contratti di servizio singoli. Tutte le attività <xref:System.ServiceModel.Activities.Receive> con lo stesso <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> vengono raggruppate nello stesso contratto di servizio (tipo di porta WSDL). Il valore predefinito è il nome CLR completo dell'attività di livello superiore (radice). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | Falso | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà selezionando il pulsante con i puntini di sospensione accanto al campo **contenuto** nella griglia delle proprietà o facendo clic sul pulsante **Definisci...** accanto all'etichetta **contenuto** nell'area di progettazione dell'attività di **ricezione** . Entrambi visualizzano la finestra di dialogo **Definizione contenuto** . Per ulteriori informazioni sull'utilizzo di questa casella, vedere l'argomento relativo alla finestra di [dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | Falso | Specifica le correlazioni tra le attività <xref:System.ServiceModel.Activities.Receive> nelle operazioni del servizio di un flusso di lavoro con un oggetto <xref:System.ServiceModel.MessageQuerySet>. Fare clic sul pulsante con i puntini di sospensione accanto alla <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> proprietà nella griglia proprietà per aprire la finestra di dialogo **definizione CorrelatesOn** . Per ulteriori informazioni sull'utilizzo di questa finestra di dialogo, vedere l'argomento relativo alla finestra di [dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | Falso | Specifica l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per indirizzare il messaggio all'istanza del flusso di lavoro appropriata.<br /><br /> Fare clic sul pulsante con i puntini di sospensione accanto alla <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> proprietà nella griglia proprietà per aprire la finestra di dialogo **Editor espressioni** . Per ulteriori informazioni sull'utilizzo di questa finestra di dialogo, vedere l'argomento [procedura: utilizzare l'editor di espressioni](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | Falso | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con i puntini di sospensione accanto alla <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> proprietà nella griglia proprietà per aprire la finestra di dialogo **Aggiungi inizializzatori di correlazione** . Per ulteriori informazioni sull'utilizzo di questa casella, vedere l'argomento relativo alla finestra di [dialogo Aggiungi CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | Falso | Specifica un valore che determina se viene creata una nuova istanza del flusso di lavoro per elaborare il messaggio se quest'ultimo non è correlato a un'istanza del flusso di lavoro esistente. Se il valore è impostato su **true** , viene creata una nuova istanza del flusso di lavoro per elaborare il messaggio quando il messaggio non è correlato a un'istanza del flusso di lavoro esistente. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | Falso | Specifica una raccolta di tipi noti per l'operazione del servizio implementata da questa attività <xref:System.ServiceModel.Activities.Receive>. Questa proprietà deve essere usata insieme alla proprietà <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> impostata su <xref:System.Runtime.Serialization.DataContractSerializer>. Viene ignorata se viene usato <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Selezionare il pulsante con i puntini di sospensione accanto al campo **knownTypes** nella griglia delle proprietà per visualizzare la finestra di dialogo **Editor raccolta** di tipi con cui è possibile aggiungere tipi rilevanti. Per ulteriori informazioni sull'utilizzo di questa casella, vedere l'argomento della finestra di [dialogo Editor raccolta di tipi](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | Falso | Specifica il tipo di <xref:System.Net.Security.ProtectionLevel> applicato al messaggio.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> indica solo l'autenticazione.<br />2.  <xref:System.Net.Security.ProtectionLevel> indica i dati del segno che consentono di garantire l'integrità dei dati trasmessi.<br />3.  <xref:System.Net.Security.ProtectionLevel> significa crittografare e firmare i dati per garantire la riservatezza e l'integrità dei dati trasmessi. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | Falso | Specifica il tipo di serializzatore da usare per l'operazione del servizio implementata dall'attività <xref:System.ServiceModel.Activities.Receive>. Il valore predefinito è <xref:System.Runtime.Serialization.DataContractSerializer>, che serializza e deserializza un'istanza di un tipo in un documento o un flusso XML che usa un contratto dati fornito. È inoltre possibile usare <xref:System.Xml.Serialization.XmlSerializer> se è richiesto un maggiore controllo sul codice XML. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | Falso | Specifica l'intestazione Action del messaggio. Se non è impostata in modo esplicito, il valore predefinito è: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . |

## <a name="see-also"></a>Vedere anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
