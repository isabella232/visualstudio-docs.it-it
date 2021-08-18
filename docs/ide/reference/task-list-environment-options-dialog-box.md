---
title: Elenco attività, Ambiente, finestra di dialogo Opzioni
description: Informazioni su come usare la Elenco attività nella sezione Ambiente per aggiungere, eliminare e modificare i token di commento che generano Elenco attività promemoria.
ms.custom: SEO-VS-2020
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 380ffd8f39590218ecbe82cde464b227a1046e8e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056056"
---
# <a name="options-dialog-box-environment--task-list"></a>Finestra di dialogo Opzioni: Ambiente \> Elenco attività

La pagina Opzioni consente di aggiungere, eliminare e modificare i token di commento che generano i promemoria di **Elenco attività**. Per visualizzare queste impostazioni selezionare **Opzioni** dal menu **Strumenti**, espandere la cartella **Ambiente** e quindi scegliere **Elenco attività**.

## <a name="task-list-tokens"></a>Token elenco attività

Quando si inserisce un commento nel codice il cui testo inizia con un token proveniente da **Elenco token**, in **Elenco attività** il commento viene visualizzato come nuova voce ogni volta che il file viene aperto per la modifica. Fare clic su una voce in **Elenco attività** per passare direttamente alla riga del commento nel codice. Per altre informazioni, vedere [Uso dell'elenco attività](../../ide/using-the-task-list.md).

Elenco dei token\
Visualizza un elenco di token e permette di aggiungere o rimuovere token personalizzati. Per i token di commento viene fatta distinzione tra maiuscole e minuscole in C# e C++, ma non in Visual Basic.

> [!NOTE]
> Se non si digita il token desiderato esattamente come è specificato nell'elenco dei token, non verrà visualizzata alcuna attività di commento in **Elenco attività**.

Priorità\
Imposta la priorità delle attività che usano il token selezionato (bassa, normale o alta). Ai commenti delle attività che iniziano con questo token viene automaticamente assegnata la priorità designata in **Elenco attività**.

Nome\
Immettere la stringa del token e quindi fare clic su **Aggiungi** per aggiungere la stringa all'elenco di token.

Aggiungi\
Pulsante abilitato quando si immette un nuovo **Nome**. Fare clic su questo pulsante per aggiungere una nuova stringa di token usando i valori immessi nei campi **Nome** e **Priorità**.

Elimina\
Fare clic per eliminare il token selezionato dall'elenco di token. Non è possibile eliminare il token di commento predefinito.

Modifica\
Fare clic su questo pulsante per apportare modifiche a un token esistente usando i valori immessi nei campi **Nome** e **Priorità**.

> [!NOTE]
> Non è possibile rinominare o eliminare il token di commento predefinito, ma è possibile modificarne il livello di priorità.

## <a name="see-also"></a>Vedi anche

- [Usare l'elenco attività](../../ide/using-the-task-list.md)
- [Impostare segnalibri nel codice](../../ide/setting-bookmarks-in-code.md)
