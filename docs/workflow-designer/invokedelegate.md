---
title: Finestra di progettazione del flusso di lavoro - InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 3d68fa1b777663ff8975f8ce99100d8eddc5f05d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976919"
---
# <a name="invokedelegate"></a>InvokeDelegate

Il **InvokeDelegate** designer viene utilizzato per creare e configurare un <xref:System.Activities.Statements.InvokeDelegate> attività.

## <a name="the-invokedelegate-activity"></a>L'attività InvokeDelegate

L'oggetto <xref:System.Activities.Statements.InvokeDelegate> chiama un delegato pubblico.

### <a name="using-the-invokedelegate-activity-designer"></a>Utilizzo dell'ActivityDesigner InvokeDelegate

Il **InvokeDelegate** ActivityDesigner sono reperibili il **primitive** categoria del **casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti** scheda Progettazione flussi di lavoro (in alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

Il **InvokeDelegate** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro in cui che le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.InvokeDelegate> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito InvokeDelegate. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **InvokeDelegate** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-invokedelegate-properties"></a>Proprietà di InvokeDelegate

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.InvokeDelegate> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area Designerdesigner del flusso di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeDelegate>. Il valore predefinito è InvokeDelegate.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nome dell'elemento <xref:System.Activities.ActivityDelegate> da richiamare quando viene eseguita l'attività. È possibile modificare questa proprietà nell'area della finestra di progettazione. Si tratta di una proprietà obbligatoria.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Raccolta dell'argomento del delegato chiamato. Le chiavi sono i nomi degli oggetti parametro nel <xref:System.Activities.ActivityDelegate> e i valori sono gli argomenti le cui espressioni vengono valutate ed assegnate agli oggetti parametro corrispondente. Nella griglia delle proprietà, fare clic sul pulsante con puntini di sospensione di **DelegateArguments** campo, viene visualizzato il **DelegateArguments** finestra di dialogo che consente di impostare questa proprietà. Fare clic su di **Crea argomento** campo per aggiungere gli argomenti.|

## <a name="see-also"></a>Vedere anche

- [Procedura: Definire e usare delegati di attività in Progettazione del flusso di lavoro](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)