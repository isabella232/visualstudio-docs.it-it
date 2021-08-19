---
title: Progettazione flussi di lavoro - Inviare ActivityDesigner
description: Informazioni sull'attività Invia e su come usare l'ActivityDesigner di invio per creare e configurare un'attività Di invio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 1574d6b48e904288cde5ea66be6350430b81bc44
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114524"
---
# <a name="send-activity-designer"></a>ActivityDesigner Send

**L'ActivityDesigner** di invio viene usato per creare e configurare un'attività. <xref:System.ServiceModel.Activities.Send>

## <a name="the-send-activity"></a>Attività Send

 Un'attività <xref:System.ServiceModel.Activities.Send> viene usata per inviare un messaggio a un servizio. È possibile associare un'attività <xref:System.ServiceModel.Activities.ReceiveReply> a un'attività <xref:System.ServiceModel.Activities.Send> che riceve un messaggio come parte di un modello di scambio di messaggi di richiesta/risposta sul client.

### <a name="using-the-send-activity-designer"></a>Utilizzo dell'ActivityDesigner Send

Accedere **all'ActivityDesigner** di invio nella **categoria Messaggistica** della Casella **degli strumenti**. **L'ActivityDesigner** di invio può  essere trascinato dalla casella degli strumenti e rilasciato nella Progettazione flussi di lavoro in cui vengono in genere posizionate le attività. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Send> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Send. <xref:System.Activities.Activity.DisplayName%2A>L'oggetto può essere modificato  nell'intestazione dell'ActivityDesigner di invio o nella **casella DisplayName** della griglia delle proprietà.

Per creare un'attività e associarla all'attività selezionata, fare clic con il pulsante destro del mouse sull'ActivityDesigner di invio, scegliere l'elemento Create ReceiveReply nel menu di scelta rapida e la finestra di progettazione <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.Send> **ReceiveReplyForSend**    viene visualizzata sotto la finestra di progettazione di invio. L'attività <xref:System.ServiceModel.Activities.ReceiveReply> è un'attività che riceve un messaggio come parte di un modello di scambio di messaggi di richiesta/risposta sul client. Può essere configurato con la finestra **di progettazione ReceiveReplyForSend.**

In alternativa, è possibile usare la finestra di  progettazione dei  modelli **SendAndReceiveReply** nella categoria Messaggistica della casella degli strumenti per creare una coppia di attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> preconfigurato. Per altre informazioni sull'uso dei modelli **SendAndReceiveReply** e **ReceiveReplyForSend,** vedere l'argomento [SendAndReceiveReply.](../workflow-designer/sendandreceivereply-template-designer.md)

### <a name="the-send-activity-properties"></a>Proprietà dell'attività Send

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.Send> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà o Progettazione flussi di lavoro superficie.

| Nome proprietà | Obbligatoria | Utilizzo |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | Nome descrittivo dell'attività <xref:System.ServiceModel.Activities.Send>. L'impostazione predefinita è Send. Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | Vero | Nome dell'operazione del servizio chiamata da questa attività <xref:System.ServiceModel.Activities.Send>. Questa proprietà viene usata per costruire il valore predefinito per la **proprietà Action** se la **proprietà Action** non è impostata in modo esplicito. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | Vero | Nome del contratto del servizio implementato dal servizio da chiamare. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | Falso | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà selezionando il pulsante con i puntini di sospensione accanto al campo **Contenuto** nella griglia delle proprietà o facendo clic sul pulsante Definisci **accanto** all'etichetta **Contenuto** nell'area **di** ActivityDesigner ricezione. Entrambi visualizzano la **finestra di dialogo Definizione** contenuto. Per altre informazioni su come usare questa casella, vedere l'argomento [Finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | Falso | Specifica l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per indirizzare il messaggio all'istanza del flusso di lavoro appropriata.<br /><br /> Fare clic sul pulsante con i puntini di sospensione accanto alla <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> proprietà nella griglia delle proprietà per aprire la finestra di dialogo **Editor** espressioni . Per altre informazioni sull'uso di questa finestra di dialogo, vedere l'argomento [Procedura: Usare l'editor di](../workflow-designer/how-to-use-the-expression-editor.md) espressioni. |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | Falso | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Send> all'interno del flusso di lavoro. Fare clic sul pulsante con i puntini di sospensione accanto alla proprietà nella griglia delle proprietà per aprire la finestra di dialogo Aggiungi <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> **inizializzatori** di correlazione . Per altre informazioni sull'uso di questa casella, vedere [l'argomento Aggiungi correlationInitializers Dialog Box.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | Falso | Raccolta di tipi noti per l'operazione del servizio che deve essere chiamata da questa attività <xref:System.ServiceModel.Activities.Send>. Questa proprietà deve essere usata insieme alla proprietà <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> impostata su <xref:System.Runtime.Serialization.DataContractSerializer>. Viene ignorata se viene usato <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Selezionare il pulsante con i puntini di sospensione accanto al campo **KnownTypes** nella griglia delle proprietà per visualizzare la finestra di dialogo **Editor** raccolta tipi con cui è possibile aggiungere tipi pertinenti.<br /><br /> Selezionare il pulsante con i puntini di sospensione accanto al campo **KnownTypes** nella griglia delle proprietà per visualizzare la finestra di dialogo **Editor** raccolta tipi con cui è possibile aggiungere tipi pertinenti. Per altre informazioni sull'uso di questa casella, vedere l'argomento [Finestra di dialogo Editor raccolta tipi](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | Vero | Specifica il tipo di <xref:System.Net.Security.ProtectionLevel> applicato al messaggio.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> indica solo l'autenticazione.<br />2.  <xref:System.Net.Security.ProtectionLevel> significa firmare i dati per garantire l'integrità dei dati trasmessi.<br />3.  <xref:System.Net.Security.ProtectionLevel> significa crittografare e firmare i dati per garantire la riservatezza e l'integrità dei dati trasmessi. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | Vero | Il tipo di serializzatore da usare per l'operazione del servizio che deve essere chiamata dall'attività <xref:System.ServiceModel.Activities.Send>. Il valore predefinito è <xref:System.Runtime.Serialization.DataContractSerializer>, che serializza e deserializza un'istanza di un tipo in un documento o un flusso XML che usa un contratto dati fornito. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | Falso | Specifica l'intestazione Action del messaggio. Se non è impostato in modo esplicito, il relativo valore predefinito è: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . Se specificato in un'attività <xref:System.ServiceModel.Activities.Send>, l'attività <xref:System.ServiceModel.Activities.Receive> che riceve il messaggio deve avere lo stesso valore perché il messaggio venga recapitato correttamente. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | L'oggetto <xref:System.Security.Principal.TokenImpersonationLevel> consentito per il destinatario del messaggio. Definisce i livelli di rappresentazione di sicurezza, che determinano il grado in cui un processo server può agire per conto di un processo client.<xref:System.Security.Principal.TokenImpersonationLevel>  indica che non è assegnato alcun livello di rappresentazione. <xref:System.Security.Principal.TokenImpersonationLevel> indica che il processo server non può ottenere informazioni di identificazione sul client e non può rappresentare il client. <xref:System.Security.Principal.TokenImpersonationLevel> indica che il processo server può ottenere informazioni sul client, ad esempio gli identificatori di sicurezza e i privilegi, ma che non può rappresentare il client. Questa impostazione è utile per i server che esportano oggetti propri, ad esempio prodotti di database che esportano tabelle e viste. Usando le informazioni di sicurezza del client recuperate, il server può decidere se convalidare l'accesso senza poter usare altri servizi del contesto di sicurezza del client. <xref:System.Security.Principal.TokenImpersonationLevel> indica che il processo server può rappresentare il contesto di sicurezza del client nel sistema locale. Il server non può rappresentare il client nei sistemi remoti. <xref:System.Security.Principal.TokenImpersonationLevel> indica che il processo server può rappresentare il contesto di sicurezza del client nei sistemi remoti. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | Oggetto <xref:System.ServiceModel.Endpoint> a cui l'attività <xref:System.ServiceModel.Activities.Send> invia il messaggio. Se questa proprietà è impostata, <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> la proprietà deve essere **Null.** |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | Oggetto <xref:System.ServiceModel.EndpointAddress> a cui viene inviato il messaggio. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Nome della configurazione dell'endpoint. Questa proprietà viene impostata durante la configurazione di un endpoint in un file di configurazione. Questa proprietà deve essere impostata sul nome specificato **\<endpoint>** nell'elemento nel file di configurazione. Se questa proprietà è impostata, <xref:System.ServiceModel.Activities.Send.Endpoint%2A> la proprietà deve essere **Null.** |

## <a name="see-also"></a>Vedi anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)