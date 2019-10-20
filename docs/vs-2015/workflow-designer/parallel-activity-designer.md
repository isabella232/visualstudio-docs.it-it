---
title: ActivityDesigner Parallel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a46a340ccdeacacb8f04b962313db18975447a67
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672629"
---
# <a name="parallel-activity-designer"></a>ActivityDesigner Parallel
L'attività <xref:System.Activities.Statements.Parallel> esegue contemporaneamente una raccolta delle attività figlio.

## <a name="the-parallel-activity"></a>Attività Parallel
 L'attività <xref:System.Activities.Statements.Parallel> archivia le relative attività figlio in una raccolta <xref:System.Activities.Statements.Parallel.Branches%2A>. Usare l'attività <xref:System.Activities.Statements.Parallel> anziché l'attività <xref:System.Activities.Statements.Sequence> se alcune delle attività figlio possono diventare inattive.

 L'attività <xref:System.Activities.Statements.Parallel> include una proprietà <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> contenente un'espressione [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] specificata dall'utente. L'attività <xref:System.Activities.Statements.Parallel> valuta tale proprietà in seguito al completamento di ogni ramo. Se restituisce **true**, l'attività <xref:System.Activities.Statements.Parallel> viene completata senza eseguire gli altri rami. Se il <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> non restituisce **true**, l'attività <xref:System.Activities.Statements.Parallel> viene completata al completamento di tutte le relative attività figlio.

### <a name="using-the-parallel-activity-designer"></a>Utilizzo dell'ActivityDesigner Parallel
 L'ActivityDesigner **Parallel** è disponibile nella categoria flusso di **controllo** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** sul lato sinistro del [!INCLUDE[wfd2](../includes/wfd2-md.md)]. in alternativa, selezionare **barra degli** strumenti dal  **Menu Visualizza** o CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **Parallel** dalla **casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)], laddove gli ActivityDesigner vengono in genere posizionati, ad esempio all'interno di un ActivityDesigner **Sequence** . Dopo averla rilasciata nel [!INCLUDE[wfd2](../includes/wfd2-md.md)], viene creata un'attività <xref:System.Activities.Statements.Parallel>, che per impostazione predefinita contiene un <xref:System.Activities.Activity.DisplayName%2A> **parallelo**

 Per aggiungere un'attività alla raccolta di <xref:System.Activities.Statements.Parallel.Branches%2A> dell'attività parallela, trascinare un altro ActivityDesigner dalla **casella degli strumenti** e rilasciarlo sul triangolo all'interno dell'ActivityDesigner **Parallel** . I triangoli si trovano di fianco alle attività contenute nei rami. È possibile aggiungere ulteriori attività ripetendo questa procedura. Le attività possono essere riordinate trascinandoli e rilasciandole all'interno dell'ActivityDesigner **Parallel** .

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Proprietà di ParallelActivity in Progettazione flussi di lavoro
 Nella tabella seguente sono elencate le proprietà dell'attività Parallel e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Richiesto|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo visualizzato nell'intestazione dell'ActivityDesigner. Il valore predefinito è **Parallel**. Facoltativamente, è possibile modificare il valore nella griglia **Proprietà** o direttamente nell'intestazione Activity Designer.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contiene la raccolta di attività figlio da eseguire.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Restituisce il risultato dopo il completamento di un ramo. Se restituisce **true**, i rami in sospeso pianificati vengono annullati. Se questa proprietà non è impostata o restituisce **false**, l'attività viene completata al completamento di tutte le relative attività figlio. Il valore predefinito è **null**.|

## <a name="see-also"></a>Vedere anche
 [Sequenza](../workflow-designer/sequence-activity-designer.md) [ActivityDesigner ParallelForEach \<T >](../workflow-designer/parallelforeach-t-activity-designer.md) [flusso di controllo](../workflow-designer/control-flow-activity-designers.md)