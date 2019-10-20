---
title: ActivityDesigner Progettazione flussi di lavoro pick
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 983a3ee3539617bf7ee5864c2138b2f0369e228f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650083"
---
# <a name="pick-activity-designer"></a>ActivityDesigner Pick

Nell'attività <xref:System.Activities.Statements.Pick> è disponibile il flusso di controllo basato sugli eventi. L'attività esegue uno di diversi rami in risposta a un evento di attivazione.

## <a name="the-pick-activity"></a>Attività Pick

Un'attività <xref:System.Activities.Statements.Pick> contiene una raccolta di oggetti <xref:System.Activities.Statements.PickBranch>, uno dei quali può essere eseguito dall'attività <xref:System.Activities.Statements.Pick> per effetto di un evento in entrata che funge da trigger. In questo modo Progettazione flussi di lavoro fornisce la modellazione del flusso di controllo basata sugli eventi. Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>. All'inizio dell'esecuzione di un'attività di <xref:System.Activities.Statements.Pick>, vengono pianificate tutte le attività del trigger degli elementi di <xref:System.Activities.Statements.PickBranch>. Quando la prima attività viene completata, l'attività dell'azione corrispondente è pianificata e tutte le altre attività del trigger sono annullate.

### <a name="how-to-use-the-pick-activity-designer"></a>Modalità di utilizzo dell'ActivityDesigner Pick

Accedere all'ActivityDesigner **pick** nella categoria **flusso di controllo** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **pick** dalla **casella degli strumenti** e rilasciarlo nell'area di progettazione flussi di lavoro, laddove gli ActivityDesigner vengono in genere posizionati, ad esempio all'interno di un ActivityDesigner **Sequence** . Dopo averla rilasciata in Progettazione flussi di lavoro, viene creata un'attività <xref:System.Activities.Statements.Pick>, che per impostazione predefinita contiene due attività <xref:System.Activities.Statements.PickBranch> vuote come elementi con i nomi visualizzati branch1 e Branch2. Questi rispettivi <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valori di proprietà possono essere modificati nell'intestazione dell'ActivityDesigner **PickBranch** o nella finestra **Proprietà** per ogni ramo.

Esistono due modi per aggiungere <xref:System.Activities.Statements.PickBranch> attività alla raccolta di un oggetto <xref:System.Activities.Statements.Pick>: trascinando la finestra di progettazione **PickBranch** dalla **casella degli strumenti** o facendo clic con il pulsante destro del mouse nell'area di progettazione **pick** . Per informazioni dettagliate, vedere l'argomento [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Si noti che l'unico elemento che può essere inserito all'interno di un ActivityDesigner **pick** è **PickBranch** Activity Designer.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di prelievo in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Pick> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Pick> nell'intestazione. Il valore predefinito è Pick. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedere anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [Attività di selezione](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Uso dell'attività Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)