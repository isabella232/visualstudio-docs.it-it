---
title: Progettazione flussi di lavoro - ActivityDesigner parallelo
description: Informazioni sull'attività Parallel e su come usare Parallel ActivityDesigner per eseguire contemporaneamente una raccolta di attività figlio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: d4b1c5315933e2e29e29774b94804846d5317723
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114693"
---
# <a name="parallel-activity-designer"></a>ActivityDesigner Parallel

L'attività <xref:System.Activities.Statements.Parallel> esegue contemporaneamente una raccolta delle attività figlio.

## <a name="the-parallel-activity"></a>Attività Parallel

L'attività <xref:System.Activities.Statements.Parallel> archivia le relative attività figlio in una raccolta <xref:System.Activities.Statements.Parallel.Branches%2A>. Usare l'attività <xref:System.Activities.Statements.Parallel> anziché l'attività <xref:System.Activities.Statements.Sequence> se alcune delle attività figlio possono diventare inattive.

<xref:System.Activities.Statements.Parallel>L'attività ha una proprietà che contiene <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> un'espressione Visual Basic specificata dall'utente. L'attività <xref:System.Activities.Statements.Parallel> valuta tale proprietà in seguito al completamento di ogni ramo. Se restituisce **True,** l'attività <xref:System.Activities.Statements.Parallel> viene completata senza eseguire gli altri rami. Se non restituisce True, l'attività viene completata al termine di tutte le <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> attività  <xref:System.Activities.Statements.Parallel> figlio.

### <a name="using-the-parallel-activity-designer"></a>Utilizzo dell'ActivityDesigner Parallel

Accedere **all'ActivityDesigner** parallelo nella **categoria Controllo Flow** della Casella degli **strumenti**.

L'ActivityDesigner parallelo può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie Progettazione flussi di lavoro ogni volta che gli ActivityDesigner vengono normalmente posizionati, ad esempio all'interno di un ActivityDesigner **Sequence.**  Dopo l'eliminazione nel Progettazione flussi di lavoro, crea un'attività, che per impostazione <xref:System.Activities.Statements.Parallel> predefinita contiene un oggetto <xref:System.Activities.Activity.DisplayName%2A> **parallel**

Per aggiungere un'attività alla raccolta dell'attività parallela, trascinare un altro ActivityDesigner dalla Casella degli strumenti e rilasciarlo sul triangolo all'interno <xref:System.Activities.Statements.Parallel.Branches%2A> dell'ActivityDesigner  parallelo.  I triangoli si trovano di fianco alle attività contenute nei rami. È possibile aggiungere ulteriori attività ripetendo questa procedura. Le attività possono essere riordinate trascinandole  all'interno dell'ActivityDesigner parallelo.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Proprietà di ParallelActivity in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà dell'attività Parallel e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo visualizzato nell'intestazione dell'ActivityDesigner. Il valore predefinito è **Parallel**. Il valore può essere modificato facoltativamente nella **griglia** Proprietà o direttamente nell'intestazione di ActivityDesigner.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Vero|Contiene la raccolta di attività figlio da eseguire.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|Falso|Restituisce il risultato dopo il completamento di un ramo. Se restituisce **True,** i rami in sospeso pianificati vengono annullati. Se questa proprietà non è impostata o restituisce **False**, l'attività viene completata al termine di tutte le attività figlio. Il valore predefinito è **null**.|

## <a name="see-also"></a>Vedi anche

- [Sequenza](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
