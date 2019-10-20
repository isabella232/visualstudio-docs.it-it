---
title: ActivityDesigner Progettazione flussi di lavoro-FinalState
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: b8f25167f3a67e2d1349354ce568c076697e3e73
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650464"
---
# <a name="finalstate-activity-designer"></a>ActivityDesigner FinalState

La finestra di progettazione di <xref:System.Activities.Core.Presentation.FinalState> viene usata per creare un <xref:System.Activities.Statements.State> che termina un'istanza della macchina a stati.

## <a name="using-the-finalstate-activity-designer"></a>Uso di ActivityDesigner FinalState

**FinalState** Designer viene usato per creare un <xref:System.Activities.Statements.State> preconfigurato come stato di terminazione in una macchina a Stati. Un <xref:System.Activities.Statements.State> creato con l'ActivityDesigner <xref:System.Activities.Core.Presentation.FinalState> dispone della proprietà <xref:System.Activities.Statements.State.IsFinal%2A> impostata su **true**, non ha alcuna attività <xref:System.Activities.Statements.State.Exit%2A> e non ha origine alcuna transizione. Per usare l'ActivityDesigner <xref:System.Activities.Core.Presentation.FinalState> per aggiungere un'attività di <xref:System.Activities.Statements.State> preconfigurata come stato di terminazione in una macchina a Stati, trascinare l'ActivityDesigner **FinalState** dalla sezione macchina a **Stati** della **casella degli strumenti** e rilasciarlo nel Progettazione flussi di lavoro. Un ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState> può essere rilasciato in <xref:System.Activities.Statements.StateMachine> e le transizioni possono essere aggiunte successivamente, o una transizione può essere creata quando viene rilasciato un ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState>. Per ulteriori informazioni sulla creazione di transizioni, vedere la pagina relativa alla [transizione](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di stato in Progettazione flussi di lavoro

Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Core.Presentation.FinalState> che possono essere impostate usando la finestra di progettazione e viene descritta la modalità di utilizzo nella finestra di progettazione. Alcune di queste proprietà possono essere modificate nella griglia delle proprietà, mentre altre possono essere modificate nell'area di progettazione.

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.State> nell'intestazione. Il valore predefinito è **state**. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner. <xref:System.Activities.Statements.State.DisplayName%2A> è usato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Statements.State.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Specifica l'azione che si verifica quando viene eseguita la transizione di questo stato. Questo valore può essere impostato trascinando un'attività dalla **casella degli strumenti** e rilasciandola nella sezione <xref:System.Activities.Statements.State.Entry%2A> dello stato.|

## <a name="see-also"></a>Vedere anche

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Stato](../workflow-designer/state-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)