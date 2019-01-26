---
title: Finestra di progettazione del flusso di lavoro, ActivityDesigner Pick
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3afd20b75bdb2c00317f9acf6ec6adcd12f6f949
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069782"
---
# <a name="pick-activity-designer"></a>ActivityDesigner Pick

Nell'attività <xref:System.Activities.Statements.Pick> è disponibile il flusso di controllo basato sugli eventi. L'attività esegue uno di diversi rami in risposta a un evento di attivazione.

## <a name="the-pick-activity"></a>Attività Pick

Un'attività <xref:System.Activities.Statements.Pick> contiene una raccolta di oggetti <xref:System.Activities.Statements.PickBranch>, uno dei quali può essere eseguito dall'attività <xref:System.Activities.Statements.Pick> per effetto di un evento in entrata che funge da trigger. In questo modo Progettazione flussi di lavoro fornisce modellazione del flusso di controllo basato su eventi. Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>. All'inizio di una <xref:System.Activities.Statements.Pick> esecuzione dell'attività, tutte le attività del trigger del <xref:System.Activities.Statements.PickBranch> elementi pianificati. Quando la prima attività viene completata, l'attività dell'azione corrispondente è pianificata e tutte le altre attività del trigger sono annullate.

### <a name="how-to-use-the-pick-activity-designer"></a>Modalità di utilizzo dell'ActivityDesigner Pick

Accesso il **Scegli** ActivityDesigner nel **flusso di controllo** categoria del **della casella degli strumenti**. Il **prelievo** ActivityDesigner può essere trascinato dal **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che vengono in genere posizionate le attività, ad esempio all'interno di un  **Sequenza** ActivityDesigner. Dopo averlo rilasciato in Progettazione flussi di lavoro, viene creato un <xref:System.Activities.Statements.Pick> attività, che per impostazione predefinita contiene due vuoto <xref:System.Activities.Statements.PickBranch> attività come elementi con i nomi visualizzati dei Branch1 e Branch2. I rispettivi <xref:System.Activities.Statements.PickBranch.DisplayName%2A> i valori delle proprietà possono essere modificati nella **PickBranch** intestazione ActivityDesigner o all'interno di **proprietà** finestra per ogni ramo.

Esistono due modi per aggiungere <xref:System.Activities.Statements.PickBranch> attività alla raccolta di un <xref:System.Activities.Statements.Pick> oggetto: trascinando la **PickBranch** della finestra di progettazione dal **della casella degli strumenti** o tramite il menu di scelta rapida dall'interno di **prelievo** nell'area di progettazione. Per informazioni dettagliate, vedere la [PickBranch](../workflow-designer/pickbranch-activity-designer.md) argomento. Si noti che l'unico elemento che possono essere inserito in una **prelievo** ActivityDesigner è un **PickBranch** ActivityDesigner.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di prelievo in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Pick> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Pick> nell'intestazione. Il valore predefinito è Pick. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedere anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [Attività di selezione](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Uso dell'attività Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)