---
title: Progettazione flussi di lavoro - ActivityDesigner diagramma di flusso
description: Informazioni su come usare l'attività Diagramma di flusso per creare flussi di lavoro che definiscono e gestiscono controlli di flusso complessi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 948d4536f28440671fdba2a7a9931e0da66d7834
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963467"
---
# <a name="flowchart-activity-designer"></a>ActivityDesigner Diagramma di flusso

L'attività <xref:System.Activities.Statements.Flowchart> viene usata per creare flussi di lavoro che definiscono e gestiscono controlli di flusso complessi. Un <xref:System.Activities.Statements.Flowchart> oggetto può essere creato nel codice o usando Progettazione flussi di lavoro. Questo argomento illustra l'Progettazione flussi di lavoro di lavoro. L Progettazione flussi di lavoro ActivityDesigner del flusso di lavoro consente agli sviluppatori di creare flussi di lavoro in modo naturale.

## <a name="the-flowchart-activity"></a>Attività Flowchart

<xref:System.Activities.Statements.Flowchart> specifica un elemento <xref:System.Activities.Statements.Flowchart.StartNode%2A> univoco che viene eseguito all'avvio del flusso di lavoro e usa una rete di <xref:System.Activities.Statements.Flowchart.Nodes%2A> collegati per creare cicli arbitrari o per deviare in un determinato momento il flusso dell'esecuzione in un altro punto del flusso di lavoro.

### <a name="using-the-flowchart-activity-designer"></a>Utilizzo dell'ActivityDesigner Flowchart

L'ActivityDesigner diagramma di flusso è disponibile nella categoria **Diagramma** di flusso della Casella degli strumenti **,** a cui si accede facendo clic sulla scheda **Casella** degli strumenti nella Progettazione flussi di lavoro.  In alternativa, selezionare **Casella degli** **strumenti** dal menu Visualizza o premere **CTRL** +  + **ALT+X.**

**L'ActivityDesigner** del diagramma di  flusso può essere trascinato dalla casella degli strumenti e rilasciato sull'area Progettazione flussi di lavoro in cui gli ActivityDesigner vengono normalmente posizionati, come attività radice o come figlio di un'altra attività del flusso di controllo. Se **l'ActivityDesigner** del diagramma di flusso viene rilasciato su una superficie Progettazione flussi di lavoro vuota, crea un'attività che per impostazione predefinita si presenta in una visualizzazione espansa in cui il nodo iniziale che avvia l'esecuzione viene rappresentato come una palla <xref:System.Activities.Statements.Flowchart> verde. Se **l'ActivityDesigner** del diagramma di flusso viene rilasciato in un'altra attività del flusso di controllo, si presenta in una visualizzazione ridotta a icona che può essere espansa facendo doppio clic sull'ActivityDesigner **diagramma** di flusso. Qualsiasi attività nella casella **degli strumenti** può essere trascinata direttamente nell'ActivityDesigner **del** diagramma di flusso, incluse altre attività del flusso di controllo.

Dopo aver trascinato vari ActivityDesigner nell Progettazione flussi di lavoro canvas, gli oggetti che rappresentano possono essere collegati tra loro <xref:System.Activities.Activity> per specificare l'ordine di esecuzione. Per creare un collegamento tra un'attività di origine e un'attività di destinazione, spostare il mouse sulla finestra di progettazione dell'attività di origine in modo da visualizzare handle quadrati su ciascun lato. Fare clic su uno degli handle quadrati e, tenendo premuto il pulsante del mouse, trascinarlo su uno degli handle visualizzati in modo simile intorno all'attività di destinazione durante il passaggio del mouse. Dopo aver rilasciato il pulsante del mouse, verrà creato un collegamento tra queste due attività rappresentato da una freccia che collega la finestra di progettazione di origine a quella di destinazione.

### <a name="flowchart-activity-properties"></a>Proprietà dell'attività Flowchart

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Flowchart> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome visualizzato nell'intestazione dell'ActivityDesigner. Il valore predefinito è Flowchart. Il valore può essere modificato nella **finestra** Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|Falso|Raccolta di variabili incluse nell'ambito di questa attività <xref:System.Activities.Statements.Flowchart> per condividere lo stato tra le relative attività figlio.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|Falso|<xref:System.Activities.Statements.FlowNode> eseguito all'avvio di <xref:System.Activities.Statements.Flowchart>.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|Falso|Contiene la raccolta di oggetti <xref:System.Activities.Statements.FlowNode> inclusi nell'attività <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>Vedi anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
