---
title: Progettazione flussi di lavoro - ActivityDesigner StateMachine
description: Informazioni su come l'attività StateMachine contiene una raccolta di stati e modella i flussi di lavoro usando il paradigma familiare della macchina a stati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: ca75e366d1c7e8c14b5bc59b0155cb99aabaf76464460226526979a42d54ed5f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440409"
---
# <a name="statemachine-activity-designer"></a>ActivityDesigner StateMachine

L'attività <xref:System.Activities.Statements.StateMachine> contiene una raccolta di stati e modella i flussi di lavoro usando il paradigma comune della macchina a stati.

## <a name="using-the-statemachine-activity-designer"></a>Utilizzo dell'ActivityDesigner StateMachine

Per aggiungere <xref:System.Activities.Statements.StateMachine> un'attività, trascinare l'ActivityDesigner **StateMachine** dalla sezione **Macchina** a stati della casella degli strumenti e rilasciarla nell'Progettazione flussi di lavoro lavoro.  Per aggiungere uno stato figlio a questa attività, trascinare un oggetto o dalla Casella degli strumenti e <xref:System.Activities.Statements.StateMachine> <xref:System.Activities.Statements.State> <xref:System.Activities.Core.Presentation.FinalState> rilasciarlo in **StateMachine.** 

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività StateMachine in Progettazione flussi di lavoro

Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.StateMachine> che possono essere impostate usando la finestra di progettazione flussi di lavoro e viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia della proprietà e alcune nell'area della finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.StateMachine> nell'intestazione. Il valore predefinito è **StateMachine.** Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner. <xref:System.Activities.Activity.DisplayName%2A> è usato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedi anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
