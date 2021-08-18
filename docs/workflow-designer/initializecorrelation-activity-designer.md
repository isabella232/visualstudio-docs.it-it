---
title: ActivityDesigner InitializeCorrelation
description: In Progettazione flussi di lavoro informazioni su come usare l'ActivityDesigner InitializeCorrelation per creare e configurare un'attività InitializeCorrelation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: aff2353f0ea681935ff576545f6eb14b957f2c1d58136e240917bd4f86653f75
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440500"
---
# <a name="initializecorrelation-activity-designer"></a>ActivityDesigner InitializeCorrelation

**L'ActivityDesigner InitializeCorrelation** viene usato per creare e configurare <xref:System.ServiceModel.Activities.InitializeCorrelation> un'attività. <xref:System.ServiceModel.Activities.InitializeCorrelation>L'attività stabilisce una correlazione tra i messaggi prima di inviarli o riceverli.

## <a name="the-initializecorrelation-activity"></a>Attività InitializeCorrelation

Un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> viene usata per inizializzare le correlazioni senza inviare o ricevere un messaggio. La correlazione viene in genere inizializzata quando si invia o riceve un messaggio. Se è necessario stabilire la correlazione prima che un messaggio venga inviato o ricevuto, usare <xref:System.ServiceModel.Activities.InitializeCorrelation> per inizializzarla.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizzo dell'ActivityDesigner InitializeCorrelation

Accedere **all'ActivityDesigner InitializeCorrelation** nella **categoria Messaggistica** della casella **degli strumenti**.

**L'ActivityDesigner InitializeCorrelation** può essere trascinato dalla **casella** degli strumenti e rilasciato nell Progettazione flussi di lavoro surface. L'eliminazione dell'ActivityDesigner crea <xref:System.ServiceModel.Activities.InitializeCorrelation> un'attività con il <xref:System.Activities.Activity.DisplayName%2A> valore predefinito InitializeCorrelation. <xref:System.Activities.Activity.DisplayName%2A>L'oggetto può essere modificato nell'intestazione dell'ActivityDesigner **InitializeCorrelation** o nella casella **DisplayName** della **finestra** Proprietà.

È <xref:System.ServiceModel.Activities.CorrelationHandle> possibile specificare nel campo  **Correlazione** della finestra Proprietà nell'area dell'ActivityDesigner **InitializeCorrelation.**

Per visualizzare  la finestra di dialogo Inizializza correlazione in cui è possibile specificare l'handle di correlazione e le coppie  chiave-valore usate per inizializzarlo, selezionare il pulsante con i puntini di sospensione accanto al **campo CorrelationData** nella finestra Proprietà. In caso contrario, selezionare "Visualizza..." Testo del suggerimento **nell'area dell'ActivityDesigner InitializeCorrelation.** Per altre informazioni sull'uso di questa finestra di dialogo, vedere [l'articolo Finestra di dialogo Editor raccolta tipi.](../workflow-designer/type-collection-editor-dialog-box.md)

### <a name="the-initializecorrelation-properties"></a>Proprietà di InitializeCorrelation

La tabella seguente illustra le <xref:System.ServiceModel.Activities.InitializeCorrelation> proprietà e ne descrive l'uso nella finestra di progettazione. Queste proprietà possono essere modificate nella **finestra Proprietà** o in Progettazione flussi di lavoro superficie.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>. Il valore predefinito è InitializeCorrelation.<br /><br /> Anche se l'uso di un valore non predefinito per l'elemento descrittivo non è <xref:System.Activities.Activity.DisplayName%2A> strettamente necessario, è consigliabile.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|Falso|<xref:System.ServiceModel.Activities.CorrelationHandle> usato per associare le attività del flusso di lavoro nella correlazione.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|Falso|Dizionario dei dati di correlazione che mette in correlazione i messaggi all'istanza del flusso di lavoro.<br /><br /> Usare la **finestra di dialogo** Inizializza correlazione per configurare <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> . Per altre informazioni sull'uso di questa finestra di dialogo, vedere [l'articolo Finestra di dialogo Editor raccolta tipi.](../workflow-designer/type-collection-editor-dialog-box.md)|

## <a name="see-also"></a>Vedi anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)