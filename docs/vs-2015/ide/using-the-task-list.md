---
title: Uso dell'elenco attività | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
ms.assetid: f46a75a8-47b3-4cb6-bb59-b72e3356a664
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9c9526b2deaafb36e991afce6d29ace47f8564ba
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091408"
---
# <a name="using-the-task-list"></a>Utilizzo dell'elenco attività
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usare **Elenco attività** per tenere traccia dei commenti di codice che usano token quali `TODO` e `HACK`, o token personalizzati, e per gestire i collegamenti che indirizzano direttamente a una posizione predefinita nel codice. Fare clic sull'elemento nell'elenco per passare alla relativa posizione nel codice sorgente.  
  
 In questo argomento  
  
- [Finestra Elenco attività](../ide/using-the-task-list.md#taskListWindow)  
  
- [Attività definite dall'utente](../ide/using-the-task-list.md#userTasks)  
  
- [Token e commenti](../ide/using-the-task-list.md#tokensComments)  
  
- [Token personalizzati](../ide/using-the-task-list.md#customTokens)  
  
- [Commenti TODO C++](../ide/using-the-task-list.md#cppComments)  
  
- [Collegamenti](../ide/using-the-task-list.md#shortcuts)  
  
## <a name="taskListWindow"></a> Finestra Elenco attività  
 Quando è aperta, la finestra **Elenco attività** viene visualizzata nella parte inferiore della finestra dell'applicazione.  
  
#### <a name="to-open-the-task-list"></a>Per aprire Elenco attività  
  
- Nel menu **Visualizza** scegliere **Elenco attività** (tastiera: CTRL+\\,T).  
  
     ![Finestra Elenco attività](../ide/media/vs2015-task-list.png "vs2015_task_list")  
  
#### <a name="to-change-the-sort-order-of-the-list"></a>Per modificare l'ordinamento dell'elenco  
  
- Fare clic sull'intestazione di una colonna qualsiasi. Per perfezionare ulteriormente i risultati della ricerca, premere il tasto MAIUSC e fare clic su una seconda intestazione di colonna.  
  
     In alternativa, nel menu di scelta rapida scegliere **Ordina per**e selezionare un'intestazione. Per perfezionare ulteriormente i risultati della ricerca, premere il tasto MAIUSC e scegliere una seconda intestazione.  
  
#### <a name="to-show-or-hide-columns"></a>Per mostrare o nascondere colonne  
  
- Fare clic su **Mostra colonne**nel menu di scelta rapida. Scegliere le colonne che si desidera mostrare o nascondere.  
  
#### <a name="to-change-the-order-of-the-columns"></a>Per modificare l'ordine delle colonne  
  
- Trascinare un'intestazione di colonna qualsiasi nella posizione desiderata.  
  
## <a name="userTasks"></a> Attività definite dall'utente  
 La funzionalità Attività definite dall'utente è stata rimossa in Visual Studio 2015. Quando si apre in Visual Studio 2015 una soluzione che contiene dati delle attività definite dall'utente in Visual Studio 2013 e versioni precedenti, i dati contenuti nel file SUO non verranno modificati, ma le attività definite dall'utente non verranno visualizzate nell'elenco attività.  
  
 Per continuare ad accedere e aggiornare i dati delle attività definite dall'utente, è necessario aprire il progetto in Visual Studio 2013 e copiare il contenuto di tutte le attività definite dall'utente nello strumento di gestione dei progetti preferito (ad esempio Team Foundation Server).  
  
## <a name="tokensComments"></a> Token e commenti  
 Nella finestra **Elenco attività** verrà anche visualizzato un commento nel codice preceduto da un marcatore di commento e un token predefinito. Ad esempio, il commento C# indicato di seguito è costituito da tre parti distinte.  
  
- Marcatore di commento (`//`)  
  
- Token, ad esempio (`TODO`)  
  
- Commento (testo rimanente)  
  
```  
// TODO: Load state from previously suspended application  
```  
  
 Poiché `TODO` è un token predefinito, questo commento verrà visualizzato come attività `TODO` nell'elenco.  
  
### <a name="customTokens"></a> Token personalizzati  
 Per impostazione predefinita, Visual Studio include i seguenti token: HACK, TODO, UNDONE, NOTE. I token non fanno distinzione tra maiuscole e minuscole.  
  
 È inoltre possibile creare token personalizzati.  
  
##### <a name="to-create-a-custom-token"></a>Per creare un token personalizzato  
  
1. Scegliere **Opzioni** dal menu **Strumenti**.  
  
2. Aprire la cartella **Ambiente** e selezionare **Elenco attività**.  
  
     È così possibile visualizzare [Elenco attività, Ambiente, finestra di dialogo Opzioni](../ide/reference/task-list-environment-options-dialog-box.md).  
  
     ![Elenco attività di Visual Studio](../ide/media/vs2015-task-list-options.png "vs2015_task_list_options")  
  
3. Nella casella di testo **Nome** della categoria **Token** immettere il nome del token, ad esempio "BUG".  
  
4. Nell'elenco a discesa di **Priorità** scegliere una priorità predefinita per il nuovo token. Scegliere il pulsante **Aggiungi**.  
  
### <a name="cppComments"></a> Commenti TODO C++  
 Per impostazione predefinita, i commenti TODO C++ vengono visualizzati nella finestra **Elenco attività** . È possibile modificare questo comportamento.  
  
##### <a name="to-turn-off-c-todo-comments"></a>Per disattivare i commenti TODO C++  
  
1. Nel menu **Strumenti** andare a **Opzioni &#124; Editor di testo &#124; C/C++ &#124; Visualizza &#124; Enumera attività di commento** e impostare il valore su False.  
  
2. Nella finestra di dialogo **Opzioni** aprire **Editor di testo**.  
  
3. In **C/C++** scegliere **Visualizza**, quindi impostare **Enumera attività di commento** su **False**.  
  
## <a name="shortcuts"></a> Collegamenti  
 Un *collegamento* è un segnalibro nel codice che viene rilevato nell' **Elenco attività**. Ha un'icona diversa rispetto a un segnalibro normale. Fare doppio clic sul collegamento in **Elenco attività** per passare alla posizione corrispondente nel codice.  
  
 ![Icona di collegamento Elenco attività di Visual Studio](../ide/media/vs2015-task-list-bookmark.png "vs2015_task_list_bookmark")  
  
#### <a name="to-create-a-shortcut"></a>Per creare un collegamento  
  
- Posizionare il puntatore nella parte del codice in cui si desidera aggiungere un collegamento. Scegliere **Modifica &#124; Segnalibri &#124; Aggiungi collegamento Elenco attività** o premere (tastiera: Ctrl+K, Ctrl+H).  
  
     Per spostarsi tra i collegamenti nel codice, scegliere un collegamento nell'elenco, quindi fare clic su **Attività successiva** o **Attività precedente** nel menu di scelta rapida.  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco attività, Ambiente, finestra di dialogo Opzioni](../ide/reference/task-list-environment-options-dialog-box.md)
