---
title: Finestra di progettazione del modello SendAndReceiveReply . Documenti Microsoft
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
ms.openlocfilehash: 1bfe43f410709a924b0ebdb0cf6afbb8d30a8fcf
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395332"
---
# <a name="sendandreceivereply-template-designer"></a>Finestra di progettazione del modello SendAndReceiveReply
Il modello **SendAndReceiveReply** viene utilizzato per creare <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> una coppia <xref:System.Activities.Statements.Sequence> di attività e preconfigurate all'interno di un'attività correlate come parte di un modello di scambio di messaggi di richiesta/risposta sul client.

## <a name="the-sendandreceivereply-template"></a>Modello SendAndReceiveReply
 L'aggiunta del modello SendAndReceiveReply <xref:System.ServiceModel.Activities.Send> esegue <xref:System.ServiceModel.Activities.ReceiveReply> tre operazioni oltre a creare le attività e all'interno di un'attività:Adding SendAndReceiveReply template does three things oltre a creare le attività e all'interno di un'attività:Adding <xref:System.Activities.Statements.Sequence> **SendAndReceiveReply** template does three things oltre

1. Configurazione delle proprietà <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> dell'attività <xref:System.ServiceModel.Activities.Send>.

2. Associazione della proprietà <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.ReceiveReply> all'attività <xref:System.ServiceModel.Activities.Send>.

3. Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="using-the-sendandreceivereply-template-designer"></a>Utilizzo della finestra di progettazione dei modelli SendAndReceiveReply
 L'ActivityDesigner **SendAndReceiveReply** è disponibile nella categoria **Messaggidella** **Casella degli strumenti**, a cui si accede facendo clic sulla scheda Casella degli **strumenti** [!INCLUDE[wfd2](../includes/wfd2-md.md)] in (in alternativa, selezionare Barra degli **strumenti** dal menu **Visualizza,** o CTRL.

 Il **SendAndReceiveReply** ActivityDesigner può essere trascinato dalla [!INCLUDE[wfd2](../includes/wfd2-md.md)] casella degli **strumenti** e rilasciato sulla superficie in cui vengono in genere posizionate le attività. Verrà creata <xref:System.ServiceModel.Activities.Send> un'attività che può essere configurata <xref:System.ServiceModel.Activities.ReceiveReply> con l'ActivityDesigner Send e una funzionalità correlata che può essere configurata con la finestra di progettazione ReceiveReplyForSend.This creates a activity that can be configured with the **Send** activity designer and a correlated that can be configured with the **ReceiveReplyForSend** designer.

 [!INCLUDE[crabout](../includes/crabout-md.md)]Utilizzando **Send** la finestra di <xref:System.ServiceModel.Activities.Send> progettazione di invio per configurare l'attività, vedere il [inviare](../workflow-designer/send-activity-designer.md) argomento.

 [!INCLUDE[crabout](../includes/crabout-md.md)]utilizzando la finestra di progettazione <xref:System.ServiceModel.Activities.ReceiveReply> **ReceiveReplyForSend** per configurare l'attività, vedere la sezione seguente.

### <a name="properties-of-receivereply"></a>Proprietà di ReceiveReply
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.ReceiveReply> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|                                 Nome proprietà                                 | Obbligatoria |                                                                                                                                                                                                                                                                                                                                                        Uso                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.ReceiveReply>. L'impostazione predefinita è ReceiveReplyForSend.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Riferimento all'attività <xref:System.ServiceModel.Activities.Send> correlata a questa attività <xref:System.ServiceModel.Activities.ReceiveReply>. Questa proprietà non deve essere **null.** <xref:System.ServiceModel.Activities.Send>e <xref:System.ServiceModel.Activities.ReceiveReply> le attività vengono utilizzate insieme sul client per modellare un modello di messaggistica richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione non è possibile modificarla in quanto viene associata automaticamente all'attività <xref:System.ServiceModel.Activities.Send> dalla quale è stata creata l'attività <xref:System.ServiceModel.Activities.ReceiveReply>. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà facendo clic sul pulsante con i puntini di sospensione accanto al campo **Contenuto** nella griglia delle proprietà o facendo clic su **Definisci...** accanto all'etichetta **Contenuto** nell'area dell'ActivityDesigner **ricezione.** Entrambi visualizzano la finestra di dialogo **Definizione contenuto.** [!INCLUDE[crabout](../includes/crabout-md.md)]come utilizzare questa casella, vedere la finestra di [dialogo Definizione contenuto.](../workflow-designer/content-definition-dialog-box.md)                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> i coniatori a i solcanto risciacqua accanto alla proprietà nella griglia delle proprietà per aprire la finestra di dialogo **Aggiungi inizializzatori di correlazione.** [!INCLUDE[crabout](../includes/crabout-md.md)]Utilizzando questa casella, vedere l'argomento [Aggiungi CorrelationInitializers dialogbox.](../workflow-designer/add-correlationinitializers-dialog-box.md)               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Specifica l'intestazione Action del messaggio. Se non viene impostata esplicitamente, assume il valore predefinito:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>Vedere anche
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md)