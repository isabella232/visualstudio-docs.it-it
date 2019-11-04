---
title: ActivityDesigner PickBranch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c7c70aa8282fb8f50ed6faca5bcee3177ef81e15
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672577"
---
# <a name="pickbranch-activity-designer"></a>ActivityDesigner PickBranch
<xref:System.Activities.Statements.PickBranch> offre un percorso di esecuzione basato sugli eventi all'interno di un'attività <xref:System.Activities.Statements.Pick> che può essere attivata da un evento in entrata.

## <a name="pickbranch"></a>PickBranch
 Gli oggetti <xref:System.Activities.Statements.PickBranch> sono contenuti nella raccolta <xref:System.Activities.Statements.Pick.Branches%2A> di un'attività <xref:System.Activities.Statements.Pick>. Ogni oggetto <xref:System.Activities.Statements.PickBranch> è contenuto in un ramo dell'attività <xref:System.Activities.Statements.Pick> e può essere eseguito in seguito a un evento in entrata che funge da trigger. In questo modo [!INCLUDE[wfd1](../includes/wfd1-md.md)] consente la modellazione di un flusso di controllo basato sugli eventi. Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Modalità di utilizzo dell'ActivityDesigner Pick
 **PickBranch** designer è disponibile nella categoria flusso di **controllo** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** in [!INCLUDE[wfd2](../includes/wfd2-md.md)]. in alternativa, scegliere **barra degli** strumenti dal menu **Visualizza** oppure premere CTRL + ALT + X).

 Due oggetti <xref:System.Activities.Statements.PickBranch> vuoti con i nomi visualizzati **branch1** e **Branch2** vengono creati per impostazione predefinita come elementi di un'attività <xref:System.Activities.Statements.Pick> quando l'ActivityDesigner **Pick** viene inizialmente rilasciato al [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Questi rispettivi <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valori di proprietà possono essere modificati nell'intestazione **PickBranch** designer o nella finestra **Proprietà** per ogni ramo.

 Esistono due modi per aggiungere <xref:System.Activities.Statements.PickBranch> oggetti alla raccolta di un oggetto <xref:System.Activities.Statements.Pick>: trascinando la finestra di progettazione **PickBranch** dalla **casella degli strumenti** o usando il menu di scelta rapida nell'area di progettazione **pick** :

1. **PickBranch** designer crea una <xref:System.Activities.Statements.PickBranch> quando viene trascinata dalla **casella degli strumenti** e rilasciata in uno dei rami di un activitydesigner **pick** sull'area [!INCLUDE[wfd2](../includes/wfd2-md.md)]. I nuovi oggetti <xref:System.Activities.Statements.PickBranch> possono essere posizionati all'interno della finestra di progettazione <xref:System.Activities.Statements.Pick>, a destra o a sinistra di qualsiasi elemento <xref:System.Activities.Statements.PickBranch> esistente già contenuto nella raccolta. Quando si trascina una finestra di progettazione **PickBranch** nella finestra di progettazione di **selezione** con il mouse, la finestra di progettazione di **selezione** usa una banda blu-grigio verticale per indicare la posizione in cui viene aggiunta la <xref:System.Activities.Statements.PickBranch> per una posizione del mouse specificata.

2. Fare clic con il pulsante destro del mouse su **pick** Activity Designer, ma non all'interno di **PickBranch** designer, per ottenere un menu di scelta rapida e selezionare **Crea ramo** per aggiungere una nuova <xref:System.Activities.Statements.PickBranch>. Si noti che la nuova <xref:System.Activities.Statements.PickBranch> viene aggiunta a destra degli oggetti <xref:System.Activities.Statements.PickBranch> esistenti nella finestra di progettazione **pick** .

   La finestra di progettazione **PickBranch** può essere espansa per rivelare le caselle **trigger** e **Action** o comprimere facendo clic sui doppi riquadri sul lato destro delle intestazioni. Modificare il <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A> di ogni <xref:System.Activities.Statements.PickBranch> rilasciando le attività nelle caselle **trigger** e **azione** delle finestre di progettazione.

   Gli oggetti <xref:System.Activities.Statements.PickBranch> nella raccolta <xref:System.Activities.Statements.Pick.Branches%2A> di un oggetto <xref:System.Activities.Statements.Pick> possono essere riordinati trascinandoli e rilasciandoli in una nuova posizione all'interno della finestra di progettazione di **selezione** . La finestra di progettazione di **selezione** usa una banda verticale blu-grigio per indicare la posizione in cui viene aggiunta la <xref:System.Activities.Statements.PickBranch> per un determinato posizionamento del mouse.

   Esistono due diverse modalità per eliminare un'attività <xref:System.Activities.Statements.PickBranch>:

3. Selezionare **PickBranch** designer ed eliminarlo.

4. Selezionare **PickBranch** designer, fare clic con il pulsante destro del mouse per ottenere il menu di scelta rapida e scegliere **Elimina**.

   Assicurarsi di selezionare la finestra di progettazione **PickBranch** , in quanto selezionando una delle attività all'interno del **trigger** o delle caselle di **azione** per errore viene eliminata una di queste attività e non l'oggetto <xref:System.Activities.Statements.PickBranch>.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Proprietà di PickBranch in Progettazione flussi di lavoro
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.PickBranch> e ne viene descritto l'uso in [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Nome descrittivo visualizzato nell'intestazione di **PickBranch** designer. Il valore predefinito è Branch.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Ogni <xref:System.Activities.Statements.PickBranch> contiene un'azione <xref:System.Activities.Statements.PickBranch.Trigger%2A> che può richiamare l'elemento <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Ogni <xref:System.Activities.Statements.PickBranch> contiene un elemento <xref:System.Activities.Statements.PickBranch.Action%2A> che viene eseguito se attivato.|

## <a name="see-also"></a>Vedere anche
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md) [Attività Pick](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [Utilizzo dell'attività Pick](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)