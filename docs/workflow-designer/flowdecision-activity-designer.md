---
title: Progettazione flussi di lavoro - ActivityDesigner FlowDecision
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
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 44afcb360f8517dd2ff8f30a76bb9a809b0da450
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963468"
---
# <a name="flowdecision-activity-designer"></a>ActivityDesigner FlowDecision

Il nodo <xref:System.Activities.Statements.FlowDecision> è un nodo condizionale che fornisce due rami alternativi per il flusso di controllo a seconda che venga soddisfatta una condizione specificata. Se il flusso richiede più di due rami, usare invece <xref:System.Activities.Statements.FlowSwitch%601>.

## <a name="the-flowdecision-node"></a>Nodo FlowDecision

Usare <xref:System.Activities.Statements.FlowDecision> quando per il flusso è possibile creare due rami in due percorsi. Un nodo <xref:System.Activities.Statements.FlowDecision> presenta un oggetto <xref:System.Activities.Statements.FlowDecision.Condition%2A> e un oggetto <xref:System.Activities.Statements.FlowNode> associato a ognuno dei due possibili risultati: <xref:System.Activities.Statements.FlowDecision.True%2A> o <xref:System.Activities.Statements.FlowDecision.False%2A>. L'elemento <xref:System.Activities.Statements.FlowDecision.Condition%2A> viene valutato e il valore di questa valutazione determina il successivo nodo <xref:System.Activities.Statements.FlowNode> da elaborare nell'oggetto <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Utilizzo dell'ActivityDesigner FlowDecision

La **finestra di progettazione FlowDecision** è disponibile nella categoria **Diagramma** di flusso della Casella degli strumenti **,** a cui si accede facendo clic sulla scheda **Casella** degli strumenti nella Progettazione flussi di lavoro. In alternativa, selezionare **Casella degli** **strumenti** dal menu Visualizza o premere **CTRL** +  + **ALT+X.**

La **finestra di progettazione FlowDecision** può essere trascinata dalla casella degli strumenti e rilasciata nella Progettazione flussi di lavoro all'interno di un ActivityDesigner **flowchart.**  Verrà creata una decisione <xref:System.Activities.Statements.FlowDecision> con etichetta **all'interno** <xref:System.Activities.Statements.Flowchart> dell'attività. Posizionare il puntatore del mouse sulla **finestra di progettazione** e visualizzare gli handle quadratici True e **False** per i due rami.

Dopo aver **trascinato la finestra di progettazione FlowDecision** e altre finestre di progettazione nel **diagramma** di flusso, i nodi possono essere collegati tra loro per specificare l'ordine di esecuzione. Per creare un collegamento tra un nodo di origine (inclusi i rami **True** e **False** di **FlowDecision)** e un nodo di destinazione, passare il mouse sulla finestra di progettazione del nodo di origine e gli handle quadratici vengono visualizzati su ogni lato del nodo. Fare clic su uno degli handle quadrati e, tenendo premuto il pulsante del mouse, trascinarlo su uno degli handle visualizzati in modo simile intorno al nodo di destinazione durante il passaggio del mouse. Dopo aver rilasciato il pulsante del mouse, verrà creato un collegamento tra questi due nodi rappresentato da una freccia che collega la finestra di progettazione di origine a quella di destinazione.

L'espressione che indica che è possibile digitare nella casella Condizione della finestra Proprietà facendo clic nel punto in cui il testo del suggerimento indica "Immettere un'VB <xref:System.Activities.Statements.FlowDecision.Condition%2A> espressione".  

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
