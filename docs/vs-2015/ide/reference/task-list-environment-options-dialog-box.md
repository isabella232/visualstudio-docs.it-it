---
title: Elenco attività, Ambiente, finestra di dialogo Opzioni | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPag.Environment.Task_List
- VS.ToolsOptionsPages.Environment.TaskList
- VS.Environment.Task List
helpviewer_keywords:
- Token List
- tokens
- icons, in Task List
- Task List, customizing environment
- Options dialog box, Task List environment
- exclamation points
- comments, comment tasks in Task List
- tokens, and the Task List
- Task List, comment tasks
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d96543e5f8cc7d1513f335fc6a54f669dfa5f356
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532512"
---
# <a name="task-list-environment-options-dialog-box"></a>Elenco attività, Ambiente, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Task List, Environment, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/task-list-environment-options-dialog-box).  
  
  
La pagina Opzioni consente di aggiungere, eliminare e modificare i token di commento che generano i promemoria di **Elenco attività**. Per visualizzare queste impostazioni selezionare **Opzioni** dal menu **Strumenti**, espandere la cartella **Ambiente** e quindi scegliere **Elenco attività**.  
  
## <a name="task-list-options"></a>Opzioni di Elenco attività  
 Chiedi conferma prima di eliminare un'attività  
 Quando questa opzione è selezionata, viene visualizzata una finestra di messaggio ogni volta che un'attività utente viene eliminata da **Elenco attività** in modo da poter confermare l'eliminazione. Questa opzione è selezionata per impostazione predefinita.  
  
> [!NOTE]
>  Per eliminare il commento di un'attività, usare il collegamento per trovare il commento e quindi rimuoverlo dal codice.  
  
 Mostra solo nomi file  
 Quando questa opzione è selezionata, nella colonna **File** di **Elenco attività** vengono visualizzati solo i nomi dei file da modificare e non i percorsi completi.  
  
## <a name="tokens"></a>token  
 Quando si inserisce un commento nel codice il cui testo inizia con un token proveniente da **Elenco token**, in **Elenco attività** il commento viene visualizzato come nuova voce ogni volta che il file viene aperto per la modifica. È possibile fare clic su questa voce di **Elenco attività** per passare direttamente alla riga del commento nel codice. Per altre informazioni, vedere [Uso dell'elenco attività](../../ide/using-the-task-list.md).  
  
 Elenco dei token  
 Visualizza un elenco di token e permette di aggiungere o rimuovere token personalizzati. I token di commento fanno distinzione tra maiuscole e minuscole in Visual C# e Visual C++, ma non in Visual Basic.  
  
> [!NOTE]
>  Se non si digita il token desiderato esattamente come è specificato in **Elenco token**, non verrà visualizzata alcuna attività di commento in **Elenco attività**.  
  
 Priorità  
 Imposta la priorità delle attività che usano il token selezionato. Ai commenti delle attività che iniziano con questo token viene automaticamente assegnata la priorità designata in **Elenco attività**.  
  
 nome  
 Immettere la stringa del token. Viene abilitato il pulsante **Aggiungi**. Quando si sceglie il pulsante **Aggiungi**, questa stringa viene inclusa in **Elenco token** e i commenti che iniziano con questo nome verranno visualizzati in **Elenco attività**.  
  
 Aggiunta  
 Pulsante abilitato quando si immette un nuovo **Nome**. Fare clic su questo pulsante per aggiungere una nuova stringa di token usando i valori immessi nei campi **Nome** e **Priorità**.  
  
 Eliminare  
 Fare clic su questo pulsante per eliminare il token selezionato da **Elenco token**. Non è possibile eliminare il token di commento predefinito.  
  
 Modifica  
 Fare clic su questo pulsante per apportare modifiche a un token esistente usando i valori immessi nei campi **Nome** e **Priorità**.  
  
> [!NOTE]
>  Non è possibile rinominare o eliminare il token di commento predefinito, ma è possibile modificarne il livello di priorità.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso dell'elenco attività](../../ide/using-the-task-list.md)   
 [Impostazione di segnalibri nel codice](../../ide/setting-bookmarks-in-code.md)   
 [Finestra di dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md)



