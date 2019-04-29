---
title: Finestra di progettazione del flusso di lavoro, ActivityDesigner TerminateWorkflow
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 662366e3b0c0558170c117104d20a1bcb6417615
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62434033"
---
# <a name="terminateworkflow-activity-designer"></a>ActivityDesigner TerminateWorkflow

Il **TerminateWorkflow** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.TerminateWorkflow> attività.

## <a name="the-terminateworkflow-activity"></a>Attività TerminateWorkflow

L'attività <xref:System.Activities.Statements.TerminateWorkflow> termina l'esecuzione di un flusso di lavoro.

### <a name="using-the-terminateworkflow-activity-designer"></a>Utilizzo dell'ActivityDesigner TerminateWorkflow

Il **TerminateWorkflow** ActivityDesigner è reperibile nel **Runtime** categoria del **della casella degli strumenti**, accessibile facendo clic di **dellacaselladeglistrumenti** della scheda (in alternativa, selezionare **casella degli strumenti** dal **vista** menu o CTRL + ALT + X.)

Il **TerminateWorkflow** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Ciò consente di creare un <xref:System.Activities.Statements.TerminateWorkflow> attività con un valore predefinito **DisplayName** terminateworkflow. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **TerminateWorkflow** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.

### <a name="the-terminateworkflow-properties"></a>Proprietà di TerminateWorkflow

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.TerminateWorkflow> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e alcune di esse possono essere modificate nell'area di progettazione del flusso di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.TerminateWorkflow>. Il valore predefinito è TerminateWorkflow. Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Eccezione da generare quando viene terminato il flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Motivo che spiega perché è stato terminato il flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)