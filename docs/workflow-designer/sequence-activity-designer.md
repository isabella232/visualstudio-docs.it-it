---
title: ActivityDesigner Progettazione flussi di lavoro Sequence
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 116e8c31a6d7cad2e5c6da95bc66e34a0d11163a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649942"
---
# <a name="sequence-activity-designer"></a>ActivityDesigner Sequence

L'attività <xref:System.Activities.Statements.Sequence> contiene una raccolta ordinata di attività figlio eseguite nell'ordine.

Un altro sistema per eseguire un set delle attività nell'ordine consiste nell'usare un'attività <xref:System.Activities.Statements.Flowchart>. Si consiglia di utilizzare il [diagramma](../workflow-designer/flowchart-activity-designer.md) di flusso quando si dispone di un semplice flusso del programma di diramazione o ciclo che si desidera modellare graficamente.

## <a name="using-the-sequence-activity-designer"></a>Utilizzo dell'ActivityDesigner Sequence

Per aggiungere un'attività <xref:System.Activities.Statements.Sequence>, trascinare l'ActivityDesigner **Sequence** dalla **casella degli strumenti** e rilasciarlo sull'area Progettazione flussi di lavoro. Per aggiungere un'attività figlio a questa attività <xref:System.Activities.Statements.Sequence>, trascinare un'altra attività dalla **casella degli strumenti** e rilasciarla sul triangolo nella casella con il testo del suggerimento "rilasciare l'attività".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività della sequenza in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Sequence> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Sequence> nell'intestazione. Il valore predefinito è Sequence. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedere anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)