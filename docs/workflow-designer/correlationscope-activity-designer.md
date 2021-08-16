---
title: Progettazione flussi di lavoro - ActivityDesigner CorrelationScope
description: Informazioni su come usare l'ActivityDesigner CorrelationScope per creare e configurare un'attività CorrelationScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: b958aa6568461ac9e753bfa8a0e304b3cabaf4e3687e648a9fc9853d113fe51a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121383911"
---
# <a name="correlationscope-activity-designer"></a>ActivityDesigner CorrelationScope

**L'ActivityDesigner CorrelationScope** viene usato per creare e configurare un'attività che fornisce la gestione implicita delle <xref:System.ServiceModel.Activities.CorrelationScope> attività di messaggistica figlio tramite un <xref:System.ServiceModel.Activities.CorrelationHandle> oggetto .

## <a name="the-correlationscope-activity"></a>Attività CorrelationScope

La proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> specifica l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per gestire le attività di messaggistica figlio. Le attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> contenute in <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> sono configurate per usare la proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> dell'attività <xref:System.ServiceModel.Activities.CorrelationScope> contenitore per eseguire la correlazione.

### <a name="use-the-correlationscope-activity-designer"></a>Usare CorrelationScope ActivityDesigner

L'ActivityDesigner **CorrelationScope** è  disponibile nella categoria Messaggistica della Casella  degli strumenti **,** a cui si accede facendo clic sulla scheda Casella degli strumenti sul lato sinistro del Progettazione flussi di lavoro. In alternativa, selezionare **Casella degli** **strumenti** dal menu Visualizza o premere **CTRL** +  + **ALT+X.**

**L'ActivityDesigner CorrelationScope** può essere trascinato dalla **casella** degli strumenti e rilasciato nella Progettazione flussi di lavoro superficie. Verrà creata <xref:System.ServiceModel.Activities.CorrelationScope> un'attività con **un valore DisplayName predefinito** di CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A>L'oggetto può essere modificato nell'intestazione dell'ActivityDesigner **CorrelationScope** o nella **casella DisplayName** della **finestra** Proprietà.

Per specificare l'oggetto utilizzato dalle attività di messaggistica figlio, selezionare il pulsante con i puntini di sospensione accanto al campo <xref:System.ServiceModel.Activities.CorrelationHandle> **CorrelatesWith** nella finestra Proprietà per visualizzare la finestra di dialogo **Editor** espressioni .  È possibile impostare questa proprietà anche nell'area di progettazione dell'attività.

Le attività con ambito all'interno della correlazione vengono specificate eliminando le finestre di progettazione all'interno della **casella Corpo** all'interno della finestra di **progettazione CorrelationScope.**

### <a name="the-correlationscope-properties"></a>Proprietà CorrelationScope

Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.CorrelationScope> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella **finestra** Proprietà o nella Progettazione flussi di lavoro e spesso in entrambe.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|Falso|Consente di specificare l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per gestire le attività di messaggistica figlio. Se non si imposta questa proprietà, <xref:System.ServiceModel.Activities.CorrelationScope> crea automaticamente un oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> implicito.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|Falso|Consente di specificare le attività all'interno dell'ambito della correlazione.|

## <a name="see-also"></a>Vedi anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Ricevere](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)