---
title: Finestra di progettazione del flusso di lavoro - FlowSwitch<T> ActivityDesigner
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3f6d396acb62b9cac8f34ef106ac96257eec612
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949630"
---
# <a name="flowswitcht-activity-designer"></a>FlowSwitch\<T > ActivityDesigner

L'attività <xref:System.Activities.Statements.FlowSwitch%601> è un nodo condizionale che consente la creazione di rami per il flusso di controllo in base ai criteri di corrispondenza quando sono necessari più di due rami alternativi. Se la creazione di rami per il flusso richiede solo due percorsi, usare invece l'attività <xref:System.Activities.Statements.FlowDecision>.

## <a name="the-flowswitcht-activity"></a>FlowSwitch\<T > attività

Il <xref:System.Activities.Statements.FlowSwitch%601> attività contiene un <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> che restituisce un valore di tipo *T* (specificato dal parametro generico) durante la valutazione. L'attività contiene inoltre un set di <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> che specifica un mapping univoco tra i possibili risultati di questa valutazione e un set di oggetti <xref:System.Activities.Statements.FlowNode>. Il <xref:System.Activities.Statements.FlowNode> eseguito è quello il cui oggetto di tipo *T* corrisponde al valore della valutato <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. È possibile fornire facoltativamente un case <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> se non è presente alcuna corrispondenza.

### <a name="using-the-flowswitcht-activity-designer"></a>Usando FlowSwitch\<T > ActivityDesigner

Il **FlowSwitch\<T >** ActivityDesigner è reperibile nella **diagramma di flusso** categoria del **casella degli strumenti**, accessibile facendo clic la **Casella degli strumenti** scheda sul lato sinistro della finestra di progettazione del flusso di lavoro. In alternativa, selezionare **della casella degli strumenti** dal **View** dal menu oppure premere **Ctrl**+**Alt** + **X**.

Il **FlowSwitch\<T >** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro all'interno di un **Flowchart** finestra di progettazione. Usare il **Seleziona tipi** finestra che visualizza per specificare il tipo (associato nel codice il <xref:System.Activities.Statements.FlowSwitch%601> dal parametro generico) ottenuto dalla valutazione il <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Questa procedura crea un <xref:System.Activities.Statements.FlowSwitch%601> attività con etichettata **commutatore** all'interno di <xref:System.Activities.Statements.Flowchart> attività. Il <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> possono essere digitate nel **espressione** finestra di **proprietà** dalla finestra in cui viene visualizzato il testo di suggerimento "Immettere un'espressione VB".

Sposta il mouse sopra il **FlowSwitch\<T >** ActivityDesigner per fare in modo gli handle quadrati usati per collegare <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> da visualizzare intorno ai relativi bordi. Dopo avere trascinato il **FlowSwitch < T\>**  ActivityDesigner e altri ActivityDesigner sul **diagramma di flusso**, il <xref:System.Activities.Activity> gli oggetti che rappresentano sono pronti per essere collegate tra loro Per specificare l'ordine di esecuzione. Per creare uno del <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> associato la <xref:System.Activities.Statements.FlowSwitch%601>, fare clic su uno degli handle quadrati dei case sul perimetro del **FlowSwitch < T\>**  e trascinarlo, tenendo premuto il pulsante del mouse, su uno dei quadratini di ridimensionamento che viene visualizzato in modo simile intorno all'attività di destinazione quando si posiziona il puntatore del mouse sulla finestra di progettazione. Rilasciare il pulsante del mouse, una freccia di **FlowSwitch < T\>**  alla finestra di progettazione di destinazione che rappresenta questo case viene visualizzato. Il valore predefinito per questo case viene visualizzato sulla freccia e può essere modificato nel **Case** finestra di **proprietà** finestra.

### <a name="the-flowswitcht-properties"></a>FlowSwitch\<T > proprietà

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.FlowSwitch%601> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Specifica l'espressione valutata per identificare l'oggetto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> cui passare nel percorso di esecuzione.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Specifica un mapping univoco tra i possibili risultati ottenuti dalla valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> e un set di oggetti <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Specifica il mapping quando la valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> non corrisponde a uno dei valori contenuti nell'oggetto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Vedere anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designers.md)
- [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)