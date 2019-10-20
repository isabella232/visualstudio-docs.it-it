---
title: ActivityDesigner Progettazione flussi di lavoro-InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98a9a6bccb6eab2c4565a717daa897f93dbe8f53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650216"
---
# <a name="initializecorrelation-activity-designer"></a>ActivityDesigner InitializeCorrelation

L'ActivityDesigner **InitializeCorrelation** viene usato per creare e configurare un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>. L'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> stabilisce una correlazione tra i messaggi prima di inviarli o riceverli.

## <a name="the-initializecorrelation-activity"></a>Attività InitializeCorrelation

Un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> viene usata per inizializzare le correlazioni senza inviare o ricevere un messaggio. La correlazione viene in genere inizializzata quando si invia o riceve un messaggio. Se è necessario stabilire la correlazione prima che un messaggio venga inviato o ricevuto, usare <xref:System.ServiceModel.Activities.InitializeCorrelation> per inizializzarla.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizzo dell'ActivityDesigner InitializeCorrelation

Accedere a **InitializeCorrelation** Activity Designer nella categoria **messaggistica** della **casella degli strumenti**.

È possibile trascinare l'ActivityDesigner **InitializeCorrelation** dalla **casella degli strumenti** e rilasciarlo nell'area di progettazione flussi di lavoro. Se si elimina l'ActivityDesigner, viene creata un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> con una <xref:System.Activities.Activity.DisplayName%2A> predefinita di InitializeCorrelation. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **InitializeCorrelation** o nella casella **DisplayName** della finestra **proprietà** .

È possibile specificare il <xref:System.ServiceModel.Activities.CorrelationHandle> nel campo **correlazione** nella finestra **Proprietà** dell'area di progettazione dell'attività **InitializeCorrelation** .

Per visualizzare la finestra di dialogo **Inizializza correlazione** in cui è possibile specificare l'handle di correlazione e le coppie chiave-valore usate per inizializzarlo, selezionare il pulsante con i puntini di sospensione accanto al campo **CorrelationData** nella finestra **proprietà** . In alternativa, selezionare "Visualizza..." Testo suggerimento sull'area dell'ActivityDesigner **InitializeCorrelation** . Per ulteriori informazioni sull'utilizzo di questa finestra di dialogo, vedere l'articolo relativo alla finestra di [dialogo Editor raccolta di tipi](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Proprietà di InitializeCorrelation

Nella tabella seguente vengono illustrate le proprietà <xref:System.ServiceModel.Activities.InitializeCorrelation> e viene descritto il modo in cui vengono utilizzate nella finestra di progettazione. Queste proprietà possono essere modificate nella finestra **Proprietà** o in Progettazione flussi di lavoro area.

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>. Il valore predefinito è InitializeCorrelation.<br /><br /> Anche se l'uso di un valore non predefinito per il <xref:System.Activities.Activity.DisplayName%2A> descrittivo non è strettamente obbligatorio, è consigliabile.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> usato per associare le attività del flusso di lavoro nella correlazione.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dizionario dei dati di correlazione che mette in correlazione i messaggi all'istanza del flusso di lavoro.<br /><br /> Utilizzare la finestra di dialogo **Inizializza correlazione** per configurare la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Per altre informazioni sulla finestra di dialogo Usa questa finestra di dialogo, vedere l'articolo sulla finestra di [dialogo Editor raccolta di tipi](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Vedere anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)