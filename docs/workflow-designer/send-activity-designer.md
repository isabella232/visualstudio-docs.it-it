---
title: Finestra di progettazione del flusso di lavoro, ActivityDesigner Send
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 788884590054b29ae31df9c5ba2ca31ac0ea5c49
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954024"
---
# <a name="send-activity-designer"></a>ActivityDesigner Send

Il **inviare** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.ServiceModel.Activities.Send> attività.

## <a name="the-send-activity"></a>Attività Send

 Un'attività <xref:System.ServiceModel.Activities.Send> viene usata per inviare un messaggio a un servizio. È possibile associare un'attività <xref:System.ServiceModel.Activities.ReceiveReply> a un'attività <xref:System.ServiceModel.Activities.Send> che riceve un messaggio come parte di un modello di scambio di messaggi di richiesta/risposta sul client.

### <a name="using-the-send-activity-designer"></a>Utilizzo dell'ActivityDesigner Send

Accesso di **inviare** ActivityDesigner nel **messaggistica** categoria del **della casella degli strumenti**. Il **inviare** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che vengono in genere posizionate le attività. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Send> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Send. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **inviare** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.

Per creare un <xref:System.ServiceModel.Activities.ReceiveReply> attività e lo associerà al <xref:System.ServiceModel.Activities.Send> attività, fare doppio clic sul **inviare** fare clic su progettazione, attività di **crea ReceiveReply** elemento nel menu di scelta rapida e il **ReceiveReplyForSend** verrà visualizzata sotto il **inviare** finestra di progettazione. L'attività <xref:System.ServiceModel.Activities.ReceiveReply> è un'attività che riceve un messaggio come parte di un modello di scambio di messaggi di richiesta/risposta sul client. Può essere configurato con il **ReceiveReplyForSend** finestra di progettazione.

In alternativa, il **SendAndReceiveReply** Progettazione modelli nel **messaggistica** categoria del **della casella degli strumenti** utilizzabile per creare una coppia di preconfigurati <xref:System.ServiceModel.Activities.Send>e <xref:System.ServiceModel.Activities.ReceiveReply> attività. Per altre informazioni sull'uso del **SendAndReceiveReply** e **ReceiveReplyForSend** modelli, vedere il [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) argomento.

### <a name="the-send-activity-properties"></a>Proprietà dell'attività Send

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.Send> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area di progettazione del flusso di lavoro.


| Nome proprietà | Obbligatorio | Utilizzo |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nome descrittivo dell'attività <xref:System.ServiceModel.Activities.Send>. L'impostazione predefinita è Send. Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | Nome dell'operazione del servizio chiamata da questa attività <xref:System.ServiceModel.Activities.Send>. Questa proprietà viene utilizzata per costruire il valore predefinito per il **azione** proprietà se il **azione** proprietà non è impostata in modo esplicito. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | Nome del contratto del servizio implementato dal servizio da chiamare. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà facendo clic sul pulsante con puntini di sospensione accanto al **contenuto** campo nella griglia delle proprietà oppure facendo clic di **definire...**  accanto al **contenuti** assegnare un'etichetta nel **ricezione** superficie dell'ActivityDesigner. Entrambi visualizzano la **definizione del contenuto** finestra di dialogo. Per altre informazioni su come usare questa casella, vedere la [finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) argomento. |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | Specifica l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per indirizzare il messaggio all'istanza del flusso di lavoro appropriata.<br /><br /> Fare clic sui puntini di sospensione accanto al <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> proprietà nella griglia delle proprietà per aprire la **Editor espressioni** nella finestra di dialogo. Per altre informazioni sull'uso della finestra di dialogo, vedere il [come: Utilizzare l'Editor espressioni](../workflow-designer/how-to-use-the-expression-editor.md) argomento. |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Send> all'interno del flusso di lavoro. Fare clic sui puntini di sospensione accanto al <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> proprietà nella griglia delle proprietà per aprire la **Aggiungi inizializzatori di correlazione** nella finestra di dialogo. Per altre informazioni sull'uso di questa casella, vedere la [finestra di dialogo Aggiungi inizializzatori di correlazione](../workflow-designer/add-correlationinitializers-dialog-box.md) argomento. |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Raccolta di tipi noti per l'operazione del servizio che deve essere chiamata da questa attività <xref:System.ServiceModel.Activities.Send>. Questa proprietà deve essere usata insieme alla proprietà <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> impostata su <xref:System.Runtime.Serialization.DataContractSerializer>. Viene ignorata se viene usato <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Selezionare il pulsante con puntini di sospensione accanto ad il **KnownTypes** campo nella griglia delle proprietà per visualizzare i **Editor raccolta di tipi** finestra di dialogo in cui è possibile aggiungere i tipi appropriati.<br /><br /> Selezionare il pulsante con puntini di sospensione accanto ad il **KnownTypes** campo nella griglia delle proprietà per visualizzare i **Editor raccolta di tipi** finestra di dialogo in cui è possibile aggiungere i tipi appropriati. Per altre informazioni sull'uso di questa casella, vedere la [finestra di dialogo Editor raccolta di tipo](../workflow-designer/type-collection-editor-dialog-box.md) argomento. |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | Specifica il tipo di <xref:System.Net.Security.ProtectionLevel> applicato al messaggio.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> indica solo l'autenticazione.<br />2. <xref:System.Net.Security.ProtectionLevel> significa firma i dati al fine di garantire l'integrità dei dati trasmessi.<br />3. <xref:System.Net.Security.ProtectionLevel> significa crittografare e firmare i dati per garantire la riservatezza e integrità dei dati trasmessi. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | Il tipo di serializzatore da usare per l'operazione del servizio che deve essere chiamata dall'attività <xref:System.ServiceModel.Activities.Send>. Il valore predefinito è <xref:System.Runtime.Serialization.DataContractSerializer>, che serializza e deserializza un'istanza di un tipo in un documento o un flusso XML che usa un contratto dati fornito. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | Specifica l'intestazione Action del messaggio. Se non è esplicitamente impostata, il valore predefinito è: https://tempuri.org/{service dello spazio dei nomi del contratto} / {nome del contratto di servizio} / {nome dell'operazione}. Se specificato in un'attività <xref:System.ServiceModel.Activities.Send>, l'attività <xref:System.ServiceModel.Activities.Receive> che riceve il messaggio deve avere lo stesso valore perché il messaggio venga recapitato correttamente. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | L'oggetto <xref:System.Security.Principal.TokenImpersonationLevel> consentito per il destinatario del messaggio. Definisce livelli di rappresentazione sicurezza, che determinano il grado in cui un processo server può operare per conto di un processo client.<xref:System.Security.Principal.TokenImpersonationLevel> indica che non è stato assegnato alcun livello di rappresentazione. <xref:System.Security.Principal.TokenImpersonationLevel> indica che processo server non può ottenere informazioni di identificazione sul client e non lo può rappresentare. <xref:System.Security.Principal.TokenImpersonationLevel> indica che il processo server può ottenere informazioni sul client, ad esempio ID di sicurezza e privilegi, ma non lo può rappresentare. Questa impostazione è utile per i server che esportano oggetti propri, ad esempio prodotti di database che esportano tabelle e viste. Usando le informazioni di sicurezza del client recuperate, il server può decidere se convalidare l'accesso senza poter usare altri servizi del contesto di sicurezza del client. <xref:System.Security.Principal.TokenImpersonationLevel> indica che il processo server può rappresentare il contesto di sicurezza del client nel sistema locale. Il server non può rappresentare il client nei sistemi remoti. <xref:System.Security.Principal.TokenImpersonationLevel> indica che il processo server può rappresentare il contesto di sicurezza del client nei sistemi locali. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | Oggetto <xref:System.ServiceModel.Endpoint> a cui l'attività <xref:System.ServiceModel.Activities.Send> invia il messaggio. Se questa proprietà è impostata la <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> della proprietà deve essere **null**. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | Oggetto <xref:System.ServiceModel.EndpointAddress> a cui viene inviato il messaggio. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Il nome della configurazione dell'endpoint. Questa proprietà viene impostata durante la configurazione di un endpoint in un file di configurazione. Questa proprietà deve essere impostata sul nome fornito  **\<endpoint >** elemento nel file di configurazione. Se questa proprietà è impostata, il <xref:System.ServiceModel.Activities.Send.Endpoint%2A> della proprietà deve essere **null**. |

## <a name="see-also"></a>Vedere anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)