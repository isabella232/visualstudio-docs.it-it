---
title: Progettazione flussi di lavoro - Assegnare ActivityDesigner
description: Informazioni su come usare l'ActivityDesigner Assign per creare e configurare un'attività Assign e su come l'attività Assign assegna un valore a una variabile o a un argomento.
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
ms.openlocfilehash: 524d55608b8cc75deea1c876ab03a4a437ad2049
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963319"
---
# <a name="assign-activity-designer"></a>ActivityDesigner Assign

L'ActivityDesigner **Assign** viene usato per creare e configurare <xref:System.Activities.Statements.Assign> un'attività.

## <a name="the-assign-activity"></a>Attività Assign

L'attività <xref:System.Activities.Statements.Assign> assegna un valore a una variabile o a un argomento.

### <a name="using-the-assign-activity-designer"></a>Utilizzo dell'ActivityDesigner Assign

L'ActivityDesigner **Assegna** è disponibile nella categoria **Primitive** della Casella  degli strumenti **,** a  cui si accede facendo clic sulla scheda Casella degli strumenti . In alternativa, scegliere Casella degli strumenti dal **menu** Visualizza o CTRL+ALT+X.

L'ActivityDesigner **Assign** può essere  trascinato dalla casella degli strumenti e rilasciato nella Progettazione flussi di lavoro in cui vengono posizionate le attività, ad esempio all'interno di <xref:System.Activities.Statements.Sequence> un oggetto . L'eliminazione **dell'ActivityDesigner Assign** crea <xref:System.Activities.Statements.Assign> un'attività con **il valore predefinito DisplayName** di Assign. <xref:System.Activities.Activity.DisplayName%2A>L'oggetto può essere modificato nell'intestazione dell'ActivityDesigner **Assign** o nella **casella DisplayName** della griglia delle proprietà.

### <a name="the-assign-properties"></a>Proprietà di Assign

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Assign> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune di esse possono essere modificate Progettazione flussi di lavoro superficie.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.Assign>. L'impostazione predefinita è Assign. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.Assign.To%2A>|Vero|La variabile o l'argomento cui è assegnata la proprietà <xref:System.Activities.Statements.Assign.Value%2A>. Il valore deve essere un identificatore Visual Basic valido. Per impostare la proprietà, digitare un Visual Basic  nella casella A dell'ActivityDesigner **Assign** o nella griglia delle proprietà.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Vero|Valore assegnato alla variabile. Per impostare , digitare un'Visual Basic nella casella Valore <xref:System.Activities.Statements.Assign.Value%2A> dell'ActivityDesigner **Assegna** o nella griglia delle proprietà. |

## <a name="see-also"></a>Vedi anche

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Ritardo](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)