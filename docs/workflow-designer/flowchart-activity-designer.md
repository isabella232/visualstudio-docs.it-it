---
title: Finestra di progettazione del flusso di lavoro - Activity Designer Flowchart
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3468e4e09f8e31ae6b3e8bf7a49b7a1c368b3e73
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877686"
---
# <a name="flowchart-activity-designer"></a>ActivityDesigner Diagramma di flusso

L'attività <xref:System.Activities.Statements.Flowchart> viene usata per creare flussi di lavoro che definiscono e gestiscono controlli di flusso complessi. Oggetto <xref:System.Activities.Statements.Flowchart> possono essere creati nel codice o tramite Progettazione del flusso di lavoro. Questo argomento vengono illustrate l'esperienza di progettazione del flusso di lavoro. L'ActivityDesigner del flusso di lavoro di progettazione del flusso di lavoro consente agli sviluppatori di creare flussi di lavoro in modo naturale.

## <a name="the-flowchart-activity"></a>Attività Flowchart

<xref:System.Activities.Statements.Flowchart> specifica un elemento <xref:System.Activities.Statements.Flowchart.StartNode%2A> univoco che viene eseguito all'avvio del flusso di lavoro e usa una rete di <xref:System.Activities.Statements.Flowchart.Nodes%2A> collegati per creare cicli arbitrari o per deviare in un determinato momento il flusso dell'esecuzione in un altro punto del flusso di lavoro.

### <a name="using-the-flowchart-activity-designer"></a>Utilizzo dell'ActivityDesigner Flowchart

Il **diagramma di flusso** ActivityDesigner è reperibile nel **diagramma di flusso** categoria del **della casella degli strumenti**, accessibile facendo clic di **della casella degli strumenti**scheda nella finestra di progettazione del flusso di lavoro. In alternativa, selezionare **della casella degli strumenti** dal **View** dal menu oppure premere **Ctrl**+**Alt** + **X**.

Il **diagramma di flusso** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che vengono in genere posizionate le attività, come un'attività radice o come il elemento figlio di un'altra attività del flusso di controllo. Se il **diagramma di flusso** ActivityDesigner viene eliminata in un'area di progettazione del flusso di lavoro vuota, viene creato un <xref:System.Activities.Statements.Flowchart> attività, che per impostazione predefinita si manifesta in una visualizzazione espansa in cui è il nodo iniziale che avvia l'esecuzione rappresentato come una palla di colore verde. Se il **diagramma di flusso** ActivityDesigner viene inserito in un'altra attività del flusso di controllo, si presenta una vista ridotta a icona che può essere espanso facendo doppio clic il **Flowchart** ActivityDesigner. Qualsiasi attività nel **casella degli strumenti** possono essere trascinati direttamente il **diagramma di flusso** ActivityDesigner, tra cui altre attività del flusso di controllo.

Dopo aver rilasciato diversi ActivityDesigner nell'area di disegno, finestra di progettazione del flusso di lavoro di <xref:System.Activities.Activity> possono essere collegati gli oggetti che rappresentano per specificare l'ordine di esecuzione. Per creare un collegamento tra un'attività di origine e un'attività di destinazione, spostare il mouse sulla finestra di progettazione dell'attività di origine in modo da visualizzare handle quadrati su ciascun lato. Fare clic su uno degli handle quadrati e, tenendo premuto il pulsante del mouse, trascinarlo su uno degli handle visualizzati in modo simile intorno all'attività di destinazione durante il passaggio del mouse. Dopo aver rilasciato il pulsante del mouse, verrà creato un collegamento tra queste due attività rappresentato da una freccia che collega la finestra di progettazione di origine a quella di destinazione.

### <a name="flowchart-activity-properties"></a>Proprietà dell'attività Flowchart

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Flowchart> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome visualizzato nell'intestazione dell'ActivityDesigner. Il valore predefinito è Flowchart. Il valore può essere modificato nel **proprietà** finestra o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|Raccolta di variabili incluse nell'ambito di questa attività <xref:System.Activities.Statements.Flowchart> per condividere lo stato tra le relative attività figlio.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|<xref:System.Activities.Statements.FlowNode> eseguito all'avvio di <xref:System.Activities.Statements.Flowchart>.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|Contiene la raccolta di oggetti <xref:System.Activities.Statements.FlowNode> inclusi nell'attività <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>Vedere anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)