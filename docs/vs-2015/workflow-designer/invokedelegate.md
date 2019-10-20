---
title: InvokeDelegate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc35aec714255b467431488936605fb37009db9d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659013"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** Designer viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.InvokeDelegate>.

## <a name="the-invokedelegate-activity"></a>L'attività InvokeDelegate

L'oggetto <xref:System.Activities.Statements.InvokeDelegate> chiama un delegato pubblico.

### <a name="using-the-invokedelegate-activity-designer"></a>Utilizzo dell'ActivityDesigner InvokeDelegate

L'ActivityDesigner **InvokeDelegate** è disponibile nella categoria **primitive** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda della **casella degli strumenti** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, scegliere **barra degli** strumenti dal menu **Visualizza** oppure CTRL + ALT + X.)

È possibile trascinare l'ActivityDesigner **InvokeDelegate** dalla **casella degli strumenti** e rilasciarlo nell'area [!INCLUDE[wfd2](../includes/wfd2-md.md)] in cui vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.InvokeDelegate> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito InvokeDelegate. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **InvokeDelegate** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-invokedelegate-properties"></a>Proprietà di InvokeDelegate

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.InvokeDelegate> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nome proprietà|Richiesto|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeDelegate>. Il valore predefinito è InvokeDelegate.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nome dell'elemento <xref:System.Activities.ActivityDelegate> da richiamare quando viene eseguita l'attività. È possibile modificare questa proprietà nell'area della finestra di progettazione. Si tratta di una proprietà obbligatoria.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Raccolta dell'argomento del delegato chiamato. Le chiavi sono i nomi degli oggetti <xref:System.Activities.DelegateArgument> su <xref:System.Activities.ActivityDelegate> e i valori sono gli argomenti le cui espressioni vengono valutate ed assegnate agli oggetti corrispondenti <xref:System.Activities.DelegateArgument>. Nella griglia delle proprietà fare clic sul pulsante con i puntini di sospensione nel campo **DelegateArguments** per visualizzare la finestra di dialogo **DelegateArguments** che consente di impostare questa proprietà. Fare clic sul campo **Crea argomento** per aggiungere gli argomenti.|

## <a name="see-also"></a>Vedere anche

- [Procedura: Definire e usare delegati di attività in Progettazione del flusso di lavoro](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)