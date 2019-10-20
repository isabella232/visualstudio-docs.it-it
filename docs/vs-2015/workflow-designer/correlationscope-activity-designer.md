---
title: ActivityDesigner ActivityDesigner CorrelationScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6ffcfd63d60ab6f085b5cb2a793e8bf17a50d8e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656918"
---
# <a name="correlationscope-activity-designer"></a>ActivityDesigner CorrelationScope
L'ActivityDesigner **ActivityDesigner CorrelationScope** viene utilizzato per creare e configurare un'attività <xref:System.ServiceModel.Activities.CorrelationScope> che fornisce la gestione implicita delle attività di messaggistica figlio utilizzando un oggetto <xref:System.ServiceModel.Activities.CorrelationHandle>.

## <a name="the-correlationscope-activity"></a>Attività CancellationScope
 La proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> specifica l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per gestire le attività di messaggistica figlio. Le attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> contenute in <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> sono configurate per usare la proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> dell'attività <xref:System.ServiceModel.Activities.CorrelationScope> contenitore per eseguire la correlazione.

### <a name="using-the-correlationscope-activity-designer"></a>Utilizzo dell'ActivityDesigner CorrelationScope
 L'ActivityDesigner **ActivityDesigner CorrelationScope** è disponibile nella categoria **messaggistica** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** sul lato sinistro del [!INCLUDE[wfd2](../includes/wfd2-md.md)]. in alternativa, selezionare **barra degli** strumenti dal Menu **Visualizza** o CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **ActivityDesigner CorrelationScope** dalla **casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Verrà creata un'attività di <xref:System.ServiceModel.Activities.CorrelationScope> con un valore **DisplayName** predefinito di ActivityDesigner CorrelationScope. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **ActivityDesigner CorrelationScope** o nella casella **DisplayName** della finestra **proprietà** .

 Per specificare la <xref:System.ServiceModel.Activities.CorrelationHandle> utilizzata dalle attività di messaggistica figlio, fare clic sul pulsante con i puntini di sospensione accanto al campo **CorrelatesWith** nella finestra **Proprietà** per visualizzare la finestra di dialogo **Editor espressioni** . È possibile impostare questa proprietà anche nell'area di progettazione dell'attività.

 Le attività nell'ambito della correlazione vengono specificate eliminando le finestre di progettazione all'interno della casella **corpo** all'interno di **ActivityDesigner CorrelationScope** designer.

### <a name="the-correlationscope-properties"></a>Proprietà di CancellationScope
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.CorrelationScope> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella finestra **Proprietà** o nell'area di progettazione [!INCLUDE[wfd2](../includes/wfd2-md.md)] e spesso in entrambi.

|Nome proprietà|Richiesto|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Consente di specificare l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per gestire le attività di messaggistica figlio. Se non si imposta questa proprietà, <xref:System.ServiceModel.Activities.CorrelationScope> crea automaticamente un oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> implicito.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Consente di specificare le attività all'interno dell'ambito della correlazione.|

## <a name="see-also"></a>Vedere anche
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)