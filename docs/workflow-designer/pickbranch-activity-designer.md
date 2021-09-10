---
title: Progettazione flussi di lavoro - Activity Designer PickBranch
description: Informazioni su come l'ActivityDesigner PickBranch fornisce un percorso di esecuzione basato su eventi all'interno di un'attività Pick che può essere attivata da un evento in ingresso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 9ccf7591c56b7dbf4ab73750690a47b012a1cb26
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963632"
---
# <a name="pickbranch-activity-designer"></a>ActivityDesigner PickBranch

<xref:System.Activities.Statements.PickBranch> offre un percorso di esecuzione basato sugli eventi all'interno di un'attività <xref:System.Activities.Statements.Pick> che può essere attivata da un evento in entrata.

## <a name="pickbranch"></a>PickBranch

Gli oggetti <xref:System.Activities.Statements.PickBranch> sono contenuti nella raccolta <xref:System.Activities.Statements.Pick.Branches%2A> di un'attività <xref:System.Activities.Statements.Pick>. Ogni oggetto <xref:System.Activities.Statements.PickBranch> è contenuto in un ramo dell'attività <xref:System.Activities.Statements.Pick> e può essere eseguito in seguito a un evento in entrata che funge da trigger. In questo modo il Progettazione flussi di lavoro la modellazione del flusso di controllo basata su eventi. Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Modalità di utilizzo dell'ActivityDesigner Pick

Accedere alla **finestra di progettazione PickBranch** nella **categoria Controllo Flow** della Casella degli **strumenti.**

Due oggetti vuoti con nomi visualizzati Branch1 e Branch2 vengono creati per impostazione predefinita come elementi di un'attività quando l'ActivityDesigner Pick viene inizialmente rilasciato nel <xref:System.Activities.Statements.PickBranch>   <xref:System.Activities.Statements.Pick> Progettazione flussi di lavoro.  Questi rispettivi <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valori di proprietà possono essere modificati nell'intestazione della finestra di progettazione **PickBranch** o all'interno **della finestra** Proprietà per ogni ramo.

Esistono due modi per aggiungere oggetti alla raccolta di un oggetto: trascinando la finestra di progettazione <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick> **PickBranch**  dalla Casella degli strumenti o usando il menu di scelta rapida dall'area di progettazione Selezione:

- La **finestra di progettazione PickBranch** crea un oggetto quando viene trascinato dalla casella degli strumenti e rilasciato in uno dei rami di un <xref:System.Activities.Statements.PickBranch> ActivityDesigner **Pick** nell'Progettazione flussi di lavoro lavoro.  I nuovi oggetti <xref:System.Activities.Statements.PickBranch> possono essere posizionati all'interno della finestra di progettazione <xref:System.Activities.Statements.Pick>, a destra o a sinistra di qualsiasi elemento <xref:System.Activities.Statements.PickBranch> esistente già contenuto nella raccolta. Quando si trascina una finestra **di progettazione PickBranch** nella finestra di progettazione **Pick** con il mouse, la finestra di progettazione **Pick** usa una banda blu-grigia verticale per indicare dove viene aggiunto l'oggetto per una determinata posizione <xref:System.Activities.Statements.PickBranch> del mouse.

- Fare clic con il **pulsante destro del** mouse sull'ActivityDesigner Pick (ma non all'interno della finestra di progettazione **PickBranch)** per ottenere un menu di scelta rapida e scegliere **Create Branch** (Crea ramo) per aggiungere un nuovo <xref:System.Activities.Statements.PickBranch> oggetto . Si noti che il <xref:System.Activities.Statements.PickBranch> nuovo oggetto viene aggiunto a destra degli oggetti esistenti nella finestra di progettazione <xref:System.Activities.Statements.PickBranch> **Seleziona.**

La **finestra di progettazione PickBranch** può essere espansa per visualizzare le caselle **Trigger** e **Action** o compressa facendo clic sui doppi caret sul lato destro delle intestazioni. Modificare e <xref:System.Activities.Statements.PickBranch.Trigger%2A> <xref:System.Activities.Statements.PickBranch.Action%2A> di ogni attività <xref:System.Activities.Statements.PickBranch> rilasciando  le attività nelle **caselle Trigger** e Azione delle finestre di progettazione.

Gli oggetti nella raccolta di un oggetto possono essere riordinati trascinandoli e rilasciandoli in una nuova posizione all'interno della <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick.Branches%2A> finestra di progettazione <xref:System.Activities.Statements.Pick> **Selezione.** La **finestra di** progettazione Selezione usa una banda verticale grigio-blu per indicare dove viene aggiunto <xref:System.Activities.Statements.PickBranch> l'oggetto per una determinata posizione del mouse.

Esistono due diverse modalità per eliminare un'attività <xref:System.Activities.Statements.PickBranch>:

- Selezionare la **finestra di progettazione PickBranch** ed eliminarla.
- Selezionare la finestra **di progettazione PickBranch,** fare clic con il pulsante destro del mouse per ottenere il menu di scelta rapida e scegliere **Elimina.**

Assicurarsi di selezionare la finestra **di progettazione PickBranch,** in quanto la selezione di una delle attività all'interno delle caselle **Trigger** o **Azione** elimina per errore una di queste attività e non <xref:System.Activities.Statements.PickBranch> l'oggetto.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Proprietà di PickBranch in Progettazione flussi di lavoro

Nella tabella seguente vengono illustrate le proprietà più <xref:System.Activities.Statements.PickBranch> utili e viene descritto come usarle nel Progettazione flussi di lavoro.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Falso|Nome descrittivo visualizzato nell'intestazione della finestra **di progettazione PickBranch.** Il valore predefinito è Branch.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Vero|Ogni <xref:System.Activities.Statements.PickBranch> contiene un'azione <xref:System.Activities.Statements.PickBranch.Trigger%2A> che può richiamare l'elemento <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|Falso|Ogni <xref:System.Activities.Statements.PickBranch> contiene un elemento <xref:System.Activities.Statements.PickBranch.Action%2A> che viene eseguito se attivato.|

## <a name="see-also"></a>Vedi anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [Attività di selezione](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Uso dell'attività Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)