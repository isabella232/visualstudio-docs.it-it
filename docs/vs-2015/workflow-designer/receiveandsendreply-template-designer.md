---
title: Progettazione modelli ReceiveAndSendReply | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e853967f73c99aa52958754e9f59f644c2f9497b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672546"
---
# <a name="receiveandsendreply-template-designer"></a>Finestra di progettazione del modello ReceiveAndSendReply
Il modello **ReceiveAndSendReply** viene usato per creare una coppia di attività preconfigurate <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> all'interno di un'attività <xref:System.Activities.Statements.Sequence> correlata come parte di un modello di scambio di messaggi di richiesta/risposta sul server.

## <a name="the-receiveandsendreply-template"></a>Modello ReceiveAndSendReply
 L'aggiunta del modello **ReceiveAndSendReply** esegue tre operazioni oltre a creare le attività <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> con un'attività <xref:System.Activities.Statements.Sequence>:

1. Configurazione delle proprietà <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> dell'attività <xref:System.ServiceModel.Activities.Receive>.

2. Associazione della proprietà <xref:System.ServiceModel.Activities.SendReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.Receive> all'attività <xref:System.ServiceModel.Activities.Send>.

3. Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="using-the-receiveandsendreply-template-designer"></a>Utilizzo della finestra di progettazione del modello ReceiveAndSendReply
 L'ActivityDesigner **ReceiveAndSendReply** è disponibile nella categoria **messaggistica** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** in [!INCLUDE[wfd2](../includes/wfd2-md.md)]. in alternativa, selezionare **barra degli** strumenti nella **visualizzazione** . oppure premere CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **ReceiveAndSendReply** dalla **casella degli strumenti** e rilasciarlo nell'area [!INCLUDE[wfd2](../includes/wfd2-md.md)] quando le attività vengono in genere posizionate. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> configurabile con l'ActivityDesigner **Send** e una <xref:System.ServiceModel.Activities.SendReply> correlata che può essere configurata con SendReplyToReceive designer.

 [!INCLUDE[crabout](../includes/crabout-md.md)] utilizzando la finestra di progettazione **ricezione** per configurare l'attività <xref:System.ServiceModel.Activities.Receive>, vedere l'argomento [Receive](../workflow-designer/receive-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] uso di **SendReplyToReceive** designer per configurare l'attività di <xref:System.ServiceModel.Activities.SendReply>, vedere la sezione seguente.

### <a name="properties-of-sendreply"></a>Proprietà di SendReply
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.SendReply> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|                               Nome proprietà                                | Richiesto |                                                                                                                                                                                                                                                                                                                                                      Utilizzo                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.SendReply>. Il valore predefinito è SendReplyToReceive.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | Riferimento all'attività <xref:System.ServiceModel.Activities.Receive> correlata a questa attività <xref:System.ServiceModel.Activities.SendReply>. Questa proprietà non può essere **null**. Le attività <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> sono usate insieme sul server per modellare un modello di messaggistica di richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione non è possibile modificarla in quanto viene associata automaticamente all'attività <xref:System.ServiceModel.Activities.Send> dalla quale è stata creata l'attività <xref:System.ServiceModel.Activities.SendReply>. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Per modificare questa proprietà, fare clic sul pulsante con i puntini di sospensione accanto al campo **contenuto** nella griglia delle proprietà o fare clic su **Definisci...** accanto all'etichetta di **contenuto** nell'area di progettazione dell'attività di **ricezione** . Entrambi visualizzano la finestra di dialogo **Definizione contenuto** . [!INCLUDE[crabout](../includes/crabout-md.md)] come usare questa casella, vedere l'argomento relativo alla finestra di [dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) .                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con i puntini di sospensione accanto alla proprietà <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> nella griglia proprietà per aprire la finestra di dialogo **Aggiungi inizializzatori di correlazione** . [!INCLUDE[crabout](../includes/crabout-md.md)] usando questa casella, vedere l'argomento relativo alla finestra di [dialogo Aggiungi CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              Specifica l'intestazione Action del messaggio. Se non viene impostata esplicitamente, assume il valore predefinito:<br /><br /> <strong>spazio dei nomi del contratto https://tempuri.org/{service }/{nome nome contratto}/{nome operazione}</strong>                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Specifica se l'istanza di servizio del flusso di lavoro deve essere salvata in modo permanente prima di inviare il messaggio di risposta. Il valore predefinito è **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Vedere anche
 [ActivityDesigner CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)