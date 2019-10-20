---
title: ActivityDesigner Progettazione flussi di lavoro-FlowSwitch <T>
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f167f46a2ed118e8781f66e4a781d4a3ef95b0d6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650398"
---
# <a name="flowswitcht-activity-designer"></a>ActivityDesigner FlowSwitch \<T >

L'attività <xref:System.Activities.Statements.FlowSwitch%601> è un nodo condizionale che consente la creazione di rami per il flusso di controllo in base ai criteri di corrispondenza quando sono necessari più di due rami alternativi. Se la creazione di rami per il flusso richiede solo due percorsi, usare invece l'attività <xref:System.Activities.Statements.FlowDecision>.

## <a name="the-flowswitcht-activity"></a>Attività FlowSwitch \<T >

L'attività <xref:System.Activities.Statements.FlowSwitch%601> contiene un <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> che restituisce un valore di tipo *t* (specificato dal parametro generico) quando viene valutato. L'attività contiene inoltre un set di <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> che specifica un mapping univoco tra i possibili risultati di questa valutazione e un set di oggetti <xref:System.Activities.Statements.FlowNode>. Il <xref:System.Activities.Statements.FlowNode> eseguito è quello il cui oggetto di tipo *t* corrisponde al valore del <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> valutato. È possibile fornire facoltativamente un case <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> se non è presente alcuna corrispondenza.

### <a name="using-the-flowswitcht-activity-designer"></a>Uso di FlowSwitch \<T > Activity Designer

**FlowSwitch \<T >** Activity Designer è disponibile nella categoria diagramma di **flusso** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** sul lato sinistro della progettazione flussi di lavoro. In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** oppure premere **CTRL** +**ALT** +**X**.

È possibile trascinare l'ActivityDesigner **FlowSwitch \<T >** dalla **casella degli strumenti** e rilasciarlo nella superficie progettazione flussi di lavoro all'interno di un ActivityDesigner **Flowchart** . Utilizzare la finestra **Selezione tipi** visualizzata per specificare il tipo (associato nel codice con il <xref:System.Activities.Statements.FlowSwitch%601> dal parametro generico) ottenuto dalla valutazione del <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Questa procedura crea un'attività di <xref:System.Activities.Statements.FlowSwitch%601> con etichetta **Switch** all'interno dell'attività <xref:System.Activities.Statements.Flowchart>. Il <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> può essere digitato nella casella **espressione** della finestra **Proprietà** facendo clic su dove il testo del suggerimento indica "immettere un'espressione VB".

Passare il puntatore del mouse sul **FlowSwitch \<T >** ActivityDesigner per fare in modo che i quadratini usati per collegare <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> siano visualizzati intorno ai bordi. Dopo aver trascinato il **FlowSwitch < T \>** ActivityDesigner e altri ActivityDesigner nel **diagramma di flusso**, gli oggetti <xref:System.Activities.Activity> che rappresentano sono pronti per essere collegati tra loro per specificare l'ordine di esecuzione. Per creare una delle <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> associate al <xref:System.Activities.Statements.FlowSwitch%601>, fare clic su uno degli handle quadratini sul perimetro di **FlowSwitch < t \>** e trascinarlo (tenendo premuto il pulsante del mouse) su uno degli handle visualizzati in modo simile intorno al attività di destinazione quando il mouse viene spostato sulla finestra di progettazione. Rilasciare il pulsante del mouse e una freccia dal **FlowSwitch < T \>** alla finestra di progettazione di destinazione che rappresenta questo caso. Il valore predefinito di questo case viene visualizzato sulla freccia e può essere modificato nella casella **caso** della finestra **Proprietà** .

### <a name="the-flowswitcht-properties"></a>Proprietà di > \<T FlowSwitch

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.FlowSwitch%601> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Specifica l'espressione valutata per identificare l'oggetto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> cui passare nel percorso di esecuzione.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Specifica un mapping univoco tra i possibili risultati ottenuti dalla valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> e un set di oggetti <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Specifica il mapping quando la valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> non corrisponde a uno dei valori contenuti nell'oggetto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Vedere anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designers.md)
- [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)