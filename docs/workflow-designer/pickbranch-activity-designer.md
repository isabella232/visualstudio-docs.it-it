---
title: ActivityDesigner Progettazione flussi di lavoro-PickBranch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34da9091c0f96b7270678f9b36fe861e4a87418f
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876086"
---
# <a name="pickbranch-activity-designer"></a>ActivityDesigner PickBranch

<xref:System.Activities.Statements.PickBranch> offre un percorso di esecuzione basato sugli eventi all'interno di un'attività <xref:System.Activities.Statements.Pick> che può essere attivata da un evento in entrata.

## <a name="pickbranch"></a>PickBranch

Gli oggetti <xref:System.Activities.Statements.PickBranch> sono contenuti nella raccolta <xref:System.Activities.Statements.Pick.Branches%2A> di un'attività <xref:System.Activities.Statements.Pick>. Ogni oggetto <xref:System.Activities.Statements.PickBranch> è contenuto in un ramo dell'attività <xref:System.Activities.Statements.Pick> e può essere eseguito in seguito a un evento in entrata che funge da trigger. In questo modo il Progettazione flussi di lavoro fornisce la modellazione del flusso di controllo basata sugli eventi. Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Modalità di utilizzo dell'ActivityDesigner Pick

Accedere a **PickBranch** designer nella categoria **flusso di controllo** della **casella degli strumenti**.

<xref:System.Activities.Statements.PickBranch>Per impostazione predefinita, vengono creati due oggetti vuoti con i nomi visualizzati **branch1** e **Branch2** come elementi di un' <xref:System.Activities.Statements.Pick> attività quando l'activitydesigner **pick** viene inizialmente rilasciato al progettazione flussi di lavoro. Questi rispettivi <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valori di proprietà possono essere modificati nell'intestazione **PickBranch** designer o nella finestra **proprietà** per ogni ramo.

È possibile aggiungere <xref:System.Activities.Statements.PickBranch> oggetti alla raccolta di un oggetto in due modi <xref:System.Activities.Statements.Pick> : trascinando e rilasciando la finestra di progettazione **PickBranch** dalla **casella degli strumenti**oppure facendo clic con il pulsante destro del mouse nell'area di progettazione **pick** :

- La finestra di progettazione **PickBranch** crea un oggetto <xref:System.Activities.Statements.PickBranch> quando viene trascinato dalla **casella degli strumenti** e rilasciata in uno dei rami di un ActivityDesigner **pick** sull'area Progettazione flussi di lavoro. I nuovi oggetti <xref:System.Activities.Statements.PickBranch> possono essere posizionati all'interno della finestra di progettazione <xref:System.Activities.Statements.Pick>, a destra o a sinistra di qualsiasi elemento <xref:System.Activities.Statements.PickBranch> esistente già contenuto nella raccolta. Quando si trascina una finestra di progettazione **PickBranch** nella finestra di progettazione di **selezione** con il mouse, la finestra di progettazione di **selezione** usa una banda blu-grigio verticale per indicare la posizione in cui viene aggiunto l'oggetto <xref:System.Activities.Statements.PickBranch> per una posizione del mouse specificata.

- Fare clic con il pulsante destro del mouse su **pick** Activity Designer, ma non all'interno di **PickBranch** designer, per ottenere un menu di scelta rapida e selezionare **Crea ramo** per aggiungere un nuovo <xref:System.Activities.Statements.PickBranch> . Si noti che il nuovo <xref:System.Activities.Statements.PickBranch> oggetto viene aggiunto a destra degli <xref:System.Activities.Statements.PickBranch> oggetti esistenti nella finestra di progettazione **pick** .

La finestra di progettazione **PickBranch** può essere espansa per rivelare le caselle **trigger** e **Action** o comprimere facendo clic sui doppi riquadri sul lato destro delle intestazioni. Modificare <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A> di ogni <xref:System.Activities.Statements.PickBranch> trascinando le attività nelle caselle **trigger** e **Action** delle rispettive finestre di progettazione.

Gli <xref:System.Activities.Statements.PickBranch> oggetti nella <xref:System.Activities.Statements.Pick.Branches%2A> raccolta di un <xref:System.Activities.Statements.Pick> oggetto possono essere riordinati trascinandoli e rilasciandoli in una nuova posizione all'interno della finestra di progettazione di **selezione** . La finestra di progettazione di **selezione** usa una banda verticale blu-grigio per indicare la posizione in cui <xref:System.Activities.Statements.PickBranch> viene aggiunto l'oggetto per una posizione del mouse specificata.

Esistono due diverse modalità per eliminare un'attività <xref:System.Activities.Statements.PickBranch>:

- Selezionare **PickBranch** designer ed eliminarlo.
- Selezionare **PickBranch** designer, fare clic con il pulsante destro del mouse per ottenere il menu di scelta rapida e scegliere **Elimina**.

Assicurarsi di selezionare la finestra di progettazione **PickBranch** , in quanto la selezione di una delle attività all'interno del **trigger** o delle caselle **azione** per errore comporta l'eliminazione di una di queste attività e non dell' <xref:System.Activities.Statements.PickBranch> oggetto.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Proprietà di PickBranch in Progettazione flussi di lavoro

Nella tabella seguente vengono illustrate le <xref:System.Activities.Statements.PickBranch> proprietà più utili e viene descritto come utilizzarle nel Progettazione flussi di lavoro.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Falso|Nome descrittivo visualizzato nell'intestazione di **PickBranch** designer. Il valore predefinito è Branch.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Vero|Ogni <xref:System.Activities.Statements.PickBranch> contiene un'azione <xref:System.Activities.Statements.PickBranch.Trigger%2A> che può richiamare l'elemento <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|Falso|Ogni <xref:System.Activities.Statements.PickBranch> contiene un elemento <xref:System.Activities.Statements.PickBranch.Action%2A> che viene eseguito se attivato.|

## <a name="see-also"></a>Vedi anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [Attività di selezione](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Uso dell'attività Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)