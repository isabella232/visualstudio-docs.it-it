---
title: Progettazione flussi di lavoro - ActivityDesigner FinalState
description: Informazioni su come usare la finestra di progettazione FinalState per creare uno stato che termina un'istanza della macchina a stati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: a44cf8413e60b0dd5049f7ce31d699e6cfbbca47
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099087"
---
# <a name="finalstate-activity-designer"></a>ActivityDesigner FinalState

La finestra di progettazione di <xref:System.Activities.Core.Presentation.FinalState> viene usata per creare un <xref:System.Activities.Statements.State> che termina un'istanza della macchina a stati.

## <a name="using-the-finalstate-activity-designer"></a>Uso di ActivityDesigner FinalState

La **finestra di progettazione FinalState** viene usata per creare un oggetto preconfigurato come stato di <xref:System.Activities.Statements.State> terminazione in una macchina a stati. La <xref:System.Activities.Statements.State> proprietà di un oggetto creato usando l'ActivityDesigner è impostata su true, non ha alcuna attività e nessuna transizione <xref:System.Activities.Core.Presentation.FinalState> da essa <xref:System.Activities.Statements.State.IsFinal%2A>  <xref:System.Activities.Statements.State.Exit%2A> originata. Per usare l'ActivityDesigner per aggiungere un'attività preconfigurata come stato di terminazione in una macchina a stati, trascinare <xref:System.Activities.Core.Presentation.FinalState> <xref:System.Activities.Statements.State> **l'ActivityDesigner FinalState**  dalla sezione **Macchina** a stati della casella degli strumenti e rilasciarla nella finestra di progettazione del flusso di lavoro. Un ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState> può essere rilasciato in <xref:System.Activities.Statements.StateMachine> e le transizioni possono essere aggiunte successivamente, o una transizione può essere creata quando viene rilasciato un ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState>. Per altre informazioni sulla creazione di transizioni, vedere [Transizione.](../workflow-designer/transition-activity-designer.md)

### <a name="state-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di stato in Progettazione flussi di lavoro 

Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Core.Presentation.FinalState> che possono essere impostate usando la finestra di progettazione e viene descritta la modalità di utilizzo nella finestra di progettazione. Alcune di queste proprietà possono essere modificate nella griglia delle proprietà, mentre altre possono essere modificate nell'area di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.State> nell'intestazione. Il valore predefinito è **State.** Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner. <xref:System.Activities.Statements.State.DisplayName%2A> è usato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Statements.State.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.State.Entry%2A>|Falso|Specifica l'azione che si verifica quando viene eseguita la transizione di questo stato. Questo valore può essere impostato trascinando un'attività dalla **Casella** degli strumenti e rilasciarla nella sezione <xref:System.Activities.Statements.State.Entry%2A> dello stato.|

## <a name="see-also"></a>Vedi anche

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)
- [Transizione](../workflow-designer/transition-activity-designer.md)