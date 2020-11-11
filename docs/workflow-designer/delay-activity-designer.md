---
title: ActivityDesigner Progettazione flussi di lavoro-Delay
description: Informazioni sulle attività Delay e su come usare l'ActivityDesigner Delay per creare e configurare un'attività Delay.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e6bbadcbabbe1dbd274c48f2325217c17d3933d
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438087"
---
# <a name="delay-activity-designer"></a>ActivityDesigner Delay

La finestra di progettazione dell'attività **delay** viene utilizzata per creare e configurare un' <xref:System.Activities.Statements.Delay> attività.

## <a name="the-delay-activity"></a>Attività Delay

L'attività <xref:System.Activities.Statements.Delay> ritarda l'esecuzione di un flusso di lavoro per una quantità di tempo specificata.

### <a name="use-the-delay-activity-designer"></a>Usare l'ActivityDesigner Delay

L'ActivityDesigner **delay** è disponibile nella categoria **primitive** della **casella degli strumenti** , a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** della progettazione flussi di lavoro. In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere **CTRL** + **ALT** + **X**.

È possibile trascinare l'ActivityDesigner **delay** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Se si elimina l'ActivityDesigner, viene creata un' <xref:System.Activities.Statements.Delay> attività con il valore predefinito <xref:System.Activities.Activity.DisplayName%2A> delay. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **delay** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-delay-properties"></a>Proprietà Delay

Nella tabella seguente sono illustrate le <xref:System.Activities.Statements.Delay> proprietà e viene descritto come vengono utilizzate nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area di Progettazione flussi di lavoro.

|Nome proprietà|Obbligatoria|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.Delay>. Il valore predefinito è Delay. Sebbene il <xref:System.Activities.Activity.DisplayName%2A> valore non sia strettamente obbligatorio, è consigliabile utilizzarne uno.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Vero|Durata del ritardo del flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà. Per specificare tale durata, digitare un valore <xref:System.TimeSpan> letterale nel formato 00:00:00 o un'espressione Visual Basic.|

## <a name="see-also"></a>Vedere anche

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Activity Designer Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)