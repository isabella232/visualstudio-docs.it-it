---
title: 'Finestra di progettazione del flusso di lavoro - procedura: Aggiungere commenti a un flusso di lavoro'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4ae0d3390be709dfe07f174bbb9754b986cdafc5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913694"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Procedura: Aggiungere commenti a un flusso di lavoro in Progettazione flussi di lavoro

Per facilitare la creazione di flussi di lavoro più ampi e complessi, .NET Framework 4.5 consente allo sviluppatore di aggiungere annotazioni per i tipi di elemento nella finestra di progettazione seguenti:

-   <xref:System.Activities.Activity>

-   <xref:System.Activities.Statements.State>

-   <xref:System.Activities.Statements.Transition>

-   Classi derivate da <xref:System.Activities.Statements.FlowNode>

-   <xref:System.Activities.Variable>

-   <xref:System.Activities.Argument>

> [!IMPORTANT]
> Il contenuto di un'annotazione viene salvato come testo normale nel file XAML associato al flusso di lavoro e potrebbe potenzialmente essere letto da altri. Prestare attenzione quando vengono fornite informazioni riservate in un'unica annotazione.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Aggiunta di un'annotazione a un'attività nella finestra di progettazione

1. Nella finestra di progettazione del flusso di lavoro, fare clic su un elemento nel flusso di lavoro della finestra di progettazione e seleziona **annotazioni**, **Aggiungi annotazione**.

1. Aggiungere il testo dell'annotazione nello spazio disponibile.

   L'elemento viene visualizzata un'icona di annotazione. Passare il mouse sull'icona di annotazione Visualizza il testo dell'annotazione.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Visualizzazione di un'annotazione della finestra di progettazione dell'attività

1. Con un ActivityDesigner che dispone di un'annotazione che verrà visualizzata all'esterno dell'attività, fare clic sui **Pin** icona nello strumento decorativo visuale dell'annotazione.

   L'annotazione verrà visualizzata nella finestra di progettazione dell'attività. Nella schermata riportata di seguito, l'annotazione "inizia attività nel flusso di lavoro" viene visualizzata nella finestra di progettazione dell'attività.

   ![Annotazione visualizzata nella finestra di progettazione dell'attività](../workflow-designer/media/annotationindesigner.png)

2. Per visualizzare l'annotazione all'esterno di progettazione dell'attività, passare il mouse sull'area dell'annotazione nella finestra di progettazione dell'attività e scegliere il **Sblocca** icona

   ![Annotazione visualizzata all'esterno di progettazione dell'attività](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Mostra o nascondi tutte le annotazioni

1. Fare clic con il pulsante destro del mouse su un'attività che dispone di annotazione. Selezionare **annotazioni**, **Mostra tutte le annotazioni**.

   Tutte le annotazioni vengono visualizzate nelle finestre di progettazione dell'attività.

1. Per visualizzare tutte le annotazioni di fuori di finestre di progettazione dell'attività, fare clic su attività e selezionare **annotazioni**, **Nascondi tutte le annotazioni**.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Modifica o eliminazione di un'annotazione per un'attività

1. Fare clic con il pulsante destro del mouse su un'attività che dispone di un'annotazione.

1. Selezionare **annotazioni**, **Modifica annotazione** oppure **Elimina annotazione**.

   L'annotazione è aperta per la modifica o eliminata.

1. Per eliminare tutte le annotazioni in una sola volta, fare doppio clic su flusso di lavoro della finestra di progettazione e seleziona **Annotation**, **eliminare tutte le annotazioni**.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Aggiunta, modifica ed eliminazione di un'annotazione per una variabile o un argomento

1. Fare clic con il pulsante destro del mouse su una variabile o un argomento e selezionare Aggiungi annotazione.

1. Immettere il testo dell'annotazione. Argomento o della variabile viene visualizzata un'icona di annotazione.

1. Fare clic con il pulsante destro del mouse su una variabile o un argomento che dispone di un'annotazione. Selezionare Modifica annotazione.

   L'annotazione viene aperto per la modifica.

1. Fare clic con il pulsante destro del mouse su una variabile o un argomento che dispone di un'annotazione. Selezionare Elimina annotazione.

   L'annotazione verrà eliminata.