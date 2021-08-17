---
title: Finestra di progettazione del modello SendAndReceiveReply
description: Informazioni su come usare il modello SendAndReceiveReply in Progettazione flussi di lavoro per creare una coppia di attività Send e ReceiveReply preconfigurato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: b39383e23f917f3f19c590e20f96dcdf8d611239ed6b1477aee4cd93bbcb12e9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440422"
---
# <a name="sendandreceivereply-template-designer"></a>Finestra di progettazione del modello SendAndReceiveReply

Il **modello SendAndReceiveReply** viene usato per creare una coppia di attività e preconfigurato. <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> Le attività fanno parte di un'attività e sono correlate come parte di un modello di scambio di messaggi di <xref:System.Activities.Statements.Sequence> richiesta/risposta nel client.

## <a name="the-sendandreceivereply-template"></a>Modello SendAndReceiveReply

**L'aggiunta del modello SendAndReceiveReply** esegue tre operazioni oltre alla creazione delle <xref:System.ServiceModel.Activities.Send> attività e <xref:System.ServiceModel.Activities.ReceiveReply> all'interno di <xref:System.Activities.Statements.Sequence> un'attività:

- Configura le proprietà <xref:System.ServiceModel.Activities.Send.OperationName%2A> e <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> <xref:System.ServiceModel.Activities.Send> dell'attività.

- Associazione della proprietà <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.ReceiveReply> all'attività <xref:System.ServiceModel.Activities.Send>.

- Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="use-the-sendandreceivereply-template-designer"></a>Usare La finestra di progettazione modelli SendAndReceiveReply

Accedere **all'ActivityDesigner SendAndReceiveReply** nella **categoria Messaggistica** della casella **degli strumenti**. L'ActivityDesigner **SendAndReceiveReply** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie Progettazione flussi di lavoro in cui vengono in genere posizionate le attività. L'eliminazione dell'ActivityDesigner crea un'attività che può essere configurata con l'ActivityDesigner di invio e un elemento correlato che può essere configurato con la finestra di progettazione <xref:System.ServiceModel.Activities.Send>  <xref:System.ServiceModel.Activities.ReceiveReply> **ReceiveReplyForSend.**

Per altre informazioni sull'uso della finestra **di** progettazione di invio per configurare <xref:System.ServiceModel.Activities.Send> l'attività, vedere [Inviare](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Proprietà di ReceiveReply

Nella tabella seguente vengono illustrate <xref:System.ServiceModel.Activities.ReceiveReply> le proprietà e viene descritto come vengono usate nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nella Progettazione flussi di lavoro superficie.

| Nome proprietà | Obbligatoria | Utilizzo |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.ReceiveReply>. L'impostazione predefinita è ReceiveReplyForSend.<br /><br /> Anche se l'uso di un valore non predefinito per il tipo descrittivo non è strettamente necessario, è meglio <xref:System.Activities.Activity.DisplayName%2A> usare tale valore. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | Vero | Riferimento all'attività <xref:System.ServiceModel.Activities.Send> correlata a questa attività <xref:System.ServiceModel.Activities.ReceiveReply>. Questa proprietà non deve essere **Null.** <xref:System.ServiceModel.Activities.Send> le <xref:System.ServiceModel.Activities.ReceiveReply> attività e vengono usate insieme nel client per modellare un modello di messaggistica di richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione non è possibile modificare questa proprietà perché è associata automaticamente <xref:System.ServiceModel.Activities.Send> all'attività da cui è stata creata l'attività. <xref:System.ServiceModel.Activities.ReceiveReply> |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | Falso | Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà facendo clic sul pulsante con i puntini di sospensione  accanto al campo  **Contenuto** nella griglia delle proprietà oppure facendo clic sul pulsante Definisci accanto all'etichetta Contenuto nell'area **di** ActivityDesigner ricezione. Entrambi visualizzano la **finestra di dialogo Definizione** contenuto. Per altre informazioni su come usare questa casella, vedere Finestra [di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | Falso | Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con i puntini di sospensione accanto alla proprietà nella griglia delle proprietà per aprire la finestra di dialogo Aggiungi <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> **inizializzatori** di correlazione . Per altre informazioni sull'uso di questa casella, vedere Finestra di dialogo [Aggiungi correlationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | Falso | Specifica l'intestazione Action del messaggio. Se non è impostato in modo esplicito, il valore predefinito è:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Vedi anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)