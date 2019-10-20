---
title: ActivityDesigner Progettazione flussi di lavoro-PickBranch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a43fa99c9f5fe4fbb3cfe336efb983fced655f2a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650061"
---
# <a name="pickbranch-activity-designer"></a>ActivityDesigner PickBranch

<xref:System.Activities.Statements.PickBranch> offre un percorso di esecuzione basato sugli eventi all'interno di un'attività <xref:System.Activities.Statements.Pick> che può essere attivata da un evento in entrata.

## <a name="pickbranch"></a>PickBranch

Gli oggetti <xref:System.Activities.Statements.PickBranch> sono contenuti nella raccolta <xref:System.Activities.Statements.Pick.Branches%2A> di un'attività <xref:System.Activities.Statements.Pick>. Ogni oggetto <xref:System.Activities.Statements.PickBranch> è contenuto in un ramo dell'attività <xref:System.Activities.Statements.Pick> e può essere eseguito in seguito a un evento in entrata che funge da trigger. In questo modo il Progettazione flussi di lavoro fornisce la modellazione del flusso di controllo basata sugli eventi. Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Modalità di utilizzo dell'ActivityDesigner Pick

Accedere a **PickBranch** designer nella categoria **flusso di controllo** della **casella degli strumenti**.

Due oggetti <xref:System.Activities.Statements.PickBranch> vuoti con i nomi visualizzati **branch1** e **Branch2** vengono creati per impostazione predefinita come elementi di un'attività <xref:System.Activities.Statements.Pick> quando l'ActivityDesigner **Pick** viene inizialmente rilasciato al progettazione flussi di lavoro. Questi rispettivi <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valori di proprietà possono essere modificati nell'intestazione **PickBranch** designer o nella finestra **Proprietà** per ogni ramo.

Sono disponibili due modi per aggiungere <xref:System.Activities.Statements.PickBranch> oggetti alla raccolta di un oggetto <xref:System.Activities.Statements.Pick>: trascinando la finestra di progettazione **PickBranch** dalla **casella degli strumenti**oppure facendo clic con il pulsante destro del mouse nell'area di progettazione **pick** :

- **PickBranch** designer crea una <xref:System.Activities.Statements.PickBranch> quando viene trascinata dalla **casella degli strumenti** e rilasciata in uno dei rami di un activitydesigner **pick** sull'area Progettazione flussi di lavoro. I nuovi oggetti <xref:System.Activities.Statements.PickBranch> possono essere posizionati all'interno della finestra di progettazione <xref:System.Activities.Statements.Pick>, a destra o a sinistra di qualsiasi elemento <xref:System.Activities.Statements.PickBranch> esistente già contenuto nella raccolta. Quando si trascina una finestra di progettazione **PickBranch** nella finestra di progettazione di **selezione** con il mouse, la finestra di progettazione di **selezione** usa una banda blu-grigio verticale per indicare la posizione in cui viene aggiunta la <xref:System.Activities.Statements.PickBranch> per una posizione del mouse specificata.

- Fare clic con il pulsante destro del mouse su **pick** Activity Designer, ma non all'interno di **PickBranch** designer, per ottenere un menu di scelta rapida e selezionare **Crea ramo** per aggiungere una nuova <xref:System.Activities.Statements.PickBranch>. Si noti che la nuova <xref:System.Activities.Statements.PickBranch> viene aggiunta a destra degli oggetti <xref:System.Activities.Statements.PickBranch> esistenti nella finestra di progettazione **pick** .

La finestra di progettazione **PickBranch** può essere espansa per rivelare le caselle **trigger** e **Action** o comprimere facendo clic sui doppi riquadri sul lato destro delle intestazioni. Modificare il <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A> di ogni <xref:System.Activities.Statements.PickBranch> rilasciando le attività nelle caselle **trigger** e **azione** delle finestre di progettazione.

Gli oggetti <xref:System.Activities.Statements.PickBranch> nella raccolta <xref:System.Activities.Statements.Pick.Branches%2A> di un oggetto <xref:System.Activities.Statements.Pick> possono essere riordinati trascinandoli e rilasciandoli in una nuova posizione all'interno della finestra di progettazione di **selezione** . La finestra di progettazione di **selezione** usa una banda verticale blu-grigio per indicare la posizione in cui viene aggiunta la <xref:System.Activities.Statements.PickBranch> per un determinato posizionamento del mouse.

Esistono due diverse modalità per eliminare un'attività <xref:System.Activities.Statements.PickBranch>:

- Selezionare **PickBranch** designer ed eliminarlo.
- Selezionare **PickBranch** designer, fare clic con il pulsante destro del mouse per ottenere il menu di scelta rapida e scegliere **Elimina**.

Assicurarsi di selezionare la finestra di progettazione **PickBranch** , in quanto selezionando una delle attività all'interno del **trigger** o delle caselle di **azione** per errore viene eliminata una di queste attività e non l'oggetto <xref:System.Activities.Statements.PickBranch>.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Proprietà di PickBranch in Progettazione flussi di lavoro

Nella tabella seguente vengono illustrate le proprietà <xref:System.Activities.Statements.PickBranch> più utili e viene descritto come utilizzarle nel Progettazione flussi di lavoro.

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Nome descrittivo visualizzato nell'intestazione di **PickBranch** designer. Il valore predefinito è Branch.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Ogni <xref:System.Activities.Statements.PickBranch> contiene un'azione <xref:System.Activities.Statements.PickBranch.Trigger%2A> che può richiamare l'elemento <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Ogni <xref:System.Activities.Statements.PickBranch> contiene un elemento <xref:System.Activities.Statements.PickBranch.Action%2A> che viene eseguito se attivato.|

## <a name="see-also"></a>Vedere anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [Attività di selezione](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Uso dell'attività Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)