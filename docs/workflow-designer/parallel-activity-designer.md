---
title: Finestra di progettazione del flusso di lavoro - ActivityDesigner Parallel
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2315c27bc0a35ac1dc839b5fd98003105d92bd4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="parallel-activity-designer"></a>ActivityDesigner Parallel

L'attività <xref:System.Activities.Statements.Parallel> esegue contemporaneamente una raccolta delle attività figlio.

## <a name="the-parallel-activity"></a>Attività Parallel

L'attività <xref:System.Activities.Statements.Parallel> archivia le relative attività figlio in una raccolta <xref:System.Activities.Statements.Parallel.Branches%2A>. Usare l'attività <xref:System.Activities.Statements.Parallel> anziché l'attività <xref:System.Activities.Statements.Sequence> se alcune delle attività figlio possono diventare inattive.

Il <xref:System.Activities.Statements.Parallel> attività dispone di un <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> proprietà che contiene un utente specificato espressione Visual Basic. L'attività <xref:System.Activities.Statements.Parallel> valuta tale proprietà in seguito al completamento di ogni ramo. Se restituisce **True**, quindi il <xref:System.Activities.Statements.Parallel> attività viene completata senza eseguire gli altri rami. Se il <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> non restituisce **True**, quindi il <xref:System.Activities.Statements.Parallel> attività viene completata quando tutte le relative attività figlio sono stati completati.

### <a name="using-the-parallel-activity-designer"></a>Utilizzo dell'ActivityDesigner Parallel

Il **Parallel** ActivityDesigner è reperibile nella **flusso di controllo** categoria del **casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti**scheda sul lato sinistro della finestra di progettazione del flusso di lavoro (in alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

Il **Parallel** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che vengono generalmente posizionati gli ActivityDesigner, ad esempio, all'interno di una **Sequenza** ActivityDesigner. Dopo averlo rilasciato in Progettazione flussi di lavoro, viene creato un <xref:System.Activities.Statements.Parallel> attività, che per impostazione predefinita contiene una <xref:System.Activities.Activity.DisplayName%2A> di **paralleli**

Per aggiungere un'attività per il <xref:System.Activities.Statements.Parallel.Branches%2A> raccolta dell'attività parallel, trascinare un altro ActivityDesigner dal **della casella degli strumenti** e rilasciarla sul triangolo all'interno di **parallela** ActivityDesigner. I triangoli si trovano di fianco alle attività contenute nei rami. È possibile aggiungere ulteriori attività ripetendo questa procedura. Le attività possono essere riordinate trascinandoli e rilasciandoli all'interno di **parallela** ActivityDesigner.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Proprietà di ParallelActivity in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà dell'attività Parallel e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo visualizzato nell'intestazione dell'ActivityDesigner. Il valore predefinito è **parallela**. Il valore può essere modificato facoltativamente nel **proprietà** griglia o direttamente nell'intestazione dell'ActivityDesigner.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contiene la raccolta di attività figlio da eseguire.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Restituisce il risultato dopo il completamento di un ramo. Se restituisce **True**, quindi pianificati in sospeso di rami vengono annullati. Se questa proprietà non è impostata o restituisce **False**, l'attività viene completata quando tutte le relative attività figlio sono stati completati. Il valore predefinito è **null**.|

## <a name="see-also"></a>Vedere anche

- [sequenza](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)