---
title: ActivityDesigner Progettazione flussi di lavoro-Delay
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
ms.openlocfilehash: abfd625a248c14f646683c7b035065e6ca096f68
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876112"
---
# <a name="delay-activity-designer"></a>ActivityDesigner Delay

La finestra di progettazione dell'attività **delay** viene utilizzata per creare e configurare un' <xref:System.Activities.Statements.Delay> attività.

## <a name="the-delay-activity"></a>Attività Delay

L'attività <xref:System.Activities.Statements.Delay> ritarda l'esecuzione di un flusso di lavoro per una quantità di tempo specificata.

### <a name="use-the-delay-activity-designer"></a>Usare l'ActivityDesigner Delay

L'ActivityDesigner **delay** è disponibile nella categoria **primitive** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** della progettazione flussi di lavoro. In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere **CTRL** + **ALT** + **X**.

È possibile trascinare l'ActivityDesigner **delay** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Se si elimina l'ActivityDesigner, viene creata un' <xref:System.Activities.Statements.Delay> attività con il valore predefinito <xref:System.Activities.Activity.DisplayName%2A> delay. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **delay** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-delay-properties"></a>Proprietà Delay

Nella tabella seguente sono illustrate le <xref:System.Activities.Statements.Delay> proprietà e viene descritto come vengono utilizzate nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area di Progettazione flussi di lavoro.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.Delay>. Il valore predefinito è Delay. Sebbene il <xref:System.Activities.Activity.DisplayName%2A> valore non sia strettamente obbligatorio, è consigliabile utilizzarne uno.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Vero|Durata del ritardo del flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà. Per specificare tale durata, digitare un valore <xref:System.TimeSpan> letterale nel formato 00:00:00 o un'espressione Visual Basic.|

## <a name="see-also"></a>Vedere anche

- [Primitive](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Activity Designer Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)