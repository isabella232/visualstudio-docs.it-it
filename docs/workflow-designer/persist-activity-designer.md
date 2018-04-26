---
title: Finestra di progettazione del flusso di lavoro - ActivityDesigner Persist
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04c7989f5cc37ec295f9fa778f2120dd372fd99a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="persist-activity-designer"></a>ActivityDesigner Persist

Il **Persist** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Persist> attività.

## <a name="the-persist-activity"></a>Attività Persist

L'attività <xref:System.Activities.Statements.Persist> salva un flusso di lavoro su disco, se possibile. Non è possibile eseguire l'attività <xref:System.Activities.Statements.Persist> in un'area non permanente come, ad esempio, all'interno di un'attività <xref:System.Activities.Statements.TransactionScope>. Se si usa un'attività <xref:System.Activities.Statements.Persist> in un ambito non permanente, viene generata un'eccezione in fase di esecuzione.

### <a name="using-the-persist-activity-designer"></a>Utilizzo dell'ActivityDesigner Persist

Il **Persist** ActivityDesigner è reperibile nel **Runtime** categoria del **della casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti** scheda (in alternativa, selezionare **della casella degli strumenti** dal **vista** menu o CTRL + ALT + X.)

Il **Persist** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Crea un <xref:System.Activities.Statements.Persist> attività con valore predefinito è **DisplayName** Persist. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **Persist** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-persist-properties"></a>Proprietà di Persist

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Persist> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune di esse possono essere modificate nell'area di progettazione flussi di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Persist>. Il valore predefinito è Persist. Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedere anche

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)