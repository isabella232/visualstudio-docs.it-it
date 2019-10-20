---
title: ActivityDesigner Progettazione flussi di lavoro-StateMachine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 2e79e1db2cc6c46361afa7412cdeb493418c0365
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649904"
---
# <a name="statemachine-activity-designer"></a>ActivityDesigner StateMachine

L'attività <xref:System.Activities.Statements.StateMachine> contiene una raccolta di stati e modella i flussi di lavoro usando il paradigma comune della macchina a stati.

## <a name="using-the-statemachine-activity-designer"></a>Utilizzo dell'ActivityDesigner StateMachine

Per aggiungere un'attività <xref:System.Activities.Statements.StateMachine>, trascinare l'ActivityDesigner **StateMachine** dalla sezione **macchina a stati** della **casella degli strumenti** e rilasciarla sull'area di progettazione flussi di lavoro. Per aggiungere uno stato figlio a questa attività <xref:System.Activities.Statements.StateMachine>, trascinare un <xref:System.Activities.Statements.State> o <xref:System.Activities.Core.Presentation.FinalState> dalla **casella degli strumenti** e rilasciarlo su **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività StateMachine in Progettazione flussi di lavoro

Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.StateMachine> che possono essere impostate usando la finestra di progettazione flussi di lavoro e viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia della proprietà e alcune nell'area della finestra di progettazione.

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.StateMachine> nell'intestazione. Il valore predefinito è **StateMachine**. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner. <xref:System.Activities.Activity.DisplayName%2A> è usato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedere anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)