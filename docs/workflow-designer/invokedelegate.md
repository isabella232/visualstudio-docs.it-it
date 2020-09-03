---
title: Progettazione flussi di lavoro-InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
author: TerryGLee
ms.author: tglee
ms.workload:
- multiple
ms.openlocfilehash: 9e63fb7a766b79467749cc5181a575e0d35a07b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876073"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** Designer viene utilizzato per creare e configurare un' <xref:System.Activities.Statements.InvokeDelegate> attività.

## <a name="the-invokedelegate-activity"></a>Attività InvokeDelegate

L'oggetto <xref:System.Activities.Statements.InvokeDelegate> chiama un delegato pubblico.

### <a name="use-the-invokedelegate-activity-designer"></a>Usare l'ActivityDesigner InvokeDelegate

Accedere all'ActivityDesigner **InvokeDelegate** nella categoria **primitive** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **InvokeDelegate** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro in cui vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Se si elimina l'ActivityDesigner, viene creata un' <xref:System.Activities.Statements.InvokeDelegate> attività con il valore predefinito <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **InvokeDelegate** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-invokedelegate-properties"></a>Proprietà di InvokeDelegate

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.InvokeDelegate> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate in Progettazione flussi di lavoro area.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeDelegate>. Il valore predefinito è InvokeDelegate.<br /><br /> Sebbene <xref:System.Activities.Activity.DisplayName%2A> non sia strettamente obbligatorio, è preferibile utilizzarne uno.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Vero|Nome dell'elemento <xref:System.Activities.ActivityDelegate> da richiamare quando viene eseguita l'attività. Questa proprietà può essere modificata nell'area di progettazione ed è obbligatoria.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Falso|Raccolta dell'argomento del delegato chiamato. Le chiavi sono i nomi degli oggetti parametro nell'oggetto <xref:System.Activities.ActivityDelegate> e i valori sono gli argomenti le cui espressioni vengono valutate e assegnate agli oggetti parametro corrispondenti. Per visualizzare la finestra di dialogo **DelegateArguments** in cui è possibile impostare questa proprietà, fare clic sul pulsante con i puntini di sospensione nel campo **DelegateArguments** della griglia delle proprietà. Fare clic sul campo **Crea argomento** per aggiungere gli argomenti.|

## <a name="see-also"></a>Vedere anche

- [Procedura: definire e utilizzare delegati di attività in Progettazione del flusso di lavoro](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)