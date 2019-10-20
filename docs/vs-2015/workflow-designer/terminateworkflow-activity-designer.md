---
title: ActivityDesigner TerminateWorkflow | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c204c14818a9c6e6fb0a46e6234b550838f3b1a4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607090"
---
# <a name="terminateworkflow-activity-designer"></a>ActivityDesigner TerminateWorkflow
L'ActivityDesigner **TerminateWorkflow** viene usato per creare e configurare un'attività <xref:System.Activities.Statements.TerminateWorkflow>.

## <a name="the-terminateworkflow-activity"></a>Attività TerminateWorkflow
 L'attività <xref:System.Activities.Statements.TerminateWorkflow> termina l'esecuzione di un flusso di lavoro.

### <a name="using-the-terminateworkflow-activity-designer"></a>Utilizzo dell'ActivityDesigner TerminateWorkflow
 L'ActivityDesigner **TerminateWorkflow** è disponibile nella categoria **Runtime** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** . in alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** oppure premere CTRL + ALT + X.)

 È possibile trascinare l'ActivityDesigner **TerminateWorkflow** dalla **casella degli strumenti** e rilasciarlo nell'area [!INCLUDE[wfd2](../includes/wfd2-md.md)] quando vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Verrà creata un'attività di <xref:System.Activities.Statements.TerminateWorkflow> con un valore **DisplayName** predefinito di TerminateWorkflow. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **TerminateWorkflow** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-terminateworkflow-properties"></a>Proprietà di TerminateWorkflow
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.TerminateWorkflow> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nome proprietà|Richiesto|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.TerminateWorkflow>. Il valore predefinito è TerminateWorkflow. Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Eccezione da generare quando viene terminato il flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Motivo che spiega perché è stato terminato il flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche
 [Runtime](../workflow-designer/runtime-activity-designers.md) [permanente](../workflow-designer/persist-activity-designer.md)