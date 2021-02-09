---
title: ActivityDesigner Progettazione flussi di lavoro FlowSwitch &lt; T &gt;
description: Informazioni sul modo <T> in cui l'attività FlowSwitch è un nodo condizionale che fornisce la diramazione per il flusso di controllo in base al criterio di corrispondenza.
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
ms.workload:
- multiple
ms.openlocfilehash: 6f61dd3f14ba527e9f5be0e009825902e683fb1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876563"
---
# <a name="flowswitcht-activity-designer"></a>Activity Designer\<T> FlowSwitch

L'attività <xref:System.Activities.Statements.FlowSwitch%601> è un nodo condizionale che consente la creazione di rami per il flusso di controllo in base ai criteri di corrispondenza quando sono necessari più di due rami alternativi. Se la creazione di rami per il flusso richiede solo due percorsi, usare invece l'attività <xref:System.Activities.Statements.FlowDecision>.

## <a name="the-flowswitcht-activity"></a>Attività FlowSwitch \<T>

L' <xref:System.Activities.Statements.FlowSwitch%601> attività contiene un oggetto <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> che restituisce un valore di tipo *T* (specificato dal parametro generico) quando viene valutato. L'attività contiene inoltre un set di <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> che specifica un mapping univoco tra i possibili risultati di questa valutazione e un set di oggetti <xref:System.Activities.Statements.FlowNode>. L' <xref:System.Activities.Statements.FlowNode> oggetto eseguito è quello il cui oggetto di tipo *T* corrisponde al valore dell'oggetto valutato <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . È possibile fornire facoltativamente un case <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> se non è presente alcuna corrispondenza.

### <a name="using-the-flowswitcht-activity-designer"></a>Utilizzo dell'ActivityDesigner \<T> FlowSwitch

L' **ActivityDesigner \<T> FlowSwitch** è disponibile nella categoria diagramma di **flusso** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** sul lato sinistro del progettazione flussi di lavoro. In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere **CTRL** + **ALT** + **X**.

È possibile trascinare l'ActivityDesigner **FlowSwitch \<T>** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro all'interno di un ActivityDesigner **Flowchart** . Utilizzare la finestra **Selezione tipi** visualizzata per specificare il tipo (associato al codice con il <xref:System.Activities.Statements.FlowSwitch%601> parametro generico) ottenuto dalla valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Questa procedura crea un' <xref:System.Activities.Statements.FlowSwitch%601> attività con etichetta **Switch** all'interno dell' <xref:System.Activities.Statements.Flowchart> attività. Il tipo <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> può essere digitato nella casella **espressione** della finestra **proprietà** facendo clic su dove il testo del suggerimento indica "immettere un'espressione VB".

Passare il puntatore del mouse sull'ActivityDesigner **FlowSwitch \<T>** per fare in modo che i quadratini di ridimensionamento usati per il collegamento vengano <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> visualizzati intorno ai bordi. Dopo aver trascinato l'ActivityDesigner **FlowSwitch<T \>** e altri ActivityDesigner nel **diagramma di flusso**, gli <xref:System.Activities.Activity> oggetti che rappresentano sono pronti per essere collegati tra loro per specificare l'ordine di esecuzione. Per creare una delle proprietà <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> associate a <xref:System.Activities.Statements.FlowSwitch%601> , fare clic su uno degli handle del case quadrato sul perimetro di **FlowSwitch<T \>** e trascinarlo (tenendo premuto il pulsante del mouse) su uno degli handle visualizzati in modo simile intorno all'attività di destinazione quando il mouse viene spostato sulla finestra di progettazione. Rilasciare il pulsante del mouse e una freccia dal **FlowSwitch<T \>** alla finestra di progettazione di destinazione, che rappresenta questo caso. Il valore predefinito di questo case viene visualizzato sulla freccia e può essere modificato nella casella **caso** della finestra **Proprietà** .

### <a name="the-flowswitcht-properties"></a>Proprietà di FlowSwitch \<T>

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
