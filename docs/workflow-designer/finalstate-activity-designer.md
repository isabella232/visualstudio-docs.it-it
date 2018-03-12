---
title: ActivityDesigner FinalState | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a5b9b8cc1fc0bdb390e1bf32a6a8f262b435a157
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="finalstate-activity-designer"></a>ActivityDesigner FinalState
La finestra di progettazione di <xref:System.Activities.Core.Presentation.FinalState> viene usata per creare un <xref:System.Activities.Statements.State> che termina un'istanza della macchina a stati.

## <a name="using-the-finalstate-activity-designer"></a>Uso di ActivityDesigner FinalState
 Il **FinalState** designer viene utilizzato per creare un <xref:System.Activities.Statements.State> che è preconfigurato come stato finale in una macchina a stati. A <xref:System.Activities.Statements.State> creato usando il <xref:System.Activities.Core.Presentation.FinalState> ActivityDesigner è relativo <xref:System.Activities.Statements.State.IsFinal%2A> proprietà impostata su **true**, non ha alcun <xref:System.Activities.Statements.State.Exit%2A> attività e non presenta alcuna transizione che originano da esso. Utilizzare il <xref:System.Activities.Core.Presentation.FinalState> ActivityDesigner per aggiungere un <xref:System.Activities.Statements.State> attività che è preconfigurato come stato finale in una macchina a stati, trascinare il **FinalState** ActivityDesigner dal **macchina a stati**sezione la **della casella degli strumenti** e rilasciarla nella finestra di progettazione del flusso di lavoro. Un ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState> può essere rilasciato in <xref:System.Activities.Statements.StateMachine> e le transizioni possono essere aggiunte successivamente, o una transizione può essere creata quando viene rilasciato un ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState>. Per ulteriori informazioni sulla creazione di transizioni, vedere [transizione](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di stato in Progettazione flussi di lavoro 
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Core.Presentation.FinalState> che possono essere impostate usando la finestra di progettazione e viene descritta la modalità di utilizzo nella finestra di progettazione. Alcune di queste proprietà possono essere modificate nella griglia delle proprietà, mentre altre possono essere modificate nell'area di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.State> nell'intestazione. Il valore predefinito è **stato**. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner. <xref:System.Activities.Statements.State.DisplayName%2A> è usato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Statements.State.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Specifica l'azione che si verifica quando viene eseguita la transizione di questo stato. Questo valore può essere impostato trascinando un'attività dal **della casella degli strumenti** e rilasciandola il <xref:System.Activities.Statements.State.Entry%2A> sezione dello stato.|

## <a name="see-also"></a>Vedere anche

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Stato](../workflow-designer/state-activity-designer.md)
- [transizione](../workflow-designer/transition-activity-designer.md)