---
title: Progettazione flussi di lavoro - Assegnare ActivityDesigner
description: Informazioni su come usare l'ActivityDesigner assegna per creare e configurare un'attività Assegna e come l'attività Assegna assegna un valore a una variabile o a un argomento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: b10e12302b2fd11a2e4aec9266e5ad517a1edb4ad47e8b64dde44df79847825e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408071"
---
# <a name="assign-activity-designer"></a>ActivityDesigner Assign

**L'ActivityDesigner** Assegna viene usato per creare e configurare <xref:System.Activities.Statements.Assign> un'attività.

## <a name="the-assign-activity"></a>Attività Assign

L'attività <xref:System.Activities.Statements.Assign> assegna un valore a una variabile o a un argomento.

### <a name="using-the-assign-activity-designer"></a>Utilizzo dell'ActivityDesigner Assign

L'ActivityDesigner Assegna è disponibile nella categoria **Primitive** della Casella  degli strumenti **,** a  cui si accede facendo clic sulla scheda Casella degli strumenti .In alternativa, selezionare Casella degli strumenti dal **menu** Visualizza o CTRL+ALT+X. 

**L'ActivityDesigner** Assegna può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie di Progettazione flussi di lavoro in cui vengono posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . L'eliminazione **di Assign** ActivityDesigner crea <xref:System.Activities.Statements.Assign> un'attività con **displayName predefinito** di Assign. <xref:System.Activities.Activity.DisplayName%2A>L'oggetto può essere modificato nell'intestazione di **Assegna** ActivityDesigner o nella **casella DisplayName** della griglia delle proprietà.

### <a name="the-assign-properties"></a>Proprietà di Assign

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Assign> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune di esse possono essere modificate Progettazione flussi di lavoro superficie.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.Assign>. L'impostazione predefinita è Assign. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.Assign.To%2A>|Vero|La variabile o l'argomento cui è assegnata la proprietà <xref:System.Activities.Statements.Assign.Value%2A>. Il valore deve essere un identificatore Visual Basic valido. Per impostare la proprietà, digitare un'Visual Basic nella casella **A** in **Assegna** ActivityDesigner o nella griglia delle proprietà.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Vero|Valore assegnato alla variabile. Per impostare <xref:System.Activities.Statements.Assign.Value%2A> , digitare un'Visual Basic nella casella **Valore** in **Assegna** ActivityDesigner o nella griglia delle proprietà.|

## <a name="see-also"></a>Vedi anche

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Ritardo](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)