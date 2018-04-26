---
title: Finestra di progettazione del flusso di lavoro - ActivityDesigner InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24d319af36b5d07661213edb3cff48d376bd3736
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="initializecorrelation-activity-designer"></a>ActivityDesigner InitializeCorrelation

Il **InitializeCorrelation** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività che viene usato per stabilire una correlazione tra i messaggi prima dell'invio e ricezione.

## <a name="the-initializecorrelation-activity"></a>Attività InitializeCorrelation

Un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> viene usata per inizializzare le correlazioni senza inviare o ricevere un messaggio. La correlazione viene in genere inizializzata quando si invia o riceve un messaggio. Se è necessario stabilire la correlazione prima che un messaggio venga inviato o ricevuto, usare <xref:System.ServiceModel.Activities.InitializeCorrelation> per inizializzarla.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizzo dell'ActivityDesigner InitializeCorrelation
 Il **InitializeCorrelation** ActivityDesigner sono reperibili il **messaggistica** categoria del **casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti**  scheda nella finestra di progettazione del flusso di lavoro (in alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu o premere CTRL + ALT + X.)

 Il **InitializeCorrelation** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro. Crea un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività con valore predefinito è <xref:System.Activities.Activity.DisplayName%2A> di InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **InitializeCorrelation** ActivityDesigner o nel  **DisplayName** casella della finestra di **proprietà** finestra.

 Il <xref:System.ServiceModel.Activities.CorrelationHandle> può essere specifica nel **correlazione** campo **proprietà** finestra il **InitializeCorrelation** superficie dell'ActivityDesigner.

 Fare clic sul pulsante ellisse oltre il **CorrelationData** campo **proprietà** finestra o il testo di suggerimento "Vista …" nel **InitializeCorrelation** ActivityDesigner superficie di attacco consente di visualizzare il **Inizializza correlazione** la finestra di dialogo in cui è possibile specificare l'handle di correlazione e le coppie chiave-valore utilizzate per l'inizializzazione. Per ulteriori informazioni sull'utilizzo di questa finestra di dialogo, vedere il [finestra di dialogo Editor dell'insieme di tipo](../workflow-designer/type-collection-editor-dialog-box.md) argomento.

### <a name="the-initializecorrelation-properties"></a>Proprietà di InitializeCorrelation
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.InitializeCorrelation> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Queste proprietà possono essere modificate nella **proprietà** finestra o nell'area di progettazione flussi di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>. Il valore predefinito è InitializeCorrelation.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> usato per associare le attività del flusso di lavoro nella correlazione.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dizionario dei dati di correlazione che mette in correlazione i messaggi all'istanza del flusso di lavoro.<br /><br /> Utilizzare il **Inizializza correlazione** la finestra di dialogo per configurare il <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Per ulteriori informazioni sull'utilizzo di questa finestra di dialogo, vedere il [finestra di dialogo Editor dell'insieme di tipo](../workflow-designer/type-collection-editor-dialog-box.md) argomento.|

## <a name="see-also"></a>Vedere anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Ricezione](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)