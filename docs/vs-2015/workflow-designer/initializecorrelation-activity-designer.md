---
title: ActivityDesigner InitializeCorrelation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 145b67574169696771f4102b29e9dc8f6a9d1575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659026"
---
# <a name="initializecorrelation-activity-designer"></a>ActivityDesigner InitializeCorrelation
L'ActivityDesigner **InitializeCorrelation** viene utilizzato per creare e configurare un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> utilizzata per stabilire una correlazione tra i messaggi prima di inviarli o riceverli.

## <a name="the-initializecorrelation-activity"></a>Attività InitializeCorrelation
 Un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> viene usata per inizializzare le correlazioni senza inviare o ricevere un messaggio. La correlazione viene in genere inizializzata quando si invia o riceve un messaggio. Se è necessario stabilire la correlazione prima che un messaggio venga inviato o ricevuto, usare <xref:System.ServiceModel.Activities.InitializeCorrelation> per inizializzarla.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizzo dell'ActivityDesigner InitializeCorrelation
 L'ActivityDesigner **InitializeCorrelation** è disponibile nella categoria **messaggistica** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** nel [!INCLUDE[wfd2](../includes/wfd2-md.md)]. in alternativa, selezionare **barra degli** strumenti nella **visualizzazione.** menu o CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **InitializeCorrelation** dalla **casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Verrà creata un'attività di <xref:System.ServiceModel.Activities.InitializeCorrelation> con un <xref:System.Activities.Activity.DisplayName%2A> predefinito di InitializeCorrelation. il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **InitializeCorrelation** o nella casella **DisplayName** della finestra **proprietà** .

 È possibile specificare il <xref:System.ServiceModel.Activities.CorrelationHandle> nel campo **correlazione** nella finestra **Proprietà** dell'area di progettazione dell'attività **InitializeCorrelation** .

 Facendo clic sul pulsante con i puntini di sospensione accanto al campo **CorrelationData** nella finestra **Proprietà** o "Visualizza..." Testo suggerimento sull'area dell'ActivityDesigner **InitializeCorrelation** Visualizza la finestra di dialogo **Inizializza correlazione** in cui è possibile specificare l'handle di correlazione e le coppie chiave-valore usate per inizializzarlo. [!INCLUDE[crabout](../includes/crabout-md.md)] utilizzando questa finestra di dialogo, vedere l'argomento della finestra di [dialogo Editor raccolta di tipi](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Proprietà di InitializeCorrelation
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.InitializeCorrelation> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella finestra **Proprietà** o in [!INCLUDE[wfd2](../includes/wfd2-md.md)] area.

|Nome proprietà|Richiesto|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>. Il valore predefinito è InitializeCorrelation.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> usato per associare le attività del flusso di lavoro nella correlazione.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dizionario dei dati di correlazione che mette in correlazione i messaggi all'istanza del flusso di lavoro.<br /><br /> Utilizzare la finestra di dialogo **Inizializza correlazione** per configurare la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../includes/crabout-md.md)] la finestra di dialogo Usa questa finestra di dialogo, vedere l'argomento della finestra di [dialogo Editor raccolta di tipi](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Vedere anche
 [ActivityDesigner CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)