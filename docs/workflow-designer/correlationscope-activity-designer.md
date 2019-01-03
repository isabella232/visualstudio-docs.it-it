---
title: Finestra di progettazione del flusso di lavoro, ActivityDesigner Correlationscope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0562b113e91bb9485eaf356085715522b1b39bc3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829920"
---
# <a name="correlationscope-activity-designer"></a>ActivityDesigner CorrelationScope

Il **CorrelationScope** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.ServiceModel.Activities.CorrelationScope> attività che fornisce la gestione implicita delle attività di messaggistica figlio mediante un <xref:System.ServiceModel.Activities.CorrelationHandle> oggetto.

## <a name="the-correlationscope-activity"></a>Attività Cancellationscope

La proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> specifica l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per gestire le attività di messaggistica figlio. Le attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> contenute in <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> sono configurate per usare la proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> dell'attività <xref:System.ServiceModel.Activities.CorrelationScope> contenitore per eseguire la correlazione.

### <a name="use-the-correlationscope-activity-designer"></a>Utilizzo dell'ActivityDesigner Correlationscope

Il **CorrelationScope** ActivityDesigner è reperibile nel **messaggistica** categoria del **della casella degli strumenti**, accessibile facendo clic di **dellacaselladeglistrumenti** scheda sul lato sinistro della finestra di progettazione del flusso di lavoro. In alternativa, selezionare **della casella degli strumenti** dal **View** dal menu oppure premere **Ctrl**+**Alt** + **X**.

Il **CorrelationScope** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro. Ciò consente di creare un <xref:System.ServiceModel.Activities.CorrelationScope> attività con un valore predefinito **DisplayName** correlationscope. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **CorrelationScope** ActivityDesigner o nel **DisplayName** finestra del **proprietà** finestra.

Per specificare il <xref:System.ServiceModel.Activities.CorrelationHandle> utilizzato dalle attività di messaggistica figlio, selezionare il pulsante con puntini di sospensione accanto ad il **CorrelatesWith** campo **delle proprietà** finestra per visualizzare il **espressione Editor** nella finestra di dialogo. È possibile impostare questa proprietà anche nell'area di progettazione dell'attività.

L'attività il cui ambito all'interno della correlazione vengono specificate rilasciando le finestre di progettazione all'interno di **corpo** finestra all'interno del **CorrelationScope** progettazione.

### <a name="the-correlationscope-properties"></a>Proprietà di Cancellationscope

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.CorrelationScope> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Queste proprietà possono essere modificati in **proprietà** finestra o nell'area di progettazione del flusso di lavoro e spesso in entrambe.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Consente di specificare l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per gestire le attività di messaggistica figlio. Se non si imposta questa proprietà, <xref:System.ServiceModel.Activities.CorrelationScope> crea automaticamente un oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> implicito.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Consente di specificare le attività all'interno dell'ambito della correlazione.|

## <a name="see-also"></a>Vedere anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)