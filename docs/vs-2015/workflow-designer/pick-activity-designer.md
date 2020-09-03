---
title: ActivityDesigner Pick | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: daefc48cfff2c5c73d9ecf14316777becf4d83c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672601"
---
# <a name="pick-activity-designer"></a>ActivityDesigner Pick
Nell'attività <xref:System.Activities.Statements.Pick> è disponibile il flusso di controllo basato sugli eventi. L'attività esegue uno di diversi rami in risposta a un evento di attivazione.

## <a name="the-pick-activity"></a>Attività Pick
 Un'attività <xref:System.Activities.Statements.Pick> contiene una raccolta di oggetti <xref:System.Activities.Statements.PickBranch>, uno dei quali può essere eseguito dall'attività <xref:System.Activities.Statements.Pick> per effetto di un evento in entrata che funge da trigger. In questo modo [!INCLUDE[wfd1](../includes/wfd1-md.md)] consente la modellazione di un flusso di controllo basato sugli eventi. Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>. All'inizio dell'esecuzione di un'attività <xref:System.Activities.Statements.Pick>, tutte le attività del trigger degli elementi <xref:System.Activities.Statements.PickBranch> sono pianificate. Quando la prima attività viene completata, l'attività dell'azione corrispondente è pianificata e tutte le altre attività del trigger sono annullate.

### <a name="how-to-use-the-pick-activity-designer"></a>Modalità di utilizzo dell'ActivityDesigner Pick
 L'ActivityDesigner **pick** è disponibile nella categoria flusso di **controllo** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** in. [!INCLUDE[wfd2](../includes/wfd2-md.md)] in alternativa, scegliere **barra degli** strumenti dal menu **Visualizza** o premere CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **pick** dalla **casella degli strumenti** e rilasciarlo nell'area in cui [!INCLUDE[wfd2](../includes/wfd2-md.md)] vengono in genere posizionati gli ActivityDesigner, ad esempio all'interno di un ActivityDesigner **Sequence** . Dopo averlo rilasciato in [!INCLUDE[wfd2](../includes/wfd2-md.md)], viene creata un'attività <xref:System.Activities.Statements.Pick> che per impostazione predefinita contiene due attività <xref:System.Activities.Statements.PickBranch> vuote come elementi i cui nomi visualizzati sono Branch1 e Branch2. Questi rispettivi <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valori di proprietà possono essere modificati nell'intestazione dell'ActivityDesigner **PickBranch** o nella finestra **proprietà** per ogni ramo.

 Esistono due modi per aggiungere <xref:System.Activities.Statements.PickBranch> attività alla raccolta di un <xref:System.Activities.Statements.Pick> oggetto: trascinando e rilasciando la finestra di progettazione **PickBranch** dalla **casella degli strumenti** o usando il menu di scelta rapida nell'area di progettazione della **selezione** . Per informazioni dettagliate, vedere l'argomento [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Si noti che l'unico elemento che può essere inserito all'interno di un ActivityDesigner **pick** è **PickBranch** Activity Designer.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di prelievo in Progettazione flussi di lavoro
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Pick> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Pick> nell'intestazione. Il valore predefinito è Pick. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedere anche
 [Control Flow](../workflow-designer/control-flow-activity-designers.md) [Attività di selezione](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [del flusso di controllo tramite l'attività Pick](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)