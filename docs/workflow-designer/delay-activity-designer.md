---
title: Finestra di progettazione del flusso di lavoro - ActivityDesigner Delay
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e22c80712bcb0c792fb929ae85b84912122a0bc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="delay-activity-designer"></a>ActivityDesigner Delay

Il **ritardo** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Delay> attività.

## <a name="the-delay-activity"></a>Attività Delay

L'attività <xref:System.Activities.Statements.Delay> ritarda l'esecuzione di un flusso di lavoro per una quantità di tempo specificata.

### <a name="using-the-delay-activity-designer"></a>Utilizzo dell'ActivityDesigner Delay

Il **ritardo** ActivityDesigner è reperibile nella **primitive** categoria del **casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti**scheda della finestra di progettazione del flusso di lavoro (in alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

Il **ritardo** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.Delay> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito Delay. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **ritardo** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-delay-properties"></a>Proprietà di Delay

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Delay> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e di essi alcuni possono essere modificate nell'area Designerdesigner del flusso di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Delay>. Il valore predefinito è Delay. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Durata del ritardo del flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà. Per specificare tale durata, digitare un valore <xref:System.TimeSpan> letterale nel formato 00:00:00 o un'espressione Visual Basic.|

## <a name="see-also"></a>Vedere anche

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [assegnare](../workflow-designer/assign-activity-designer.md)
- [Activity Designer Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)