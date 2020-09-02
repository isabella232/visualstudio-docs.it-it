---
title: ActivityDesigner di assegnazione Progettazione flussi di lavoro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83a01c96b64dcd55adfd775efc266063efbab27d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875943"
---
# <a name="assign-activity-designer"></a>ActivityDesigner Assign

L'ActivityDesigner **assign** viene usato per creare e configurare un' <xref:System.Activities.Statements.Assign> attività.

## <a name="the-assign-activity"></a>Attività Assign

L'attività <xref:System.Activities.Statements.Assign> assegna un valore a una variabile o a un argomento.

### <a name="using-the-assign-activity-designer"></a>Utilizzo dell'ActivityDesigner Assign

L'ActivityDesigner **assign** è disponibile nella categoria **primitive** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** . in alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere CTRL + ALT + X.

È possibile trascinare l'ActivityDesigner **assign** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro in cui vengono inserite le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Se si elimina l'ActivityDesigner **assign** , viene creata un' <xref:System.Activities.Statements.Assign> attività con un **DisplayName** predefinito Assign. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **assign** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-assign-properties"></a>Proprietà di Assign

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Assign> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate in Progettazione flussi di lavoro area.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.Assign>. L'impostazione predefinita è Assign. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.Assign.To%2A>|Vero|La variabile o l'argomento cui è assegnata la proprietà <xref:System.Activities.Statements.Assign.Value%2A>. Il valore deve essere un identificatore di Visual Basic valido. Per impostare la proprietà, digitare un'espressione Visual Basic nella casella **a** dell'ActivityDesigner **assign** o nella griglia delle proprietà.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Vero|Valore assegnato alla variabile. Per impostare <xref:System.Activities.Statements.Assign.Value%2A> , digitare un'espressione Visual Basic nella casella **valore** dell'ActivityDesigner **assign** o nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Primitive](../workflow-designer/primitives-activity-designers.md)
- [Ritardo](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)