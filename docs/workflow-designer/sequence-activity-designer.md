---
title: Progettazione flussi di lavoro - ActivityDesigner Sequence
description: Informazioni su come l'attività Sequence contiene una raccolta ordinata di attività figlio eseguite in ordine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 7980e01f23dab3ddb927af207e4e2ce67ab515a7
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963510"
---
# <a name="sequence-activity-designer"></a>ActivityDesigner Sequence

L'attività <xref:System.Activities.Statements.Sequence> contiene una raccolta ordinata di attività figlio eseguite nell'ordine.

Un altro sistema per eseguire un set delle attività nell'ordine consiste nell'usare un'attività <xref:System.Activities.Statements.Flowchart>. È consigliabile [usare il diagramma di](../workflow-designer/flowchart-activity-designer.md) flusso quando si dispone di un semplice flusso di programma di diramazione o ciclo che si vuole modellare in modo diagrammatico.

## <a name="using-the-sequence-activity-designer"></a>Utilizzo dell'ActivityDesigner Sequence

Per aggiungere <xref:System.Activities.Statements.Sequence> un'attività, trascinare **l'ActivityDesigner Sequence** dalla Casella **degli** strumenti e rilasciarlo nell'area Progettazione flussi di lavoro sequenza. Per aggiungere un'attività figlio a questa attività, trascinare un'altra attività dalla casella degli strumenti e rilasciarla sul triangolo nella casella con il testo del suggerimento <xref:System.Activities.Statements.Sequence> "Drop activity  here".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività della sequenza in Progettazione flussi di lavoro 

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Sequence> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Sequence> nell'intestazione. Il valore predefinito è Sequence. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedi anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)