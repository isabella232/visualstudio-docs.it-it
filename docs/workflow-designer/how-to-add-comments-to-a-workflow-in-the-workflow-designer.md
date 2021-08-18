---
title: 'Progettazione flussi di lavoro - Procedura: Aggiungere commenti a un flusso di lavoro'
description: Informazioni su .NET Framework 4.5 consente allo sviluppatore di aggiungere annotazioni a determinati tipi di elementi nella finestra di progettazione, ad esempio gli elementi Activity, State e Transition.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 81de5a8b27626066fb8c85b5d13da2f387bae8c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114758"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Procedura: aggiungere commenti a un flusso di lavoro in Progettazione del flusso di lavoro

Per facilitare la creazione di flussi di lavoro più grandi e più complessi, .NET Framework 4.5 consente allo sviluppatore di aggiungere annotazioni ai tipi di elemento seguenti nella finestra di progettazione:

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Classi derivate da <xref:System.Activities.Statements.FlowNode>

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> Il contenuto di un'annotazione viene salvato come testo normale nel file XAML associato al flusso di lavoro e potrebbe potenzialmente essere letto da altri. Prestare attenzione quando vengono fornite informazioni riservate in un'unica annotazione.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Aggiunta di un'annotazione a un'attività nella finestra di progettazione

1. Nella finestra di progettazione del flusso di lavoro fare clic con il pulsante destro del mouse su un elemento nella finestra di progettazione del flusso di lavoro e scegliere **Annotazioni**, **Aggiungi annotazione**.

1. Aggiungere il testo dell'annotazione nello spazio disponibile.

   L'elemento mostra un'icona di annotazione. Passando il puntatore del mouse sull'icona dell'annotazione viene visualizzato il testo dell'annotazione.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Visualizzazione di un'annotazione della finestra di progettazione dell'attività

1. Con un ActivityDesigner con un'annotazione visualizzata all'esterno dell'attività, fare clic sull'icona **Aggiungi** nello strumento decorativo dell'annotazione.

   L'annotazione viene visualizzata nella finestra di progettazione dell'attività. Nella schermata riportata di seguito, l'annotazione "inizia attività nel flusso di lavoro" viene visualizzata nella finestra di progettazione dell'attività.

   ![Annotazione visualizzata nella finestra di progettazione dell'attività](../workflow-designer/media/annotationindesigner.png)

2. Per visualizzare l'annotazione all'esterno della finestra di progettazione dell'attività, passare il puntatore del mouse sull'area di annotazione nella finestra di progettazione dell'attività e fare clic **sull'icona Rimuovi**

   ![Annotazione visualizzata all'esterno della finestra di progettazione di un'attività](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Mostra o nascondi tutte le annotazioni

1. Fare clic con il pulsante destro del mouse su un'attività che dispone di annotazione. Selezionare **Annotazioni**, **Mostra tutte le annotazioni**.

   Tutte le annotazioni vengono visualizzate nelle finestre di progettazione dell'attività.

1. Per visualizzare tutte le annotazioni all'esterno delle finestre di progettazione dell'attività, fare clic con il pulsante destro del mouse sull'attività e scegliere **Annotazioni**, **Nascondi tutte le annotazioni**.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Modifica o eliminazione di un'annotazione per un'attività

1. Fare clic con il pulsante destro del mouse su un'attività che dispone di un'annotazione.

1. Selezionare **Annotazioni**, **Modifica annotazione** o **Elimina annotazione**.

   L'annotazione viene aperta per la modifica o l'eliminazione.

1. Per eliminare tutte le annotazioni contemporaneamente, fare clic con il pulsante destro del mouse sulla finestra di progettazione del flusso di lavoro e scegliere **Annotazione**, **Elimina tutte le annotazioni**.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Aggiunta, modifica ed eliminazione di un'annotazione per una variabile o un argomento

1. Fare clic con il pulsante destro del mouse su una variabile o un argomento e selezionare Aggiungi annotazione.

1. Immettere il testo dell'annotazione. La variabile o l'argomento visualizza un'icona di annotazione.

1. Fare clic con il pulsante destro del mouse su una variabile o un argomento che dispone di un'annotazione. Selezionare Modifica annotazione.

   L'annotazione viene aperta per la modifica.

1. Fare clic con il pulsante destro del mouse su una variabile o un argomento che dispone di un'annotazione. Selezionare Elimina annotazione.

   L'annotazione viene eliminata.
