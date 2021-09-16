---
ms.date: 08/30/2021
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jmartens
ms.topic: include
ms.openlocfilehash: e045d40958e339d497cea8509110618769649182
ms.sourcegitcommit: 559c662b2d60048300b76ea6ed3defaa2a259492
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2021
ms.locfileid: "127833351"
---
::: moniker range=">=vs-2019"

## <a name="add-git-source-control"></a>Aggiungere il controllo del codice sorgente Git

Dopo aver creato un'app, è possibile aggiungerla a un repository Git. È tutto sotto controllo. Visual Studio semplifica questo processo con gli strumenti Git che è possibile usare direttamente dall'IDE.

> [!TIP]
> Git è il sistema di controllo della versione moderno più usato, quindi, che si sia uno sviluppatore professionista o si sta imparando a codificare, Git può essere molto utile. Se non si ha una buona idea di Git, il sito [https://git-scm.com/](https://git-scm.com/) Web è un buon punto di partenza. Qui sono disponibili fogli di trucchi, un popolare libro online e video di Git Basics.

Per associare il codice a Git, iniziare creando un nuovo repository Git in cui si trova il codice. Ecco come:

1. Nella barra di stato nell'angolo inferiore destro del Visual Studio selezionare Aggiungi **al** controllo del codice sorgente e quindi **Git.**

    :::image type="content" source="../media/vs-2022/git-add-source-control.png" alt-text="Screenshot dei pulsanti del controllo del codice sorgente Git sotto il riquadro Esplora soluzioni, con il pulsante Aggiungi al controllo del codice sorgente evidenziato.":::

1. Nella finestra **di dialogo Crea un repository Git** accedere a GitHub.

    :::image type="content" source="../media/vs-2022/git-create-repo.png" alt-text="Screenshot della finestra di dialogo Crea un repository Git in cui è possibile accedere a GitHub.":::

    Il nome del repository viene popolato automaticamente in base al percorso della cartella. Per impostazione predefinita, il nuovo repository è privato, ovvero l'utente è l'unico che può accedervi.

    > [!TIP]
    > Indipendentemente dal fatto che il repository sia pubblico o privato, è meglio avere un backup remoto del codice archiviato in modo sicuro GitHub. Anche se non si lavora con un team, un repository remoto rende disponibile il codice da qualsiasi computer.

1. Selezionare **Crea ed esegui push**.

    Dopo aver creato il repository, nella barra di stato vengono visualizzati i dettagli sullo stato.

    :::image type="content" source="../media/vs-2022/git-new-private-repo-status-details.png" alt-text="Screenshot della barra di stato del riposino sotto il riquadro Esplora soluzioni in Visual Studio.":::

    La prima icona con le frecce mostra il numero di commit in uscita/in ingresso presenti nel ramo corrente. È possibile usare questa icona per eseguire il pull di qualsiasi commit in ingresso o per eseguire il push di qualsiasi commit in uscita. È anche possibile scegliere di visualizzare prima questi commit. A tale scopo, selezionare l'icona e quindi **selezionare Visualizza in uscita/in ingresso**.

    La seconda icona con la matita mostra il numero di modifiche di cui non è stato eseguito ilcommitted al codice. È possibile selezionare questa icona per visualizzare le modifiche nella **finestra Modifiche** git.

Per altre informazioni su come usare Git con l'app, vedere la documentazione Visual Studio [controllo della versione.](../../version-control/index.yml)

::: moniker-end