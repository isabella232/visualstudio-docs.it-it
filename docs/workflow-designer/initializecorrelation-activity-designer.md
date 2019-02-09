---
title: Finestra di progettazione del flusso di lavoro, ActivityDesigner InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 496aefb2679edd87c892c54f44b14876b4ebce5b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953217"
---
# <a name="initializecorrelation-activity-designer"></a>ActivityDesigner InitializeCorrelation

Il **InitializeCorrelation** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività. Il <xref:System.ServiceModel.Activities.InitializeCorrelation> attività stabilisce una correlazione tra i messaggi prima di inviare o riceverli.

## <a name="the-initializecorrelation-activity"></a>Attività InitializeCorrelation

Un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> viene usata per inizializzare le correlazioni senza inviare o ricevere un messaggio. La correlazione viene in genere inizializzata quando si invia o riceve un messaggio. Se è necessario stabilire la correlazione prima che un messaggio venga inviato o ricevuto, usare <xref:System.ServiceModel.Activities.InitializeCorrelation> per inizializzarla.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizzo dell'ActivityDesigner InitializeCorrelation

Accesso di **InitializeCorrelation** ActivityDesigner nel **messaggistica** categoria del **della casella degli strumenti**.

Il **InitializeCorrelation** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro. La finestra di progettazione di attività di rilascio crea un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività predefinito <xref:System.Activities.Activity.DisplayName%2A> initializecorrelation. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **InitializeCorrelation** ActivityDesigner o nel **DisplayName** finestra del **proprietà** finestra.

Il <xref:System.ServiceModel.Activities.CorrelationHandle> può essere specifica nel **correlazione** campo **delle proprietà** finestra nel **InitializeCorrelation** superficie dell'ActivityDesigner.

Per visualizzare il **Inizializza correlazione** dove è possibile specificare l'handle di correlazione e le coppie chiave-valore utilizzate per inizializzare, selezionare il pulsante con puntini di sospensione accanto alla finestra di dialogo il **CorrelationData** campo **proprietà** finestra. In alternativa, selezionare il testo di suggerimento "Visualizza in corso" sul **InitializeCorrelation** superficie dell'ActivityDesigner. Per altre informazioni sull'uso di questa finestra di dialogo, vedere la [finestra di dialogo Editor raccolta di tipo](../workflow-designer/type-collection-editor-dialog-box.md) articolo.

### <a name="the-initializecorrelation-properties"></a>Proprietà di InitializeCorrelation

La tabella seguente illustra il <xref:System.ServiceModel.Activities.InitializeCorrelation> proprietà e viene descritto l'utilizzo nella finestra di progettazione. Queste proprietà possono essere modificate nella **proprietà** finestra o nell'area di progettazione del flusso di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>. Il valore predefinito è InitializeCorrelation.<br /><br /> Sebbene l'uso di un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A> non è strettamente necessaria, è consigliabile.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> usato per associare le attività del flusso di lavoro nella correlazione.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dizionario dei dati di correlazione che mette in correlazione i messaggi all'istanza del flusso di lavoro.<br /><br /> Usare la **Inizializza correlazione** finestra di dialogo per configurare il <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Per altre informazioni sull'utilizzo questa finestra di dialogo, vedere la [finestra di dialogo Editor raccolta di tipo](../workflow-designer/type-collection-editor-dialog-box.md) articolo.|

## <a name="see-also"></a>Vedere anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)