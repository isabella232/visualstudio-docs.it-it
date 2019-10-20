---
title: Progettazione modelli SendAndReceiveReply | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4ecb0e201c4351a8a117d1e35aca97866b2beb89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663274"
---
# <a name="sendandreceivereply-template-designer"></a>Finestra di progettazione del modello SendAndReceiveReply
Il modello **SendAndReceiveReply** viene usato per creare una coppia di attività preconfigurate <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> all'interno di un'attività <xref:System.Activities.Statements.Sequence> correlata come parte di un modello di scambio di messaggi di richiesta/risposta sul client.

## <a name="the-sendandreceivereply-template"></a>Modello SendAndReceiveReply
 L'aggiunta del modello **SendAndReceiveReply** esegue tre operazioni oltre a creare le attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> all'interno di un'attività <xref:System.Activities.Statements.Sequence>:

1. Configurazione delle proprietà <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> dell'attività <xref:System.ServiceModel.Activities.Send>.

2. Associazione della proprietà <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.ReceiveReply> all'attività <xref:System.ServiceModel.Activities.Send>.

3. Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="using-the-sendandreceivereply-template-designer"></a>Utilizzo della finestra di progettazione dei modelli SendAndReceiveReply
 L'ActivityDesigner **SendAndReceiveReply** è disponibile nella categoria **messaggistica** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** in [!INCLUDE[wfd2](../includes/wfd2-md.md)]. in alternativa, selezionare **barra degli** strumenti nella **visualizzazione** . oppure premere CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **SendAndReceiveReply** dalla **casella degli strumenti** e rilasciarlo nell'area [!INCLUDE[wfd2](../includes/wfd2-md.md)] quando le attività vengono in genere posizionate. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Send> configurabile con l'ActivityDesigner **Send** e una <xref:System.ServiceModel.Activities.ReceiveReply> correlata che può essere configurata con **ReceiveReplyForSend** designer.

 [!INCLUDE[crabout](../includes/crabout-md.md)] utilizzando la finestra di progettazione **Send** per configurare l'attività di <xref:System.ServiceModel.Activities.Send>, vedere l'argomento [Send](../workflow-designer/send-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] uso di **ReceiveReplyForSend** designer per configurare l'attività di <xref:System.ServiceModel.Activities.ReceiveReply>, vedere la sezione seguente.

### <a name="properties-of-receivereply"></a>Proprietà di ReceiveReply
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.ReceiveReply> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|                                 Nome proprietà                                 | Richiesto |                                                                                                                                                                                                                                                                                                                                                        Utilizzo                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.ReceiveReply>. L'impostazione predefinita è ReceiveReplyForSend.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Riferimento all'attività <xref:System.ServiceModel.Activities.Send> correlata a questa attività <xref:System.ServiceModel.Activities.ReceiveReply>. Questa proprietà non può essere **null**. Le attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> sono usate insieme al client per modellare un modello di messaggistica di richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione non è possibile modificarla in quanto viene associata automaticamente all'attività <xref:System.ServiceModel.Activities.Send> dalla quale è stata creata l'attività <xref:System.ServiceModel.Activities.ReceiveReply>. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Per modificare questa proprietà, fare clic sul pulsante con i puntini di sospensione accanto al campo **contenuto** nella griglia delle proprietà o fare clic su **Definisci...** accanto all'etichetta di **contenuto** nell'area di progettazione dell'attività di **ricezione** . Entrambi visualizzano la finestra di dialogo **Definizione contenuto** . [!INCLUDE[crabout](../includes/crabout-md.md)] come usare questa casella, vedere l'argomento relativo alla finestra di [dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) .                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con i puntini di sospensione accanto alla proprietà <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> nella griglia proprietà per aprire la finestra di dialogo **Aggiungi inizializzatori di correlazione** . [!INCLUDE[crabout](../includes/crabout-md.md)] usando questa casella, vedere l'argomento relativo alla finestra di [dialogo Aggiungi CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Specifica l'intestazione Action del messaggio. Se non viene impostata esplicitamente, assume il valore predefinito:<br /><br /> <strong>https://tempuri.org/{service spazio dei nomi del contratto}/{nome nome contratto}/{nome operazione}.</strong>                                                                                                                                                                                                                                               |

## <a name="see-also"></a>Vedere anche
 [ActivityDesigner CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)