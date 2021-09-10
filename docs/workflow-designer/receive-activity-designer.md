---
title: Progettazione flussi di lavoro - Ricevere ActivityDesigner
description: Informazioni sull'attività Receive e su come usare l'ActivityDesigner receive per creare e configurare un'attività Receive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 1319dcbdbbefe6639fe6d52b4dfb5c5d5015ad22
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963223"
---
# <a name="receive-activity-designer"></a>ActivityDesigner Receive

**L'ActivityDesigner** di ricezione viene usato per creare e configurare un'attività. <xref:System.ServiceModel.Activities.Receive> Un'attività <xref:System.ServiceModel.Activities.Receive> è un'attività che riceve un messaggio che può essere un tipo incorporato, quale <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> o <xref:System.Xml.Linq.XElement>, o una classe XML, un contratto dati o un contratto di messaggio serializzabile definito dall'applicazione.

## <a name="the-receive-activity"></a>Attività Receive

L'attività <xref:System.ServiceModel.Activities.Receive> può ricevere un solo elemento o più elementi a seconda del tipo di contenuto di ricezione usato. È possibile associare un'attività <xref:System.ServiceModel.Activities.SendReply> a un'attività <xref:System.ServiceModel.Activities.Receive> che riceve un messaggio come parte di un modello di scambio di messaggi di richiesta/risposta nel servizio.

### <a name="using-the-receive-activity-designer"></a>Utilizzo dell'ActivityDesigner Receive

Accedere **all'ActivityDesigner** di ricezione nella **categoria Messaggistica** della Casella **degli strumenti**. **L'ActivityDesigner** di ricezione può  essere trascinato dalla casella degli strumenti e rilasciato nella Progettazione flussi di lavoro in cui vengono in genere posizionate le attività. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. <xref:System.Activities.Activity.DisplayName%2A>L'oggetto può essere modificato  nell'intestazione dell'ActivityDesigner di ricezione o nella **casella DisplayName** della griglia delle proprietà.

Per creare un'attività e associarla all'attività selezionata, fare clic con il pulsante destro del mouse sull'ActivityDesigner di ricezione, scegliere l'elemento Create SendReply nel menu di scelta rapida e la finestra di progettazione <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Receive> **SendReplyToReceive**    viene visualizzata sotto la finestra di progettazione ricezione. L'attività <xref:System.ServiceModel.Activities.SendReply> è un'attività che invia il messaggio di risposta come parte di un modello di scambio di messaggi di richiesta/risposta nel servizio. Può essere configurato con la finestra **di progettazione SendReplyToReceive.**

In alternativa, è possibile usare la finestra  di progettazione  dei modelli **ReceiveAndSendReply** nella categoria Messaggistica della casella degli strumenti per creare una coppia di attività e <xref:System.ServiceModel.Activities.Receive> preconfigurato. <xref:System.ServiceModel.Activities.SendReply> Per altre informazioni sull'uso del modello **ReceiveAndSendReply** e **SendReplyToReceive,** vedere l'argomento [ReceiveAndSendReply.](../workflow-designer/receiveandsendreply-template-designer.md)

### <a name="the-receive-activity-properties"></a>Proprietà dell'attività Receive

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.Receive> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà o nella Progettazione flussi di lavoro superficie. L'unica proprietà obbligatoria è la proprietà <xref:System.ServiceModel.Activities.Receive.OperationName%2A>.

| Nome proprietà | Obbligatoria | Utilizzo |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | Specifica il nome descrittivo dell'attività <xref:System.ServiceModel.Activities.Receive>. Il valore predefinito è Receive.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | Vero | Specifica il nome dell'operazione del servizio implementata da questa attività <xref:System.ServiceModel.Activities.Receive>. Questa proprietà viene usata per costruire il valore predefinito per la **proprietà Action** se la **proprietà Action** non è impostata in modo esplicito. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | Falso | Specifica il nome del contratto di servizio. Questa proprietà viene usata per raggruppare operazioni del servizio in contratti di servizio singoli. Tutte le attività <xref:System.ServiceModel.Activities.Receive> con lo stesso <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> vengono raggruppate nello stesso contratto di servizio (tipo di porta WSDL). Il valore predefinito è il nome CLR completo dell'attività di primo livello (radice). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | Falso | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà selezionando il pulsante con i puntini di sospensione accanto al campo **Contenuto** nella griglia delle proprietà o facendo clic sul pulsante Definisci **accanto** all'etichetta **Contenuto** nell'area **di** ActivityDesigner ricezione. Entrambi visualizzano la **finestra di dialogo Definizione** contenuto. Per altre informazioni su come usare questa casella, vedere l'argomento [Finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | Falso | Specifica le correlazioni tra le attività <xref:System.ServiceModel.Activities.Receive> nelle operazioni del servizio di un flusso di lavoro con un oggetto <xref:System.ServiceModel.MessageQuerySet>. Fare clic sul pulsante con i puntini di sospensione accanto alla proprietà nella griglia delle proprietà per aprire la finestra di dialogo <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> **Definizione CorrelatesOn** . Per altre informazioni sull'uso di questa finestra di dialogo, vedere l'argomento [Finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | Falso | Specifica l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per indirizzare il messaggio all'istanza del flusso di lavoro appropriata.<br /><br /> Fare clic sul pulsante con i puntini di sospensione accanto alla <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> proprietà nella griglia delle proprietà per aprire la finestra di dialogo **Editor** espressioni . Per altre informazioni sull'uso di questa finestra di dialogo, vedere l'argomento [Procedura: Usare l'editor di](../workflow-designer/how-to-use-the-expression-editor.md) espressioni. |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | Falso | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con i puntini di sospensione accanto alla proprietà nella griglia delle proprietà per aprire la finestra di dialogo Aggiungi <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> **inizializzatori** di correlazione . Per altre informazioni sull'uso di questa casella, vedere [l'argomento Aggiungi correlationInitializers Dialog Box.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | Falso | Specifica un valore che determina se viene creata una nuova istanza del flusso di lavoro per elaborare il messaggio se quest'ultimo non è correlato a un'istanza del flusso di lavoro esistente. Se il valore è impostato su **true**, viene creata una nuova istanza del flusso di lavoro per elaborare il messaggio quando il messaggio non è correlato a un'istanza del flusso di lavoro esistente. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | Falso | Specifica una raccolta di tipi noti per l'operazione del servizio implementata da questa attività <xref:System.ServiceModel.Activities.Receive>. Questa proprietà deve essere usata insieme alla proprietà <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> impostata su <xref:System.Runtime.Serialization.DataContractSerializer>. Viene ignorata se viene usato <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Selezionare il pulsante con i puntini di sospensione accanto al campo **KnownTypes** nella griglia delle proprietà per visualizzare la finestra di dialogo **Editor** raccolta tipi con cui è possibile aggiungere tipi pertinenti. Per altre informazioni sull'uso di questa casella, vedere l'argomento [Finestra di dialogo Editor raccolta tipi](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | Falso | Specifica il tipo di <xref:System.Net.Security.ProtectionLevel> applicato al messaggio.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> indica solo l'autenticazione.<br />2.  <xref:System.Net.Security.ProtectionLevel> significa firmare i dati per garantire l'integrità dei dati trasmessi.<br />3.  <xref:System.Net.Security.ProtectionLevel> significa crittografare e firmare i dati per garantire la riservatezza e l'integrità dei dati trasmessi. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | Falso | Specifica il tipo di serializzatore da usare per l'operazione del servizio implementata dall'attività <xref:System.ServiceModel.Activities.Receive>. Il valore predefinito è <xref:System.Runtime.Serialization.DataContractSerializer>, che serializza e deserializza un'istanza di un tipo in un documento o un flusso XML che usa un contratto dati fornito. È inoltre possibile usare <xref:System.Xml.Serialization.XmlSerializer> se è richiesto un maggiore controllo sul codice XML. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | Falso | Specifica l'intestazione Action del messaggio. Se non è impostato in modo esplicito, il valore predefinito è: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . |

## <a name="see-also"></a>Vedi anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
