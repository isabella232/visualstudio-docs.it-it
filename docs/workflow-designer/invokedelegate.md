---
title: Progettazione flussi di lavoro - InvokeDelegate
description: Informazioni sulla finestra di progettazione InvokeDelegate e su come usare la finestra di progettazione InvokeDelegate per creare e configurare un'attività InvokeDelegate.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 12fd42bd51a252470c2b7d4fbae23581847ddf0f6d3dede60f6e2659215d80fd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121393510"
---
# <a name="invokedelegate"></a>InvokeDelegate

La **finestra di progettazione InvokeDelegate** viene usata per creare e configurare un'attività. <xref:System.Activities.Statements.InvokeDelegate>

## <a name="the-invokedelegate-activity"></a>Attività InvokeDelegate

L'oggetto <xref:System.Activities.Statements.InvokeDelegate> chiama un delegato pubblico.

### <a name="use-the-invokedelegate-activity-designer"></a>Usare l'ActivityDesigner InvokeDelegate

Accedere **all'ActivityDesigner InvokeDelegate** nella **categoria Primitive** della casella degli **strumenti.** **L'ActivityDesigner InvokeDelegate** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie Progettazione flussi di lavoro in cui vengono in genere inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . L'eliminazione dell'ActivityDesigner <xref:System.Activities.Statements.InvokeDelegate> crea un'attività con il <xref:System.Activities.Activity.DisplayName%2A> valore predefinito InvokeDelegate. Può <xref:System.Activities.Activity.DisplayName%2A> essere modificato nell'intestazione **dell'ActivityDesigner InvokeDelegate** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-invokedelegate-properties"></a>Proprietà InvokeDelegate

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.InvokeDelegate> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate Progettazione flussi di lavoro superficie.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeDelegate>. Il valore predefinito è InvokeDelegate.<br /><br /> Anche se <xref:System.Activities.Activity.DisplayName%2A> non è strettamente necessario, è meglio usarne uno.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Vero|Nome dell'elemento <xref:System.Activities.ActivityDelegate> da richiamare quando viene eseguita l'attività. Questa proprietà può essere modificata nell'area di progettazione ed è obbligatoria.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Falso|Raccolta dell'argomento del delegato chiamato. Le chiavi sono i nomi degli oggetti parametro in e i valori sono gli argomenti le cui espressioni vengono valutate e <xref:System.Activities.ActivityDelegate> assegnate agli oggetti parametro corrispondenti. Per visualizzare la **finestra di dialogo DelegateArguments** in cui è possibile impostare questa proprietà, fare clic sul pulsante con i puntini di sospensione nel campo **DelegateArguments** della griglia delle proprietà. Fare clic **sul campo Crea** argomento per aggiungere gli argomenti.|

## <a name="see-also"></a>Vedi anche

- [Procedura: definire e utilizzare delegati di attività in Progettazione del flusso di lavoro](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)