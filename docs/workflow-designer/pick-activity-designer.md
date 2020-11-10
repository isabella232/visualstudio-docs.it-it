---
title: ActivityDesigner Progettazione flussi di lavoro pick
description: Informazioni sul modo in cui l'attività Pick fornisce un flusso di controllo basato sugli eventi ed esegue uno dei diversi rami in risposta a un evento di attivazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9968a00a1e4530e22abe25819c9e3d5188bcefa
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434246"
---
# <a name="pick-activity-designer"></a>ActivityDesigner Pick

Nell'attività <xref:System.Activities.Statements.Pick> è disponibile il flusso di controllo basato sugli eventi. L'attività esegue uno di diversi rami in risposta a un evento di attivazione.

## <a name="the-pick-activity"></a>Attività Pick

Un'attività <xref:System.Activities.Statements.Pick> contiene una raccolta di oggetti <xref:System.Activities.Statements.PickBranch>, uno dei quali può essere eseguito dall'attività <xref:System.Activities.Statements.Pick> per effetto di un evento in entrata che funge da trigger. In questo modo Progettazione flussi di lavoro fornisce la modellazione del flusso di controllo basata sugli eventi. Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>. All'inizio dell'esecuzione di un' <xref:System.Activities.Statements.Pick> attività, vengono pianificate tutte le attività trigger degli <xref:System.Activities.Statements.PickBranch> elementi. Quando la prima attività viene completata, l'attività dell'azione corrispondente è pianificata e tutte le altre attività del trigger sono annullate.

### <a name="how-to-use-the-pick-activity-designer"></a>Modalità di utilizzo dell'ActivityDesigner Pick

Accedere all'ActivityDesigner **pick** nella categoria **flusso di controllo** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **pick** dalla **casella degli strumenti** e rilasciarlo nell'area di progettazione flussi di lavoro, laddove gli ActivityDesigner vengono in genere posizionati, ad esempio all'interno di un ActivityDesigner **Sequence** . Dopo averla rilasciata in Progettazione flussi di lavoro, viene creata un' <xref:System.Activities.Statements.Pick> attività, che per impostazione predefinita contiene due <xref:System.Activities.Statements.PickBranch> attività vuote come elementi con i nomi visualizzati branch1 e Branch2. Questi rispettivi <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valori di proprietà possono essere modificati nell'intestazione dell'ActivityDesigner **PickBranch** o nella finestra **proprietà** per ogni ramo.

È possibile aggiungere <xref:System.Activities.Statements.PickBranch> attività alla raccolta di un oggetto in due modi <xref:System.Activities.Statements.Pick> : trascinando la finestra di progettazione **PickBranch** dalla **casella degli strumenti** o usando il menu di scelta rapida nell'area di progettazione della **selezione** . Per informazioni dettagliate, vedere l'argomento [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Si noti che l'unico elemento che può essere inserito all'interno di un ActivityDesigner **pick** è **PickBranch** Activity Designer.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di prelievo in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Pick> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatoria|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Pick> nell'intestazione. Il valore predefinito è Pick. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedere anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [Attività di selezione](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Uso dell'attività Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)