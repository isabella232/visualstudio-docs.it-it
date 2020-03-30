---
title: Progettazione flussi di lavoro - Invia ActivityDesigner
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8690d5ccf18c752aacb37a71243d9f591fb9ee30
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395215"
---
# <a name="send-activity-designer"></a>ActivityDesigner Send

L'ActivityDesigner **Send** viene utilizzato <xref:System.ServiceModel.Activities.Send> per creare e configurare un'attività.

## <a name="the-send-activity"></a>Attività Send

 Un'attività <xref:System.ServiceModel.Activities.Send> viene usata per inviare un messaggio a un servizio. È possibile associare un'attività <xref:System.ServiceModel.Activities.ReceiveReply> a un'attività <xref:System.ServiceModel.Activities.Send> che riceve un messaggio come parte di un modello di scambio di messaggi di richiesta/risposta sul client.

### <a name="using-the-send-activity-designer"></a>Utilizzo dell'ActivityDesigner Send

Accedere all'ActivityDesigner **Send** nella categoria **Messaggistica** della **Casella degli strumenti**. L'ActivityDesigner **Send** può essere trascinato dalla **Casella degli strumenti** e rilasciato nell'area di Progettazione flussi di lavoro in cui vengono in genere inserite le attività. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Send> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Send. L'oggetto <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **Send** o nella casella **DisplayName** della griglia delle proprietà.

Per creare <xref:System.ServiceModel.Activities.ReceiveReply> un'attività e <xref:System.ServiceModel.Activities.Send> associarla all'attività selezionata, fare clic con il pulsante destro del mouse sull'ActivityDesigner **Send,** scegliere l'elemento **Create ReceiveReply** nel menu di scelta rapida e la finestra di progettazione **ReceiveReplyForSend** viene visualizzata sotto la finestra di progettazione **Send.** L'attività <xref:System.ServiceModel.Activities.ReceiveReply> è un'attività che riceve un messaggio come parte di un modello di scambio di messaggi di richiesta/risposta sul client. Può essere configurato con la finestra di progettazione **ReceiveReplyForSend.It** can be configured with the ReceiveReplyForSend designer.

In alternativa, la finestra di progettazione del modello **SendAndReceiveReply** nella categoria Di <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> **seguito** messaggistica della Casella **degli strumenti** può essere utilizzata per creare una coppia di attività e preconfigurate. Per ulteriori informazioni sull'utilizzo dei modelli **SendAndReceiveReply** e **ReceiveReplyForSend,** vedere l'argomento [SendAndReceiveReply.](../workflow-designer/sendandreceivereply-template-designer.md)

### <a name="the-send-activity-properties"></a>Proprietà dell'attività Send

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.Send> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà o nell'area di Progettazione flussi di lavoro.

| Nome proprietà | Obbligatoria | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nome descrittivo dell'attività <xref:System.ServiceModel.Activities.Send>. L'impostazione predefinita è Send. Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | Nome dell'operazione del servizio chiamata da questa attività <xref:System.ServiceModel.Activities.Send>. Questa proprietà viene utilizzata per costruire il valore predefinito per il **Action** proprietà se il **Action** proprietà non è impostata in modo esplicito. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | Nome del contratto del servizio implementato dal servizio da chiamare. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà selezionando il pulsante con i due coniatori accanto al **contenuto** campo nella griglia delle proprietà o facendo clic sul **definisci...** pulsante accanto al **contenuto** etichetta nel **ricezione** area dell'ActivityDesigner. Entrambi visualizzano la finestra di dialogo **Definizione contenuto.** Per altre informazioni su come usare questa casella, vedere l'argomento Finestra di [dialogo Definizione contenuto.](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | Specifica l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per indirizzare il messaggio all'istanza del flusso di lavoro appropriata.<br /><br /> Fare clic sul pulsante con <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> i coniatori a i solcanto risciacquatore accanto alla proprietà nella griglia delle proprietà per aprire la finestra di dialogo **Editor espressioni.** Per ulteriori informazioni sull'utilizzo di questa finestra di dialogo, vedere la [procedura: utilizzare l'argomento Editor espressioni.](../workflow-designer/how-to-use-the-expression-editor.md) |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Send> all'interno del flusso di lavoro. Fare clic sul pulsante con <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> i coniatori a i solcanto risciacqua accanto alla proprietà nella griglia delle proprietà per aprire la finestra di dialogo **Aggiungi inizializzatori di correlazione.** Per altre informazioni sull'uso di questa casella, vedere l'argomento Finestra di [dialogo Aggiungi CorrelationInitializers.For](../workflow-designer/add-correlationinitializers-dialog-box.md) more information about using this box, see the Add CorrelationInitializers Dialog Box topic. |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Raccolta di tipi noti per l'operazione del servizio che deve essere chiamata da questa attività <xref:System.ServiceModel.Activities.Send>. Questa proprietà deve essere usata insieme alla proprietà <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> impostata su <xref:System.Runtime.Serialization.DataContractSerializer>. Viene ignorata se viene usato <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Selezionare il pulsante con i puntine accanto al campo **KnownTypes** nella griglia delle proprietà per visualizzare la finestra di dialogo **Editor della raccolta** di tipi con cui è possibile aggiungere tipi pertinenti.<br /><br /> Selezionare il pulsante con i puntine accanto al campo **KnownTypes** nella griglia delle proprietà per visualizzare la finestra di dialogo **Editor della raccolta** di tipi con cui è possibile aggiungere tipi pertinenti. Per altre informazioni sull'uso di questa casella, vedere l'argomento Finestra di [dialogo Editor dell'insieme dei](../workflow-designer/type-collection-editor-dialog-box.md) tipi. |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | Specifica il tipo di <xref:System.Net.Security.ProtectionLevel> applicato al messaggio.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> significa solo autenticazione.<br />2. <xref:System.Net.Security.ProtectionLevel> significa firmare i dati per contribuire a garantire l'integrità dei dati trasmessi.<br />3. <xref:System.Net.Security.ProtectionLevel> significa crittografare e firmare i dati per contribuire a garantire la riservatezza e l'integrità dei dati trasmessi. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | Il tipo di serializzatore da usare per l'operazione del servizio che deve essere chiamata dall'attività <xref:System.ServiceModel.Activities.Send>. Il valore predefinito è <xref:System.Runtime.Serialization.DataContractSerializer>, che serializza e deserializza un'istanza di un tipo in un documento o un flusso XML che usa un contratto dati fornito. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | Specifica l'intestazione Action del messaggio. Se non è impostato in modo esplicito, il valore predefinito è: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. Se specificato in un'attività <xref:System.ServiceModel.Activities.Send>, l'attività <xref:System.ServiceModel.Activities.Receive> che riceve il messaggio deve avere lo stesso valore perché il messaggio venga recapitato correttamente. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | L'oggetto <xref:System.Security.Principal.TokenImpersonationLevel> consentito per il destinatario del messaggio. Definisce i livelli di rappresentazione di sicurezza, che regolano il grado in cui un processo server può agire per conto di un processo client.<xref:System.Security.Principal.TokenImpersonationLevel>  indica che non è assegnato alcun livello di rappresentazione. <xref:System.Security.Principal.TokenImpersonationLevel>indica che il processo server non è in grado di ottenere informazioni di identificazione sul client e di non poter rappresentare il client. <xref:System.Security.Principal.TokenImpersonationLevel>indica che il processo server può ottenere informazioni sul client, ad esempio gli identificatori di protezione e i privilegi, ma che non può rappresentare il client. Questa impostazione è utile per i server che esportano oggetti propri, ad esempio prodotti di database che esportano tabelle e viste. Usando le informazioni di sicurezza del client recuperate, il server può decidere se convalidare l'accesso senza poter usare altri servizi del contesto di sicurezza del client. <xref:System.Security.Principal.TokenImpersonationLevel>indica che il processo server può rappresentare il contesto di sicurezza del client nel sistema locale. Il server non può rappresentare il client nei sistemi remoti. <xref:System.Security.Principal.TokenImpersonationLevel>indica che il processo server può rappresentare il contesto di sicurezza del client nei sistemi remoti. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | Oggetto <xref:System.ServiceModel.Endpoint> a cui l'attività <xref:System.ServiceModel.Activities.Send> invia il messaggio. Se questa proprietà <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> è impostata, la proprietà deve essere **null.** |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | Oggetto <xref:System.ServiceModel.EndpointAddress> a cui viene inviato il messaggio. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Nome della configurazione dell'endpoint. Questa proprietà viene impostata durante la configurazione di un endpoint in un file di configurazione. Questa proprietà deve essere impostata ** \<** sul nome specificato nell'elemento>endpoint nel file di configurazione. Se questa proprietà è <xref:System.ServiceModel.Activities.Send.Endpoint%2A> impostata, la proprietà deve essere **null**. |

## <a name="see-also"></a>Vedere anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)