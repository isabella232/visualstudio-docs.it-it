---
title: 'Progettazione flussi di lavoro-procedura: aggiungere commenti a un flusso di lavoro'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 77fb43671a45d5d53d2fe23fa3e4e7a9a98c4373
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815500"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Procedura: aggiungere commenti a un flusso di lavoro in Progettazione del flusso di lavoro

Per semplificare la creazione di flussi di lavoro più grandi e più complessi, .NET Framework 4,5 consente allo sviluppatore di aggiungere annotazioni ai tipi di elemento seguenti nella finestra di progettazione:

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Classi derivate da <xref:System.Activities.Statements.FlowNode>

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> Il contenuto di un'annotazione viene salvato come testo normale nel file XAML associato al flusso di lavoro e potrebbe potenzialmente essere letto da altri. Prestare attenzione quando vengono fornite informazioni riservate in un'unica annotazione.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Aggiunta di un'annotazione a un'attività nella finestra di progettazione

1. In Progettazione flussi di lavoro, fare clic con il pulsante destro del mouse su un elemento in Progettazione flussi di lavoro **e selezionare Annotazioni**, **Aggiungi annotazione**.

1. Aggiungere il testo dell'annotazione nello spazio disponibile.

   L'elemento Mostra un'icona di annotazione. Il puntatore del mouse sull'icona dell'annotazione Visualizza il testo dell'annotazione.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Visualizzazione di un'annotazione della finestra di progettazione dell'attività

1. Con un ActivityDesigner con un'annotazione visualizzata all'esterno dell'attività, fare clic sull'icona **Aggiungi** nello strumento decorativo di annotazione.

   L'annotazione viene visualizzata nella finestra di progettazione dell'attività. Nella schermata riportata di seguito, l'annotazione "inizia attività nel flusso di lavoro" viene visualizzata nella finestra di progettazione dell'attività.

   ![Annotazione visualizzata nella finestra di progettazione dell'attività](../workflow-designer/media/annotationindesigner.png)

2. Per visualizzare l'annotazione all'esterno della finestra di progettazione dell'attività, passare il mouse sull'area annotazione nella finestra di progettazione dell'attività e fare clic sull'icona **Rimuovi**

   ![Annotazione visualizzata all'esterno della finestra di progettazione dell'attività](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Mostra o nascondi tutte le annotazioni

1. Fare clic con il pulsante destro del mouse su un'attività che dispone di annotazione. Selezionare le **annotazioni**, **visualizzare tutte le annotazioni**.

   Tutte le annotazioni vengono visualizzate nelle finestre di progettazione dell'attività.

1. Per visualizzare tutte le annotazioni all'esterno delle finestre di progettazione dell'attività, fare clic con il pulsante destro del mouse sull'attività e selezionare **annotazioni**, **Nascondi tutte le**annotazioni

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Modifica o eliminazione di un'annotazione per un'attività

1. Fare clic con il pulsante destro del mouse su un'attività che dispone di un'annotazione.

1. Selezionare **le annotazioni**, **Modifica annotazione** o **Elimina annotazione**.

   L'annotazione viene aperta per la modifica o l'eliminazione.

1. Per eliminare tutte le annotazioni contemporaneamente, fare clic con il pulsante destro del mouse su Progettazione flussi di lavoro e selezionare **annotazione**, **eliminare tutte le annotazioni**.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Aggiunta, modifica ed eliminazione di un'annotazione per una variabile o un argomento

1. Fare clic con il pulsante destro del mouse su una variabile o un argomento e selezionare Aggiungi annotazione.

1. Immettere il testo dell'annotazione. La variabile o l'argomento Visualizza un'icona di annotazione.

1. Fare clic con il pulsante destro del mouse su una variabile o un argomento che dispone di un'annotazione. Selezionare Modifica annotazione.

   L'annotazione viene aperta per la modifica.

1. Fare clic con il pulsante destro del mouse su una variabile o un argomento che dispone di un'annotazione. Selezionare Elimina annotazione.

   L'annotazione viene eliminata.
