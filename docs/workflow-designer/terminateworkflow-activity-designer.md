---
title: ActivityDesigner TerminateWorkflow
description: In Progettazione flussi di lavoro informazioni su come usare l'ActivityDesigner TerminateWorkflow per creare e configurare un'attività TerminateWorkflow.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 5d4fe0b77c91b36440cbb760b3e192af453c4f58
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963391"
---
# <a name="terminateworkflow-activity-designer"></a>ActivityDesigner TerminateWorkflow

**L'ActivityDesigner TerminateWorkflow** viene usato per creare e configurare <xref:System.Activities.Statements.TerminateWorkflow> un'attività.

## <a name="the-terminateworkflow-activity"></a>Attività TerminateWorkflow

L'attività <xref:System.Activities.Statements.TerminateWorkflow> termina l'esecuzione di un flusso di lavoro.

### <a name="using-the-terminateworkflow-activity-designer"></a>Utilizzo dell'ActivityDesigner TerminateWorkflow

L'ActivityDesigner **TerminateWorkflow** è disponibile nella categoria **Runtime** della Casella degli strumenti **,** a  cui si accede facendo clic sulla scheda **Casella** degli strumenti . In alternativa, scegliere Casella degli strumenti dal **menu** Visualizza o CTRL+ALT+X.

**L'ActivityDesigner TerminateWorkflow** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie Progettazione flussi di lavoro ogni volta che vengono in genere inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Verrà creata <xref:System.Activities.Statements.TerminateWorkflow> un'attività con un **valore DisplayName predefinito** di TerminateWorkflow. Può <xref:System.Activities.Activity.DisplayName%2A> essere modificato nell'intestazione **dell'ActivityDesigner TerminateWorkflow** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-terminateworkflow-properties"></a>Proprietà di TerminateWorkflow

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.TerminateWorkflow> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune di esse possono essere modificate Progettazione flussi di lavoro superficie.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.TerminateWorkflow>. Il valore predefinito è TerminateWorkflow. Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|Falso|Eccezione da generare quando viene terminato il flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|Falso|Motivo che spiega perché è stato terminato il flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà.|

## <a name="see-also"></a>Vedi anche

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)
