---
title: Finestra di progettazione del flusso di lavoro - finestra di progettazione modello SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c6a4749ed138b22ac3d600befad01ef1776478e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976266"
---
# <a name="sendandreceivereply-template-designer"></a>Finestra di progettazione del modello SendAndReceiveReply

Il **SendAndReceiveReply** modello viene utilizzato per creare una coppia di preconfigurato <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> attività all'interno di un <xref:System.Activities.Statements.Sequence> attività correlate tra loro come parte di uno scambio di messaggi di richiesta/risposta modello sul client.

## <a name="the-sendandreceivereply-template"></a>Modello SendAndReceiveReply

Aggiunta di **SendAndReceiveReply** modello vengono eseguite tre operazioni oltre alla creazione di <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> attività all'interno di un <xref:System.Activities.Statements.Sequence> attività:

1.  Configurazione delle proprietà <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> dell'attività <xref:System.ServiceModel.Activities.Send>.

2.  Associazione della proprietà <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.ReceiveReply> all'attività <xref:System.ServiceModel.Activities.Send>.

3.  Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.

### <a name="using-the-sendandreceivereply-template-designer"></a>Utilizzo della finestra di progettazione dei modelli SendAndReceiveReply
 Il **SendAndReceiveReply** ActivityDesigner sono reperibili il **messaggistica** categoria del **casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti**  scheda nella finestra di progettazione del flusso di lavoro (in alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

 Il **SendAndReceiveReply** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che vengono in genere posizionate le attività. Crea un <xref:System.ServiceModel.Activities.Send> attività che può essere configurato con il **inviare** ActivityDesigner e un correlati <xref:System.ServiceModel.Activities.ReceiveReply> che può essere configurato con il **ReceiveReplyForSend** finestra di progettazione.

 Per ulteriori informazioni sull'utilizzo di **inviare** designer per configurare il <xref:System.ServiceModel.Activities.Send> attività, vedere il [inviare](../workflow-designer/send-activity-designer.md) argomento.

 Per ulteriori informazioni sull'utilizzo di **ReceiveReplyForSend** designer per configurare il <xref:System.ServiceModel.Activities.ReceiveReply> attività, vedere la sezione seguente.

### <a name="properties-of-receivereply"></a>Proprietà di ReceiveReply
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.ReceiveReply> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area Designerdesigner del flusso di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.ReceiveReply>. L'impostazione predefinita è ReceiveReplyForSend.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|True|Riferimento all'attività <xref:System.ServiceModel.Activities.Send> correlata a questa attività <xref:System.ServiceModel.Activities.ReceiveReply>. Questa proprietà non deve essere **null**. Le attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> sono usate insieme al client per modellare un modello di messaggistica di richiesta/risposta. Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata. Nella finestra di progettazione non è possibile modificarla in quanto viene associata automaticamente all'attività <xref:System.ServiceModel.Activities.Send> dalla quale è stata creata l'attività <xref:System.ServiceModel.Activities.ReceiveReply>.|
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|Specifica il contenuto del messaggio o del parametro da ricevere. Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modificare questa proprietà facendo clic sul pulsante con i puntini di sospensione accanto il **contenuto** griglia delle proprietà oppure facendo clic sul campo di **Definisci...**  accanto il **contenuto** etichetta nel **ricezione** superficie dell'ActivityDesigner. Entrambi visualizzano la **definizione contenuto** finestra di dialogo. Per ulteriori informazioni sull'utilizzo di questa casella, vedere il [finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md) argomento.|
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro. Fare clic sul pulsante con i puntini di sospensione accanto al <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> proprietà nella griglia delle proprietà per aprire la **Aggiungi inizializzatori di correlazione** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo di questa casella, vedere il [CorrelationInitializers di dialogo Aggiungi](../workflow-designer/add-correlationinitializers-dialog-box.md) argomento.|
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|Specifica l'intestazione Action del messaggio. Se non viene impostata esplicitamente, assume il valore predefinito:<br /><br /> **https://tempuri.org/{service spazio dei nomi del contratto} / {nome del contratto di servizio} / {nome operazione}.**|

## <a name="see-also"></a>Vedere anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Ricezione](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)