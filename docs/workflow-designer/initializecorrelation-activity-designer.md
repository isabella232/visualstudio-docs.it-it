---
title: ActivityDesigner Progettazione flussi di lavoro-InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aadb526e50351c8344c8b265dca3364637d1ff0c
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875566"
---
# <a name="initializecorrelation-activity-designer"></a>ActivityDesigner InitializeCorrelation

L'ActivityDesigner **InitializeCorrelation** viene usato per creare e configurare un' <xref:System.ServiceModel.Activities.InitializeCorrelation> attività. L' <xref:System.ServiceModel.Activities.InitializeCorrelation> attività stabilisce una correlazione tra i messaggi prima di inviarli o riceverli.

## <a name="the-initializecorrelation-activity"></a>Attività InitializeCorrelation

Un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> viene usata per inizializzare le correlazioni senza inviare o ricevere un messaggio. La correlazione viene in genere inizializzata quando si invia o riceve un messaggio. Se è necessario stabilire la correlazione prima che un messaggio venga inviato o ricevuto, usare <xref:System.ServiceModel.Activities.InitializeCorrelation> per inizializzarla.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizzo dell'ActivityDesigner InitializeCorrelation

Accedere a **InitializeCorrelation** Activity Designer nella categoria **messaggistica** della **casella degli strumenti**.

È possibile trascinare l'ActivityDesigner **InitializeCorrelation** dalla **casella degli strumenti** e rilasciarlo nell'area di progettazione flussi di lavoro. Se si elimina l'ActivityDesigner, viene creata un' <xref:System.ServiceModel.Activities.InitializeCorrelation> attività con il valore predefinito <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **InitializeCorrelation** o nella casella **DisplayName** della finestra **Proprietà** .

Il <xref:System.ServiceModel.Activities.CorrelationHandle> può essere specificato nel campo **correlazione** nella finestra **Proprietà** della superficie dell'ActivityDesigner **InitializeCorrelation** .

Per visualizzare la finestra di dialogo **Inizializza correlazione** in cui è possibile specificare l'handle di correlazione e le coppie chiave-valore usate per inizializzarlo, selezionare il pulsante con i puntini di sospensione accanto al campo **CorrelationData** nella finestra **proprietà** . In alternativa, selezionare "Visualizza..." Testo suggerimento sull'area dell'ActivityDesigner **InitializeCorrelation** . Per ulteriori informazioni sull'utilizzo di questa finestra di dialogo, vedere l'articolo relativo alla finestra di [dialogo Editor raccolta di tipi](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Proprietà di InitializeCorrelation

Nella tabella seguente sono illustrate le <xref:System.ServiceModel.Activities.InitializeCorrelation> proprietà e viene descritto come vengono utilizzate nella finestra di progettazione. Queste proprietà possono essere modificate nella finestra **Proprietà** o in Progettazione flussi di lavoro area.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>. Il valore predefinito è InitializeCorrelation.<br /><br /> Anche se l'uso di un valore non predefinito per friendly <xref:System.Activities.Activity.DisplayName%2A> non è strettamente obbligatorio, è consigliabile.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|Falso|<xref:System.ServiceModel.Activities.CorrelationHandle> usato per associare le attività del flusso di lavoro nella correlazione.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|Falso|Dizionario dei dati di correlazione che mette in correlazione i messaggi all'istanza del flusso di lavoro.<br /><br /> Utilizzare la finestra di dialogo **Inizializza correlazione** per configurare <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> . Per altre informazioni sulla finestra di dialogo Usa questa finestra di dialogo, vedere l'articolo sulla finestra di [dialogo Editor raccolta di tipi](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Vedi anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)