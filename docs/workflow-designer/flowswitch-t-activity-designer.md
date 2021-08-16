---
title: Progettazione flussi di lavoro - &lt; ActivityDesigner T FlowSwitch &gt;
description: Informazioni su come l'attività FlowSwitch è un nodo condizionale che fornisce la diramazione per <T> il flusso di controllo in base al criterio di corrispondenza.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 6aa40da33fba5ae7f95e41fff6a2d905fc0585f64cab88d2d2cb0d4340cf8ccc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121383781"
---
# <a name="flowswitcht-activity-designer"></a>Activity Designer\<T> FlowSwitch

L'attività <xref:System.Activities.Statements.FlowSwitch%601> è un nodo condizionale che consente la creazione di rami per il flusso di controllo in base ai criteri di corrispondenza quando sono necessari più di due rami alternativi. Se la creazione di rami per il flusso richiede solo due percorsi, usare invece l'attività <xref:System.Activities.Statements.FlowDecision>.

## <a name="the-flowswitcht-activity"></a>Attività \<T> FlowSwitch

<xref:System.Activities.Statements.FlowSwitch%601>L'attività contiene un oggetto che restituisce un valore di tipo <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> *T* (specificato dal parametro generico) quando viene valutato. L'attività contiene inoltre un set di <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> che specifica un mapping univoco tra i possibili risultati di questa valutazione e un set di oggetti <xref:System.Activities.Statements.FlowNode>. <xref:System.Activities.Statements.FlowNode>L'oggetto eseguito è quello il cui oggetto di tipo *T* corrisponde al valore dell'oggetto <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> valutato. È possibile fornire facoltativamente un case <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> se non è presente alcuna corrispondenza.

### <a name="using-the-flowswitcht-activity-designer"></a>Uso dell'ActivityDesigner FlowSwitch \<T>

**L'ActivityDesigner \<T> FlowSwitch** è disponibile nella categoria **Diagramma** di flusso della Casella degli strumenti **,** a cui si accede facendo clic sulla scheda **Casella** degli strumenti sul lato sinistro del Progettazione flussi di lavoro. In alternativa, scegliere **Casella degli** strumenti **dal** menu Visualizza o premere **CTRL** + **ALT** + **X.**

**L'ActivityDesigner \<T> FlowSwitch** può essere  trascinato dalla casella degli strumenti e rilasciato nell'area Progettazione flussi di lavoro all'interno di un ActivityDesigner **Diagramma** di flusso. Usare la **finestra Seleziona** tipi visualizzata per specificare il tipo (associato nel codice all'oggetto dal relativo parametro generico) ottenuto dalla <xref:System.Activities.Statements.FlowSwitch%601> valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Questa procedura crea <xref:System.Activities.Statements.FlowSwitch%601> un'attività con etichetta Switch **all'interno** <xref:System.Activities.Statements.Flowchart> dell'attività. È possibile digitare nella casella Espressione della finestra Proprietà facendo clic nel punto in cui il testo del suggerimento indica <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> "Immettere  un'VB'espressione". 

Posizionare il puntatore del mouse sull'ActivityDesigner **FlowSwitch \<T>** per fare in modo che gli handle quadrati utilizzati per il collegamento vengano visualizzati <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> intorno ai bordi. Dopo aver trascinato l'ActivityDesigner **FlowSwitch<T \>** e altri ActivityDesigner nel diagramma di flusso , gli oggetti che rappresentano sono pronti per essere collegati tra loro per specificare l'ordine di  <xref:System.Activities.Activity> esecuzione. Per creare uno degli oggetti associati all'oggetto , fare clic su uno degli handle quadrati del case sul perimetro di <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> <xref:System.Activities.Statements.FlowSwitch%601> **FlowSwitch<T \>** e trascinarlo (tenendo premuto il pulsante del mouse) su uno degli handle visualizzati in modo simile intorno all'attività di destinazione quando il puntatore del mouse viene posizionato sulla relativa finestra di progettazione. Rilasciare il pulsante del mouse e viene visualizzata una freccia dal<**flusso alla \>** finestra di progettazione di destinazione che rappresenta questo caso. Il valore predefinito per questo caso viene visualizzato sulla freccia e può essere modificato nella **casella Case** della **finestra** Proprietà.

### <a name="the-flowswitcht-properties"></a>Proprietà di \<T> FlowSwitch

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.FlowSwitch%601> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Vero|Specifica l'espressione valutata per identificare l'oggetto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> cui passare nel percorso di esecuzione.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Falso|Specifica un mapping univoco tra i possibili risultati ottenuti dalla valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> e un set di oggetti <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Vero|Specifica il mapping quando la valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> non corrisponde a uno dei valori contenuti nell'oggetto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Vedi anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designers.md)
- [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
