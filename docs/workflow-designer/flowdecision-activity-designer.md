---
title: ActivityDesigner Progettazione flussi di lavoro-FlowDecision
description: Informazioni su come il nodo FlowDecision è un nodo condizionale che fornisce un ramo per il flusso di controllo in una delle due alternative.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 77570557563b4aca3109f5bcbdebd16c7af09144
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938434"
---
# <a name="flowdecision-activity-designer"></a>ActivityDesigner FlowDecision

Il nodo <xref:System.Activities.Statements.FlowDecision> è un nodo condizionale che fornisce due rami alternativi per il flusso di controllo a seconda che venga soddisfatta una condizione specificata. Se il flusso richiede più di due rami, usare invece <xref:System.Activities.Statements.FlowSwitch%601>.

## <a name="the-flowdecision-node"></a>Nodo FlowDecision

Usare <xref:System.Activities.Statements.FlowDecision> quando per il flusso è possibile creare due rami in due percorsi. Un nodo <xref:System.Activities.Statements.FlowDecision> presenta un oggetto <xref:System.Activities.Statements.FlowDecision.Condition%2A> e un oggetto <xref:System.Activities.Statements.FlowNode> associato a ognuno dei due possibili risultati: <xref:System.Activities.Statements.FlowDecision.True%2A> o <xref:System.Activities.Statements.FlowDecision.False%2A>. L'elemento <xref:System.Activities.Statements.FlowDecision.Condition%2A> viene valutato e il valore di questa valutazione determina il successivo nodo <xref:System.Activities.Statements.FlowNode> da elaborare nell'oggetto <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Utilizzo dell'ActivityDesigner FlowDecision

**FlowDecision** designer è disponibile nella categoria diagramma di **flusso** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** nella progettazione flussi di lavoro. In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere **CTRL** + **ALT** + **X**.

La finestra di progettazione **FlowDecision** può essere trascinata dalla **casella degli strumenti** e rilasciata nell'area Progettazione flussi di lavoro all'interno di un ActivityDesigner **Flowchart** . Viene creata una <xref:System.Activities.Statements.FlowDecision> **decisione** con etichetta all'interno dell' <xref:System.Activities.Statements.Flowchart> attività. Passare il mouse sulla finestra di progettazione e visualizzare gli handle quadrati **veri** e **falsi** per i due rami.

Dopo aver trascinato **FlowDecision** designer e altre finestre di progettazione nel **diagramma di flusso**, i nodi possono essere collegati tra loro per specificare l'ordine di esecuzione. Per creare un collegamento tra un nodo di origine (inclusi i rami **true** e **false** di **FlowDecision**) e un nodo di destinazione, il puntatore del mouse sulla finestra di progettazione del nodo di origine e sui quadratini di ridimensionamento vengono visualizzati su ogni lato. Fare clic su uno degli handle quadrati e, tenendo premuto il pulsante del mouse, trascinarlo su uno degli handle visualizzati in modo simile intorno al nodo di destinazione durante il passaggio del mouse. Dopo aver rilasciato il pulsante del mouse, verrà creato un collegamento tra questi due nodi rappresentato da una freccia che collega la finestra di progettazione di origine a quella di destinazione.

L'espressione che dichiara l'oggetto <xref:System.Activities.Statements.FlowDecision.Condition%2A> può essere digitata nella casella **condizione** della finestra **proprietà** facendo clic sul punto in cui il testo del suggerimento indica "immettere un'espressione VB".

### <a name="the-flowdecision-properties"></a>Proprietà di FlowDecision

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.FlowDecision> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Vero|Condizione che determina il percorso seguito dal controllo di flusso.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|Falso|Percorso seguito dal controllo di flusso se viene soddisfatta <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|Falso|Percorso seguito dal controllo di flusso se non viene soddisfatta <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|

## <a name="see-also"></a>Vedi anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designers.md)
- [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
