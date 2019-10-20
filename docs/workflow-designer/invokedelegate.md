---
title: Progettazione flussi di lavoro-InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 5227d96e3fad03dd3e3309523a6d2c68a1abdc11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650186"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** Designer viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.InvokeDelegate>.

## <a name="the-invokedelegate-activity"></a>Attività InvokeDelegate

L'oggetto <xref:System.Activities.Statements.InvokeDelegate> chiama un delegato pubblico.

### <a name="use-the-invokedelegate-activity-designer"></a>Usare l'ActivityDesigner InvokeDelegate

Accedere all'ActivityDesigner **InvokeDelegate** nella categoria **primitive** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **InvokeDelegate** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro in cui vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Se si elimina l'ActivityDesigner, viene creata un'attività <xref:System.Activities.Statements.InvokeDelegate> con una <xref:System.Activities.Activity.DisplayName%2A> predefinita di InvokeDelegate. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **InvokeDelegate** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-invokedelegate-properties"></a>Proprietà di InvokeDelegate

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.InvokeDelegate> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate in Progettazione flussi di lavoro area.

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeDelegate>. Il valore predefinito è InvokeDelegate.<br /><br /> Sebbene il <xref:System.Activities.Activity.DisplayName%2A> non sia strettamente necessario, è preferibile utilizzarne uno.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nome dell'elemento <xref:System.Activities.ActivityDelegate> da richiamare quando viene eseguita l'attività. Questa proprietà può essere modificata nell'area di progettazione ed è obbligatoria.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Raccolta dell'argomento del delegato chiamato. Le chiavi sono i nomi degli oggetti parametro nell'<xref:System.Activities.ActivityDelegate> e i valori sono gli argomenti le cui espressioni vengono valutate e assegnate agli oggetti parametro corrispondenti. Per visualizzare la finestra di dialogo **DelegateArguments** in cui è possibile impostare questa proprietà, fare clic sul pulsante con i puntini di sospensione nel campo **DelegateArguments** della griglia delle proprietà. Fare clic sul campo **Crea argomento** per aggiungere gli argomenti.|

## <a name="see-also"></a>Vedere anche

- [Procedura: Definire e usare delegati di attività in Progettazione del flusso di lavoro](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)