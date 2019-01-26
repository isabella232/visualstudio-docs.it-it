---
title: Finestra di progettazione del flusso di lavoro - Activity Designer PickBranch
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29b7cc9d61f7be551e5b53e053a86586bab8708b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916269"
---
# <a name="pickbranch-activity-designer"></a>ActivityDesigner PickBranch

<xref:System.Activities.Statements.PickBranch> offre un percorso di esecuzione basato sugli eventi all'interno di un'attività <xref:System.Activities.Statements.Pick> che può essere attivata da un evento in entrata.

## <a name="pickbranch"></a>PickBranch

Gli oggetti <xref:System.Activities.Statements.PickBranch> sono contenuti nella raccolta <xref:System.Activities.Statements.Pick.Branches%2A> di un'attività <xref:System.Activities.Statements.Pick>. Ogni oggetto <xref:System.Activities.Statements.PickBranch> è contenuto in un ramo dell'attività <xref:System.Activities.Statements.Pick> e può essere eseguito in seguito a un evento in entrata che funge da trigger. In questo modo la finestra di progettazione del flusso di lavoro fornisce modellazione del flusso di controllo basato su eventi. Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Modalità di utilizzo dell'ActivityDesigner Pick

Accesso di **PickBranch** della finestra di progettazione nel **flusso di controllo** categoria del **della casella degli strumenti**.

Due vuoto <xref:System.Activities.Statements.PickBranch> gli oggetti con i nomi visualizzati dei **Branch1** e **Branch2** vengono creati per impostazione predefinita come elementi di un <xref:System.Activities.Statements.Pick> attività quando il **scegliere** ActivityDesigner viene inizialmente rilasciato alla finestra di progettazione del flusso di lavoro. I rispettivi <xref:System.Activities.Statements.PickBranch.DisplayName%2A> i valori delle proprietà possono essere modificati nella **PickBranch** intestazione della finestra di progettazione o all'interno di **proprietà** finestra per ogni ramo.

Esistono due modi per aggiungere <xref:System.Activities.Statements.PickBranch> oggetti alla raccolta di un <xref:System.Activities.Statements.Pick> oggetto: trascinando la **PickBranch** della finestra di progettazione dal **della casella degli strumenti**, oppure usando il menu di scelta rapida da all'interno di **prelievo** nell'area di progettazione:

- Il **PickBranch** designer crea un <xref:System.Activities.Statements.PickBranch> quando viene trascinato dal **della casella degli strumenti** e rilasciato in uno dei rami di un **Scegli** ActivityDesigner sul Area di progettazione del flusso di lavoro. I nuovi oggetti <xref:System.Activities.Statements.PickBranch> possono essere posizionati all'interno della finestra di progettazione <xref:System.Activities.Statements.Pick>, a destra o a sinistra di qualsiasi elemento <xref:System.Activities.Statements.PickBranch> esistente già contenuto nella raccolta. Quando si trascina un **PickBranch** della finestra di progettazione nel **selezionare** della finestra di progettazione con il mouse, il **selezionare** progettazione viene utilizzata una striscia verticale blu-grigio per indicare dove il <xref:System.Activities.Statements.PickBranch> viene aggiunta per una determinata posizione del mouse.

- Fare doppio clic su **prelievo** ActivityDesigner (ma non all'interno **PickBranch** designer) per visualizzare un menu di scelta rapida e scegliere **Crea ramo** per aggiungere un nuovo <xref:System.Activities.Statements.PickBranch>. Si noti che il nuovo <xref:System.Activities.Statements.PickBranch> viene aggiunta a destra dell'oggetto esistente <xref:System.Activities.Statements.PickBranch> gli oggetti nel **Scegli** finestra di progettazione.

Il **PickBranch** finestra di progettazione può essere espanso per visualizzare i **Trigger** e **azione** caselle o compresso facendo sui due accenti circonflessi sul lato destro delle rispettive intestazioni. Modificare il <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A> della ognuno <xref:System.Activities.Statements.PickBranch> rilasciando le attività nel **Trigger** e **azione** caselle delle finestre di progettazione.

Il <xref:System.Activities.Statements.PickBranch> gli oggetti nel <xref:System.Activities.Statements.Pick.Branches%2A> raccolta di un <xref:System.Activities.Statements.Pick> oggetto, possono essere riordinati trascinandoli e rilasciandoli in una nuova posizione all'interno del **scegliere** finestra di progettazione. Il **seleziona** progettazione viene utilizzata una striscia verticale blu-grigio per indicare dove il <xref:System.Activities.Statements.PickBranch> viene aggiunta per una determinata posizione del mouse.

Esistono due diverse modalità per eliminare un'attività <xref:System.Activities.Statements.PickBranch>:

- Selezionare il **PickBranch** progettazione ed eliminarlo.
- Selezionare il **PickBranch** della finestra di progettazione, pulsante destro del mouse per visualizzare il menu di scelta rapida e scegliere **eliminare**.

Assicurarsi di selezionare il **PickBranch** della finestra di progettazione, selezionare una delle attività all'interno di relativo **Trigger** oppure **azione** caselle viene eliminato per errore uno di tali attività e non il <xref:System.Activities.Statements.PickBranch> oggetto.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Proprietà di PickBranch in Progettazione flussi di lavoro

La tabella seguente illustra il più utile <xref:System.Activities.Statements.PickBranch> proprietà e viene spiegato come usarle nella finestra di progettazione del flusso di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Nome descrittivo visualizzato nell'intestazione del **PickBranch** finestra di progettazione. Il valore predefinito è Branch.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Ogni <xref:System.Activities.Statements.PickBranch> contiene un'azione <xref:System.Activities.Statements.PickBranch.Trigger%2A> che può richiamare l'elemento <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Ogni <xref:System.Activities.Statements.PickBranch> contiene un elemento <xref:System.Activities.Statements.PickBranch.Action%2A> che viene eseguito se attivato.|

## <a name="see-also"></a>Vedere anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [Attività di selezione](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Uso dell'attività Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)