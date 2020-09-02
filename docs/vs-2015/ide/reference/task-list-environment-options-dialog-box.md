---
title: Elenco attività, Ambiente, finestra di dialogo Opzioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72e5f82fa3ca4b7ca909ee07e5b77a31b3e20879
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72650969"
---
# <a name="task-list-environment-options-dialog-box"></a>Elenco attività, Ambiente, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La pagina Opzioni consente di aggiungere, eliminare e modificare i token di commento che generano i promemoria di **Elenco attività**. Per visualizzare queste impostazioni selezionare **Opzioni** dal menu **Strumenti**, espandere la cartella **Ambiente** e quindi scegliere **Elenco attività**.

## <a name="task-list-options"></a>Opzioni di Elenco attività
 Confermare l'eliminazione delle attività quando viene selezionata, viene visualizzata una finestra di messaggio ogni volta che un'attività utente viene eliminata dal **elenco attività**, consentendo di confermare l'eliminazione. Questa opzione è selezionata per impostazione predefinita.

> [!NOTE]
> Per eliminare il commento di un'attività, usare il collegamento per trovare il commento e quindi rimuoverlo dal codice.

 Mostra i nomi di file solo quando è selezionata, nella colonna **file** della **elenco attività** vengono visualizzati solo i nomi dei file da modificare e non i percorsi completi.

## <a name="tokens"></a>Tokens
 Quando si inserisce un commento nel codice il cui testo inizia con un token proveniente da **Elenco token**, in **Elenco attività** il commento viene visualizzato come nuova voce ogni volta che il file viene aperto per la modifica. È possibile fare clic su questa voce di **Elenco attività** per passare direttamente alla riga del commento nel codice. Per altre informazioni, vedere [Uso dell'elenco attività](../../ide/using-the-task-list.md).

 Elenco di token Visualizza un elenco di token e consente di aggiungere o rimuovere token personalizzati. I token di commento fanno distinzione tra maiuscole e minuscole in Visual C# e Visual C++, ma non in Visual Basic.

> [!NOTE]
> Se non si digita il token desiderato esattamente come è specificato in **Elenco token**, non verrà visualizzata alcuna attività di commento in **Elenco attività**.

 Priority imposta la priorità delle attività che utilizzano il token selezionato. Ai commenti delle attività che iniziano con questo token viene automaticamente assegnata la priorità designata in **Elenco attività**.

 Nome immettere la stringa del token. Viene abilitato il pulsante **Aggiungi**. Quando si sceglie il pulsante **Aggiungi**, questa stringa viene inclusa in **Elenco token** e i commenti che iniziano con questo nome verranno visualizzati in **Elenco attività**.

 Aggiungere abilitato quando si immette un nuovo **nome**. Fare clic su questo pulsante per aggiungere una nuova stringa di token usando i valori immessi nei campi **Nome** e **Priorità**.

 Elimina fare clic per eliminare il token selezionato dall' **elenco dei token**. Non è possibile eliminare il token di commento predefinito.

 Modifica fare clic per apportare modifiche a un token esistente usando i valori immessi nei campi **nome** e **priorità** .

> [!NOTE]
> Non è possibile rinominare o eliminare il token di commento predefinito, ma è possibile modificarne il livello di priorità.

## <a name="see-also"></a>Vedere anche
 [Utilizzo dell'impostazione elenco attività](../../ide/using-the-task-list.md) [segnalibri nella finestra di](../../ide/setting-bookmarks-in-code.md) [dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md) codice
