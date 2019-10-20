---
title: ActivityDesigner Progettazione flussi di lavoro-WriteLine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 475755fed96f8341c45b8260b414658967b3284c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649757"
---
# <a name="writeline-activity-designer"></a>ActivityDesigner WriteLine

L'ActivityDesigner **WriteLine** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.WriteLine>.

## <a name="the-writeline-activity"></a>Attività WriteLine

L'attività <xref:System.Activities.Statements.WriteLine> scrive il testo in un oggetto <xref:System.IO.TextWriter> specificato. Se non è specificato alcun oggetto <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> scrive il testo sulla console.

### <a name="using-the-writeline-activity-designer"></a>Utilizzo dell'ActivityDesigner WriteLine

Accedere all'ActivityDesigner **WriteLine** nella categoria **primitive** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **WriteLine** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.WriteLine> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito WriteLine. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **WriteLine** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-writeline-properties"></a>Proprietà di WriteLine

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.WriteLine> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate in Progettazione flussi di lavoro area.

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.WriteLine>. Il valore predefinito è WriteLine. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Testo da scrivere. Per impostare la proprietà, digitare un'espressione Visual Basic nella casella di **testo** dell'ActivityDesigner **WriteLine** o nella griglia delle proprietà.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|Oggetto <xref:System.IO.TextWriter> nel quale <xref:System.Activities.Statements.WriteLine> scrive <xref:System.Activities.Statements.WriteLine.Text%2A>. Il valore predefinito corrisponde alla console.|

## <a name="see-also"></a>Vedere anche

- [Primitive](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)