---
title: 'Procedura: aggiungere commenti a un flusso di lavoro nella finestra di progettazione del flusso di lavoro | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: "7"
ms.author: sdanie
manager: erikre
ms.workload: multiple
ms.openlocfilehash: e4d547fed57abf11194b35bcd3ac42f12322374b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Procedura: aggiungere commenti a un flusso di lavoro in Progettazione del flusso di lavoro
Per facilitare la creazione di flussi di lavoro più ampi e complessi, [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] consente allo sviluppatore di aggiungere annotazioni ai seguenti tipi di elementi nella finestra di progettazione:  
  
-   <xref:System.Activities.Activity>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
-   Classi derivate da <xref:System.Activities.Statements.FlowNode>  
  
-   <xref:System.Activities.Variable>  
  
-   <xref:System.Activities.Argument>  
  
> [!IMPORTANT]
>  Il contenuto di un'annotazione viene salvato come testo normale nel file XAML associato al flusso di lavoro e potrebbe potenzialmente essere letto da altri. Prestare attenzione quando vengono fornite informazioni riservate in un'unica annotazione.  
  
### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Aggiunta di un'annotazione a un'attività nella finestra di progettazione  
  
1.  Nella finestra di progettazione del flusso di lavoro, fare clic su un elemento nel flusso di lavoro della finestra di progettazione e seleziona **annotazioni**, **Aggiungi annotazione**.  
  
2.  Aggiungere il testo dell'annotazione nello spazio disponibile.  
  
3.  Nell'elemento verrà visualizzata un'icona dell'annotazione. Passare il mouse sull'icona di annotazione per visualizzare il testo dell'annotazione.  
  
     ![Sequenza di attività con annotazione](../debugger/debug-interface-access/annotation.md "annotazione")  
  
### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Visualizzazione di un'annotazione della finestra di progettazione dell'attività  
  
1.  Con un ActivityDesigner che dispone di un'annotazione verrà visualizzata all'esterno dell'attività, fare clic su di **Pin** sull'icona dello strumento decorativo di annotazione.  
  
2.  Le annotazioni vengono visualizzati nella finestra di progettazione dell'attività. Nella schermata riportata di seguito, l'annotazione "inizia attività nel flusso di lavoro" viene visualizzata nella finestra di progettazione dell'attività.  
  
     ![Annotazione visualizzata nella finestra di progettazione attività](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")  
  
3.  Per visualizzare l'annotazione all'esterno di progettazione dell'attività, passa il mouse sull'area dell'annotazione nella finestra di progettazione dell'attività e scegliere il **Sblocca** icona  
  
     ![Annotazione visualizzata all'esterno di progettazione di un'attività](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")  
  
### <a name="showing-or-hiding-all-annotations"></a>Mostra o nascondi tutte le annotazioni  
  
1.  Fare clic con il pulsante destro del mouse su un'attività che dispone di annotazione. Selezionare **annotazioni**, **Mostra tutte le annotazioni**.  
  
2.  Tutte le annotazioni verranno visualizzate nelle finestre di progettazione dell'attività.  
  
3.  Per visualizzare tutte le annotazioni di fuori di finestre di progettazione dell'attività, fare clic su attività e selezionare **annotazioni**, **nascondere tutte le annotazioni**.  
  
### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Modifica o eliminazione di un'annotazione per un'attività  
  
1.  Fare clic con il pulsante destro del mouse su un'attività che dispone di un'annotazione.  
  
2.  Selezionare **annotazioni**, **Modifica annotazione** o **Elimina annotazione**.  
  
3.  L'annotazione verrà aperta per la modifica o l'eliminazione.  
  
4.  Per eliminare tutte le annotazioni in una sola volta, fare doppio clic sul flusso di lavoro della finestra di progettazione e seleziona **annotazione**, **Elimina tutte le annotazioni**.  
  
### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Aggiunta, modifica ed eliminazione di un'annotazione per una variabile o un argomento  
  
1.  Fare clic con il pulsante destro del mouse su una variabile o un argomento e selezionare Aggiungi annotazione.  
  
2.  Immettere il testo dell'annotazione. Nella variabile o nell'argomento verrà visualizzata un'icona dell'annotazione.  
  
3.  Fare clic con il pulsante destro del mouse su una variabile o un argomento che dispone di un'annotazione. Selezionare Modifica annotazione.  
  
4.  L'annotazione verrà aperta per la modifica.  
  
5.  Fare clic con il pulsante destro del mouse su una variabile o un argomento che dispone di un'annotazione. Selezionare Elimina annotazione.  
  
6.  L'annotazione verrà eliminata.