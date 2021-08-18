---
title: Usare l'elenco attività
description: Informazioni su come Elenco attività in Visual Studio consentono di tenere traccia e usare i commenti del codice in modo più efficiente.
ms.date: 10/12/2020
ms.topic: how-to
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: c20f0b6eb2a496455469f3bc7404839954add74d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116799"
---
# <a name="use-the-task-list"></a>Usare l'elenco attività

Usare **Elenco attività** per tenere traccia dei commenti di codice che usano token quali `TODO` e `HACK`, o token personalizzati, e per gestire i collegamenti che indirizzano direttamente a una posizione predefinita nel codice. Fare clic sull'elemento nell'elenco per passare alla relativa posizione nel codice sorgente.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Commenti dell'attività (Visual Studio per Mac)](/visualstudio/mac/task-comments).

## <a name="the-task-list-window"></a>Finestra Elenco attività

Quando è aperta, la finestra **Elenco attività** viene visualizzata nella parte inferiore della finestra dell'applicazione.

Per aprire **Elenco attività**, selezionare **Visualizza** > **Elenco attività** o premere **CTRL**+**\\**,**T**.

![Finestra Elenco attività](../ide/media/vs2015_task_list.png)

Per modificare l'ordinamento dell'elenco, selezionare l'intestazione di qualsiasi colonna. Per perfezionare ulteriormente i risultati della ricerca, premere **MAIUSC** e fare clic su una seconda intestazione di colonna. In alternativa, nel menu di scelta rapida scegliere **Ordina per** e quindi scegliere un'intestazione. Per perfezionare ulteriormente i risultati della ricerca, premere **MAIUSC** e scegliere una seconda intestazione.

Per mostrare o nascondere le colonne, nel menu di scelta rapida scegliere **Mostra colonne**. Scegliere le colonne che si vuole mostrare o nascondere.

Per modificare l'ordine delle colonne, trascinare qualsiasi intestazione di colonna nella posizione desiderata.

## <a name="user-tasks"></a>Attività dell'utente

La funzionalità Attività definite dall'utente è stata rimossa a partire da Visual Studio 2015. Quando si apre una soluzione che contiene dati di attività definite dall'utente in Visual Studio 2013 e versioni precedenti, i dati contenuti nel file con estensione *suo* non vengono modificati, ma le attività definite dall'utente non vengono visualizzate nell'elenco attività.

Per continuare ad accedere e aggiornare i dati delle attività definite dall'utente, aprire il progetto in Visual Studio 2013 e copiare il contenuto di tutte le attività definite dall'utente nello strumento di gestione dei progetti preferito (ad esempio Team Foundation Server).

## <a name="tokens-and-comments"></a>Token e commenti

Nella finestra **Elenco attività** viene inoltre visualizzato un commento nel codice preceduto da un marcatore di commento e un token predefinito. Ad esempio, il commento C# indicato di seguito è costituito da tre parti distinte.

- Marcatore di commento (`//`)

- Token, ad esempio (`TODO`)

- Commento (testo rimanente)

```csharp
// TODO: Load state from previously suspended application
```

Poiché `TODO` è un token predefinito, questo commento viene visualizzato nell'elenco come attività `TODO`.

### <a name="custom-tokens"></a>Token personalizzati

Per impostazione predefinita, Visual Studio include i token seguenti: `HACK`, `TODO`, `UNDONE` e `UnresolvedMergeConflict`. Per i token non viene fatta distinzione tra maiuscole e minuscole. È inoltre possibile creare token personalizzati.

> [!NOTE]
> I token predefiniti sono disponibili solo per i linguaggi C/C++, C# e VB linguaggi. Per creare token personalizzati per altri linguaggi di programmazione, seguire questa procedura.

Per creare un token personalizzato:

1. Scegliere **Opzioni** dal menu **Strumenti**.

2. Aprire la cartella **Ambiente** e selezionare **Elenco attività**.

   Verrà visualizzata la pagina [Opzioni elenco attività](../ide/reference/task-list-environment-options-dialog-box.md).

   ![Elenco attività di Visual Studio](../ide/media/vs2015_task_list_options.png)

3. Nella casella di testo **Nome** immettere il nome del token, ad esempio **BUG**.

4. Nell'elenco a discesa di **Priorità** scegliere una priorità predefinita per il nuovo token.

5. Scegliere **Aggiungi**.

> [!TIP]
> Il pulsante **Aggiungi** viene abilitato dopo avere immesso un nome. È necessario immettere un nome prima di fare clic su **Aggiungi**.

### <a name="c-todo-comments"></a>Commenti TODO C++

Per impostazione predefinita, i commenti TODO C++ vengono visualizzati nella finestra **Elenco attività**.

Per disattivare i commenti TODO C++, dal menu **Strumenti** scegliere **Opzioni** > **Editor di testo** > **C/C++** > **Visualizza** > **Enumera attività di commento** e impostare il valore su **false**.

## <a name="shortcuts"></a>Collegamenti

Un *collegamento* è un segnalibro nel codice di cui viene tenuta traccia nell'**Elenco attività**. Ha un'icona diversa rispetto a un segnalibro normale. Fare doppio clic sul collegamento in **Elenco attività** per passare alla posizione corrispondente nel codice.

![Icona di collegamento di Elenco attività di Visual Studio](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Creare un collegamento

Per creare un collegamento, posizionare il puntatore nella parte del codice in cui si vuole aggiungere il collegamento. Scegliere **Modifica**  >  **segnalibri Aggiungi** Elenco attività collegamento  >  **oppure** premere **CTRL** + **K**, **CTRL** + **H**.

Per spostarsi tra i collegamenti nel codice, scegliere un collegamento nell'elenco, quindi fare clic su **Attività successiva** o **Attività precedente** nel menu di scelta rapida.

## <a name="see-also"></a>Vedi anche

- [Elenco attività, Ambiente, finestra di dialogo Opzioni](../ide/reference/task-list-environment-options-dialog-box.md)
- [Commenti dell'attività (Visual Studio per Mac)](/visualstudio/mac/task-comments)
