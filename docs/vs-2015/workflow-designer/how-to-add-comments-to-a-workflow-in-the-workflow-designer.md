---
title: 'Procedura: Aggiungere commenti a un flusso di lavoro nella finestra di progettazione del flusso di lavoro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 507bb70539019646f57f0aa9267573429d3fa202
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433565"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Procedura: Aggiungere commenti a un flusso di lavoro in Progettazione flussi di lavoro
Per facilitare la creazione di flussi di lavoro più ampi e complessi, [!INCLUDE[net_v45](../includes/net-v45-md.md)] consente allo sviluppatore di aggiungere annotazioni ai seguenti tipi di elementi nella finestra di progettazione:  
  
- <xref:System.Activities.Activity>  
  
- <xref:System.Activities.Statements.State>  
  
- <xref:System.Activities.Statements.Transition>  
  
- Classi derivate da <xref:System.Activities.Statements.FlowNode>  
  
- <xref:System.Activities.Variable>  
  
- <xref:System.Activities.Argument>  
  
> [!IMPORTANT]
> Il contenuto di un'annotazione viene salvato come testo normale nel file XAML associato al flusso di lavoro e potrebbe potenzialmente essere letto da altri. Prestare attenzione quando vengono fornite informazioni riservate in un'unica annotazione.  
  
### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Aggiunta di un'annotazione a un'attività nella finestra di progettazione  
  
1. Nella finestra di progettazione del flusso di lavoro, fare clic su un elemento nel flusso di lavoro della finestra di progettazione e seleziona **annotazioni**, **Aggiungi annotazione**.  
  
2. Aggiungere il testo dell'annotazione nello spazio disponibile.  
  
3. Nell'elemento verrà visualizzata un'icona dell'annotazione. Passare il mouse sull'icona di annotazione per visualizzare il testo dell'annotazione.  
  
     ![Sequenza di attività con annotazione](../workflow-designer/media/annotation.png "annotazione")  
  
### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Visualizzazione di un'annotazione della finestra di progettazione dell'attività  
  
1. Con un ActivityDesigner che dispone di un'annotazione che verrà visualizzata all'esterno dell'attività, fare clic sui **Pin** icona nello strumento decorativo visuale dell'annotazione.  
  
2. Le annotazioni vengono visualizzati nella finestra di progettazione dell'attività. Nella schermata riportata di seguito, l'annotazione "inizia attività nel flusso di lavoro" viene visualizzata nella finestra di progettazione dell'attività.  
  
     ![Annotazione visualizzata nell'oggetto ActivityDesigner](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")  
  
3. Per visualizzare l'annotazione all'esterno di progettazione dell'attività, passare il mouse sull'area dell'annotazione nella finestra di progettazione dell'attività e scegliere il **Sblocca** icona  
  
     ![Annotazione visualizzata all'esterno di progettazione dell'attività](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")  
  
### <a name="showing-or-hiding-all-annotations"></a>Mostra o nascondi tutte le annotazioni  
  
1. Fare clic con il pulsante destro del mouse su un'attività che dispone di annotazione. Selezionare **annotazioni**, **Mostra tutte le annotazioni**.  
  
2. Tutte le annotazioni verranno visualizzate nelle finestre di progettazione dell'attività.  
  
3. Per visualizzare tutte le annotazioni di fuori di finestre di progettazione dell'attività, fare clic su attività e selezionare **annotazioni**, **Nascondi tutte le annotazioni**.  
  
### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Modifica o eliminazione di un'annotazione per un'attività  
  
1. Fare clic con il pulsante destro del mouse su un'attività che dispone di un'annotazione.  
  
2. Selezionare **annotazioni**, **Modifica annotazione** oppure **Elimina annotazione**.  
  
3. L'annotazione verrà aperta per la modifica o l'eliminazione.  
  
4. Per eliminare tutte le annotazioni in una sola volta, fare doppio clic su flusso di lavoro della finestra di progettazione e seleziona **Annotation**, **eliminare tutte le annotazioni**.  
  
### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Aggiunta, modifica ed eliminazione di un'annotazione per una variabile o un argomento  
  
1. Fare clic con il pulsante destro del mouse su una variabile o un argomento e selezionare Aggiungi annotazione.  
  
2. Immettere il testo dell'annotazione. Nella variabile o nell'argomento verrà visualizzata un'icona dell'annotazione.  
  
3. Fare clic con il pulsante destro del mouse su una variabile o un argomento che dispone di un'annotazione. Selezionare Modifica annotazione.  
  
4. L'annotazione verrà aperta per la modifica.  
  
5. Fare clic con il pulsante destro del mouse su una variabile o un argomento che dispone di un'annotazione. Selezionare Elimina annotazione.  
  
6. L'annotazione verrà eliminata.