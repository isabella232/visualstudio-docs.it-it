---
title: Finestra di progettazione del flusso di lavoro - InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: fd490d15d5dc1760222446a1ae507d0e764c73f4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870535"
---
# <a name="invokedelegate"></a>InvokeDelegate

Il **InvokeDelegate** designer viene utilizzato per creare e configurare un <xref:System.Activities.Statements.InvokeDelegate> attività.

## <a name="the-invokedelegate-activity"></a>L'attività InvokeDelegate

L'oggetto <xref:System.Activities.Statements.InvokeDelegate> chiama un delegato pubblico.

### <a name="use-the-invokedelegate-activity-designer"></a>Utilizzo dell'ActivityDesigner InvokeDelegate

Accesso di **InvokeDelegate** ActivityDesigner nel **primitive** categoria del **della casella degli strumenti**. Il **InvokeDelegate** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro in cui sin posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. La finestra di progettazione di attività di rilascio crea un <xref:System.Activities.Statements.InvokeDelegate> attività predefinito <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **InvokeDelegate** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.

### <a name="the-invokedelegate-properties"></a>Le proprietà di InvokeDelegate

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.InvokeDelegate> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area di progettazione del flusso di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeDelegate>. Il valore predefinito è InvokeDelegate.<br /><br /> Sebbene il <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatorio, si consiglia di usarne uno.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nome dell'elemento <xref:System.Activities.ActivityDelegate> da richiamare quando viene eseguita l'attività. Questa proprietà può essere modificata nell'area di progettazione ed è obbligatoria.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Raccolta dell'argomento del delegato chiamato. Le chiavi sono i nomi degli oggetti parametro nel <xref:System.Activities.ActivityDelegate>, e i valori sono gli argomenti le cui espressioni vengono valutate ed assegnate agli oggetti parametro corrispondente. Per visualizzare il **DelegateArguments** finestra di dialogo in cui è possibile impostare questa proprietà, fare clic sul pulsante con puntini di sospensione il **DelegateArguments** campo della griglia delle proprietà. Scegliere il **Crea argomento** campo da aggiungere gli argomenti.|

## <a name="see-also"></a>Vedere anche

- [Procedura: Definire e usare delegati di attività nella finestra di progettazione del flusso di lavoro](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)