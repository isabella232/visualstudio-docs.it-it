---
ms.date: 08/11/2021
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jmartens
ms.topic: include
ms.openlocfilehash: 058bb38112e89ed77cc01eae59d16a827c88c11a
ms.sourcegitcommit: 51a01cc1f1feeac9432c7989db4578e30a573fa1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2021
ms.locfileid: "122274086"
---
::: moniker range=">=vs-2019"

## <a name="add-git-source-control"></a>Aggiungere il controllo del codice sorgente Git

Dopo aver creato l'app, è possibile aggiungerla a un repository Git. L'utente è stato coperto. Visual Studio semplifica questo processo con gli strumenti Git che è possibile usare direttamente dall'IDE.

> [!TIP]
> Git è il sistema di controllo della versione moderno più diffuso, quindi, sia che si sia uno sviluppatore professionale che si sta imparando a creare codice, Git può essere molto utile. Se non si ha di nuovo git, [https://git-scm.com/](https://git-scm.com/) il sito Web è un buon punto di partenza. Qui sono disponibili fogli di informazioni, un libro online molto diffuso e video di git basics.

Per associare il codice a Git, iniziare creando un nuovo repository Git in cui si trova il codice. Ecco come.

1. Nella barra di stato nell'angolo inferiore destro di  Visual Studio selezionare il pulsante Aggiungi al controllo del codice sorgente e quindi **git.**

    :::image type="content" source="../media/vs-2022/git-add-source-control.png" alt-text="Screenshot dei pulsanti del controllo del codice sorgente Git sotto il riquadro Esplora soluzioni, con il pulsante Aggiungi al controllo del codice sorgente evidenziato.":::

1. Nella finestra **di dialogo Crea un repository Git** accedere a GitHub.

    :::image type="content" source="../media/vs-2022/git-create-repo.png" alt-text="Screenshot della finestra di dialogo Crea un repository Git in cui è possibile accedere a GitHub.":::

    Il nome del repository viene popolato automaticamente in base al percorso della cartella. Per impostazione predefinita, il nuovo repository è privato, ovvero l'utente è l'unico che può accedervi.

    > [!TIP]
    > Indipendentemente dal fatto che il repository sia pubblico o privato, è meglio avere un backup remoto del codice archiviato in modo sicuro in GitHub anche se non si lavora con un team. In questo modo il codice sarà disponibile anche per l'utente, indipendentemente dal computer in uso.

1. Selezionare **Crea ed esegui push**.

    Dopo aver creato il repository, nella barra di stato verranno visualizzati i dettagli sullo stato.

    :::image type="content" source="../media/vs-2022/git-new-private-repo-status-details.png" alt-text="Screenshot della barra di stato del Esplora soluzioni nella Visual Studio.":::

    La prima icona con le frecce indica il numero di commit in uscita/in ingresso presenti nel ramo corrente. È possibile usare questa icona per eseguire il pull di qualsiasi commit in ingresso o per eseguire il push di eventuali commit in uscita. È anche possibile scegliere di visualizzare prima questi commit. A tale scopo, fare clic sull'icona e quindi selezionare **Visualizza in uscita/In ingresso.**

    La seconda icona con la matita mostra il numero di modifiche di cui non è stato eseguito ilcommitted al codice. È possibile fare clic su questa icona per visualizzare le modifiche nella **finestra Git Changes (Modifiche** Git).

Per altre informazioni su come usare Git con l'app, vedere la pagina Visual Studio [della documentazione sul controllo della versione.](../../version-control/index.yml)

::: moniker-end