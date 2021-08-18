---
title: Progettazione flussi di lavoro - ActivityDesigner State
description: Informazioni sull'attività StateMachine e su come usare l'ActivityDesigner State per aggiungere uno stato a un flusso di lavoro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 2a0d23bedea24a68285e90faf8ee39fd46de90fc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135273"
---
# <a name="state-activity-designer"></a>ActivityDesigner State

Un oggetto <xref:System.Activities.Statements.State> rappresenta uno stato in cui può trovarsi una macchina a stati.

## <a name="using-the-state-activity-designer"></a>Utilizzo della Finestra di progettazione di stato.

Per aggiungere un oggetto a un flusso di lavoro, trascinare l'ActivityDesigner State dalla sezione State Machine della casella degli strumenti e rilasciarlo su un'attività <xref:System.Activities.Statements.State>    <xref:System.Activities.Statements.StateMachine> nell'area Progettazione flussi di lavoro stato. Un'attività di <xref:System.Activities.Statements.State> può essere rilasciata in <xref:System.Activities.Statements.StateMachine> e le transizioni possono essere aggiunte successivamente, o una transizione può essere creata quando viene rilasciata un'attività di <xref:System.Activities.Statements.State>. Per aggiungere un'attività e creare una transizione in un passaggio, trascinare un'attività State dalla sezione Macchina a stati della Casella degli strumenti e passarla su un altro stato nella finestra di progettazione <xref:System.Activities.Statements.State> del flusso di lavoro.    Quando l'oggetto <xref:System.Activities.Statements.State> trascinato si trova su un altro oggetto <xref:System.Activities.Statements.State>, intorno a <xref:System.Activities.Statements.State> verranno visualizzati quattro triangoli. Se l'oggetto <xref:System.Activities.Statements.State> viene rilasciato su uno dei quattro triangoli, viene aggiunto alla macchina a stati e una transizione viene creata dall'oggetto <xref:System.Activities.Statements.State> di origine all'oggetto <xref:System.Activities.Statements.State> di destinazione rilasciato. Per altre informazioni, vedere [Transizione.](../workflow-designer/transition-activity-designer.md)

### <a name="state-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di stato in Progettazione flussi di lavoro 

Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.State> che possono essere impostate usando la finestra di progettazione flussi di lavoro e viene descritta la modalità di utilizzo nella finestra di progettazione. Alcune di queste proprietà possono essere modificate nella griglia delle proprietà, mentre altre possono essere modificate nell'area di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.State> nell'intestazione. Il valore predefinito è **State.** Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner. <xref:System.Activities.Statements.State.DisplayName%2A> è usato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Statements.State.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.State.Entry%2A>|Falso|Specifica l'azione che si verifica quando viene eseguita la transizione di questo stato. Quando <xref:System.Activities.Statements.State> l'attività viene espansa, questo valore può  essere impostato trascinando un'attività dalla Casella degli strumenti e rilasciarla nella **sezione Entry** dello stato.|
|<xref:System.Activities.Statements.State.Exit%2A>|Falso|Specifica l'azione che si verifica quando viene eseguita la transizione da questo stato. Quando <xref:System.Activities.Statements.State> l'attività viene espansa, questo valore può  essere impostato trascinando un'attività dalla Casella degli strumenti e rilasciarla nella **sezione Exit** dello stato.|
|<xref:System.Activities.Statements.State.Transitions%2A>|Falso|Vengono elencate le transizioni possibili originate da <xref:System.Activities.Statements.State>. Ogni elemento nell'elenco ha un collegamento a <xref:System.Activities.Statements.Transition> collegato e a <xref:System.Activities.Statements.State> di destinazione. Una volta fatto clic sul collegamento la finestra di progettazione passerà a una visualizzazione espansa di <xref:System.Activities.Statements.Transition> o di <xref:System.Activities.Statements.State>.|

## <a name="see-also"></a>Vedi anche

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Transizione](../workflow-designer/transition-activity-designer.md)
