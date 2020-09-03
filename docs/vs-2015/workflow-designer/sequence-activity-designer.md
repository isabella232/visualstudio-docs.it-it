---
title: ActivityDesigner Sequence | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3acf02ab478eee244557e04f19f78ba2d5f0b950
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663254"
---
# <a name="sequence-activity-designer"></a>ActivityDesigner Sequence
L'attività <xref:System.Activities.Statements.Sequence> contiene una raccolta ordinata di attività figlio eseguite nell'ordine.

 Un altro sistema per eseguire un set delle attività nell'ordine consiste nell'usare un'attività <xref:System.Activities.Statements.Flowchart>. Si consiglia di utilizzare il [diagramma](../workflow-designer/flowchart-activity-designer.md) di flusso quando si dispone di un semplice flusso del programma di diramazione o ciclo che si desidera modellare graficamente.

## <a name="using-the-sequence-activity-designer"></a>Utilizzo dell'ActivityDesigner Sequence
 Per aggiungere un' <xref:System.Activities.Statements.Sequence> attività, trascinare l'ActivityDesigner **Sequence** dalla **casella degli strumenti** e rilasciarlo sulla [!INCLUDE[wfd1](../includes/wfd1-md.md)] superficie. Per aggiungere un'attività figlio a questa <xref:System.Activities.Statements.Sequence> attività, trascinare un'altra attività dalla **casella degli strumenti** e rilasciarla sul triangolo nella casella con il testo del suggerimento "rilasciare l'attività".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività della sequenza in Progettazione flussi di lavoro 
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Sequence> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Sequence> nell'intestazione. Il valore predefinito è Sequence. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedere anche
 [Flowchart](../workflow-designer/flowchart-activity-designer.md) [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md) diagramma di flusso