---
title: ActivityDesigner Progettazione flussi di lavoro-mantenuti
description: Informazioni sull'attività di salvataggio permanente e su come usare l'ActivityDesigner di salvataggio permanente per creare e configurare un'attività di salvataggio permanente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3daa7cef76d2448cc7bcda66a967a3406bb2352c
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435573"
---
# <a name="persist-activity-designer"></a>ActivityDesigner Persist

L'ActivityDesigner **rese** viene utilizzato per creare e configurare un' <xref:System.Activities.Statements.Persist> attività.

## <a name="the-persist-activity"></a>Attività Persist

L'attività <xref:System.Activities.Statements.Persist> salva un flusso di lavoro su disco, se possibile. Non è possibile eseguire l'attività <xref:System.Activities.Statements.Persist> in un'area non permanente come, ad esempio, all'interno di un'attività <xref:System.Activities.Statements.TransactionScope>. Se si utilizza un' <xref:System.Activities.Statements.Persist> attività in un ambito non di persistenza, viene generata un'eccezione in fase di esecuzione.

### <a name="using-the-persist-activity-designer"></a>Utilizzo dell'ActivityDesigner Persist

L'ActivityDesigner di **salvataggio** è disponibile nella categoria **Runtime** della **casella degli strumenti** , a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** . in alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere CTRL + ALT + X.

È possibile trascinare l'ActivityDesigner di **salvataggio** dalla **casella degli strumenti** e rilasciarlo nell'area di progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Verrà creata un' <xref:System.Activities.Statements.Persist> attività con un valore **DisplayName** predefinito di permanente. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner di **mantenimento** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-persist-properties"></a>Proprietà di Persist

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Persist> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate in Progettazione flussi di lavoro area.

|Nome proprietà|Obbligatoria|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.Persist>. Il valore predefinito è Persist. Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedere anche

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
