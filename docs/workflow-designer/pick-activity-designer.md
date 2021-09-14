---
title: Progettazione flussi di lavoro - ActivityDesigner Pick
description: Informazioni su come l'attività Pick fornisce un flusso di controllo basato su eventi ed esegue uno dei diversi rami in risposta a un evento di attivazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: e871e38cb9f675e1a76edae0410cbd5ac45aee10
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710018"
---
# <a name="pick-activity-designer"></a>ActivityDesigner Pick

Nell'attività <xref:System.Activities.Statements.Pick> è disponibile il flusso di controllo basato sugli eventi. L'attività esegue uno di diversi rami in risposta a un evento di attivazione.

## <a name="the-pick-activity"></a>Attività Pick

Un'attività <xref:System.Activities.Statements.Pick> contiene una raccolta di oggetti <xref:System.Activities.Statements.PickBranch>, uno dei quali può essere eseguito dall'attività <xref:System.Activities.Statements.Pick> per effetto di un evento in entrata che funge da trigger. In questo modo Progettazione flussi di lavoro la modellazione del flusso di controllo basata su eventi. Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>. All'inizio <xref:System.Activities.Statements.Pick> dell'esecuzione di un'attività, vengono pianificate tutte le attività trigger <xref:System.Activities.Statements.PickBranch> degli elementi. Quando la prima attività viene completata, l'attività dell'azione corrispondente è pianificata e tutte le altre attività del trigger sono annullate.

### <a name="how-to-use-the-pick-activity-designer"></a>Modalità di utilizzo dell'ActivityDesigner Pick

Accedere **all'ActivityDesigner Pick** nella **categoria Controllo Flow** della Casella degli **strumenti.** L'ActivityDesigner **Pick** può essere  trascinato dalla casella degli strumenti e rilasciato nell'area Progettazione flussi di lavoro ogni volta che gli ActivityDesigner sono normalmente posizionati, ad esempio all'interno di un ActivityDesigner **Sequence.** Dopo il rilascio in Progettazione flussi di lavoro, viene creata un'attività che per impostazione predefinita contiene due attività vuote come elementi con nomi visualizzati <xref:System.Activities.Statements.Pick> <xref:System.Activities.Statements.PickBranch> Branch1 e Branch2. Questi rispettivi <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valori di proprietà possono essere modificati nell'intestazione dell'ActivityDesigner **PickBranch** o all'interno della **finestra** Proprietà per ogni ramo.

Esistono due modi per aggiungere attività alla raccolta di un oggetto: trascinando e rilasciando la finestra di progettazione <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick> **PickBranch**   dalla Casella degli strumenti o usando il menu di scelta rapida dall'area di progettazione Seleziona. Per informazioni dettagliate, vedere [l'argomento PickBranch.](../workflow-designer/pickbranch-activity-designer.md) Si noti che l'unico elemento che può essere inserito all'interno di un ActivityDesigner **Pick** è un **ActivityDesigner PickBranch.**

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di prelievo in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Pick> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Pick> nell'intestazione. Il valore predefinito è Pick. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedi anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [Attività di selezione](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Uso dell'attività Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)