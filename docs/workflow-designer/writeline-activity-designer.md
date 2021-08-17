---
title: Progettazione flussi di lavoro - ActivityDesigner WriteLine
description: Informazioni sull'attività WriteLine e su come usare l'ActivityDesigner WriteLine per creare e configurare un'attività WriteLine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: daa88d858af5b99beda41631c6c139be9aff425d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025173"
---
# <a name="writeline-activity-designer"></a>ActivityDesigner WriteLine

**L'ActivityDesigner WriteLine** viene usato per creare e configurare <xref:System.Activities.Statements.WriteLine> un'attività.

## <a name="the-writeline-activity"></a>Attività WriteLine

L'attività <xref:System.Activities.Statements.WriteLine> scrive il testo in un oggetto <xref:System.IO.TextWriter> specificato. Se non è specificato alcun oggetto <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> scrive il testo sulla console.

### <a name="using-the-writeline-activity-designer"></a>Utilizzo dell'ActivityDesigner WriteLine

Accedere **all'ActivityDesigner WriteLine** nella **categoria Primitive** della casella **degli strumenti**. **L'ActivityDesigner WriteLine** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie di Progettazione flussi di lavoro ogni volta che vengono in genere inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . In questo modo viene creata un'attività <xref:System.Activities.Statements.WriteLine> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito WriteLine. <xref:System.Activities.Activity.DisplayName%2A>L'oggetto può essere modificato nell'intestazione dell'ActivityDesigner **WriteLine** o nella **casella DisplayName** della griglia delle proprietà.

### <a name="the-writeline-properties"></a>Proprietà di WriteLine

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.WriteLine> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune di esse possono essere modificate Progettazione flussi di lavoro superficie.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.WriteLine>. Il valore predefinito è WriteLine. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|Falso|Testo da scrivere. Per impostare la proprietà, digitare un Visual Basic  nella casella Testo dell'ActivityDesigner **WriteLine** o nella griglia delle proprietà.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Falso|Oggetto <xref:System.IO.TextWriter> nel quale <xref:System.Activities.Statements.WriteLine> scrive <xref:System.Activities.Statements.WriteLine.Text%2A>. Il valore predefinito corrisponde alla console.|

## <a name="see-also"></a>Vedi anche

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Ritardo](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
