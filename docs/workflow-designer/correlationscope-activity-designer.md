---
title: Finestra di progettazione del flusso di lavoro - ActivityDesigner Correlationscope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4b7eb7586eeb746bdeb3d28dfcc5fb14fe7bd6f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976605"
---
# <a name="correlationscope-activity-designer"></a>ActivityDesigner CorrelationScope

Il **CorrelationScope** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.ServiceModel.Activities.CorrelationScope> attività che fornisce la gestione implicita di attività di messaggistica figlio mediante un <xref:System.ServiceModel.Activities.CorrelationHandle> oggetto.

## <a name="the-correlationscope-activity"></a>Attività CancellationScope

La proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> specifica l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per gestire le attività di messaggistica figlio. Le attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> contenute in <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> sono configurate per usare la proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> dell'attività <xref:System.ServiceModel.Activities.CorrelationScope> contenitore per eseguire la correlazione.

### <a name="using-the-correlationscope-activity-designer"></a>Utilizzo dell'ActivityDesigner CorrelationScope
 Il **CorrelationScope** ActivityDesigner sono reperibili il **messaggistica** categoria del **casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti** scheda sul lato sinistro della finestra di progettazione del flusso di lavoro (in alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

 Il **CorrelationScope** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro. Crea un <xref:System.ServiceModel.Activities.CorrelationScope> attività con valore predefinito è **DisplayName** correlationscope. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **CorrelationScope** ActivityDesigner o nel **DisplayName** casella del **proprietà** finestra.

 Per specificare il <xref:System.ServiceModel.Activities.CorrelationHandle> utilizzato dalle attività di messaggistica figlio, fare clic su pulsante con i puntini di sospensione accanto il **CorrelatesWith** campo **proprietà** finestra per visualizzare il **Editor espressioni**  la finestra di dialogo. È possibile impostare questa proprietà anche nell'area di progettazione dell'attività.

 L'attività il cui ambito all'interno della correlazione vengono specificate rilasciando le finestre di progettazione all'interno di **corpo** casella all'interno di **CorrelationScope** progettazione.

### <a name="the-correlationscope-properties"></a>Proprietà di CancellationScope
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.CorrelationScope> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Queste proprietà possono essere modificati in **proprietà** finestra o nella superficie di progettazione di progettazione flussi di lavoro e spesso in entrambe.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Consente di specificare l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per gestire le attività di messaggistica figlio. Se non si imposta questa proprietà, <xref:System.ServiceModel.Activities.CorrelationScope> crea automaticamente un oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> implicito.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Consente di specificare le attività all'interno dell'ambito della correlazione.|

## <a name="see-also"></a>Vedere anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Ricezione](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)