---
title: 'Esercitazione: Aprire un progetto da un Visual Studio 2017'
description: Informazioni su come aprire un progetto in un repository Git o Azure DevOps usando Visual Studio 2017.
ms.custom: vs-acquisition, get-started
ms.date: 02/15/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2017
ms.openlocfilehash: 6b69a138689c7351b51e5674b587911a41eb61c7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078583"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>Esercitazione: Aprire un progetto da un Visual Studio 2017

In questa esercitazione si userà Visual Studio 2017 per connettersi a un repository per la prima volta e quindi aprire un progetto da esso.

> [!TIP]
> Esiste un nuovo modo completamente integrato per connettersi a un GitHub di lavoro in [Visual Studio 2019.](https://visualstudio.microsoft.com/downloads) Per altre informazioni, vedere la [**pagina Nuova esperienza Git Visual Studio 2019.**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true)

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Aprire un progetto da un GitHub 2017 usando Visual Studio 2017

1. Aprire Visual Studio 2017.

1. Nella barra dei menu superiore selezionare **Apri file** dal controllo del  >    >  **codice sorgente.**

   Si apre il riquadro **Team Explorer - Connetti**.

    ![Finestra Team Explorer nell'IDE di Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Nella sezione **Repository Git locali** selezionare **Clona.**

    ![Scegliere Clona dalla sezione Repository Git locali](./media/open-proj-repo-local-git-repo-clone.png)

1. Nella casella * Immettere **l'URL** di un repository Git per clonare _, digitare o incollare l'URL del repository e quindi premere _*Invio**. Se viene visualizzata la richiesta di accedere a GitHub, eseguire questa operazione.

   Quando Visual Studio ha clonato il repository, Team Explorer si chiude e si apre Esplora soluzioni. Viene visualizzato il messaggio *Fare clic sopra su "Soluzioni e cartelle" per visualizzare un elenco di soluzioni*. Scegliere **Soluzioni e cartelle**.

   ![Scegliere "Soluzioni e cartelle" in Esplora soluzioni](./media/open-proj-repo-github-solutions-folders.png)

1. Se si ha un file di soluzione disponibile, verrà visualizzato nel menu a comparsa "Soluzioni e cartelle". Selezionarlo e Visual Studio aprirà la soluzione.

   ![Scegliere cosa si vuole aprire nell'elenco a discesa Esplora soluzioni](./media/open-proj-repo-github-solutions-folders-picker.png)

   Se nel repository non è disponibile un file di soluzione (con estensione sln), il menu a comparsa indicherà che "Non sono state trovate soluzioni". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

### <a name="review-your-work"></a>Esaminare il lavoro

Visualizzare l'animazione seguente per verificare il lavoro completato nella sezione precedente.

   ![Animazione dell'apertura di un progetto in un repository GitHub con Visual Studio](./media/open-project-from-github.gif)

> [!NOTE]
> Per informazioni specifiche di Visual Studio 2019, vedere la pagina Aprire un progetto da un Visual Studio [2019.](tutorial-open-project-from-repo-visual-studio-2019.md)

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Aprire un progetto da un Azure DevOps 2017 usando Visual Studio 2017

1. Aprire Visual Studio 2017.

1. Nella barra dei menu superiore selezionare **Apri file** dal controllo del  >    >  **codice sorgente.**

   Si apre il riquadro **Team Explorer - Connetti**.

    ![Finestra Team Explorer nell'IDE di Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Esistono due modi per connettersi al repository Azure DevOps:

      - Nella sezione **Provider di servizi ospitati** selezionare **Connessione...**.

        ![La sezione Provider di servizi ospitati della finestra Team Explorer nell'IDE di Visual Studio](./media/open-proj-repo-azure-devops.png)

      - **Nell'elenco a** discesa Gestisci connessioni selezionare Connessione **a un Project...**.

        ![La sezione Gestione connessioni della finestra Team Explorer nell'IDE di Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Nella finestra **Connessione a un Project** scegliere il repo a cui connettersi e quindi selezionare **Clona.**

      ![Finestra di Connessione a un Project' generata da Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ciò che compare nella casella di riepilogo dipende dai repository Azure DevOps ai quali si ha accesso.

1. Quando Visual Studio ha clonato il repository, Team Explorer si chiude e si apre Esplora soluzioni. Viene visualizzato il messaggio *Fare clic sopra su "Soluzioni e cartelle" per visualizzare un elenco di soluzioni*. Scegliere **Soluzioni e cartelle**.

      ![La notifica "Soluzioni e cartelle" da Team Explorer in Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Un file di soluzione (con estensione sln) verrà visualizzato nel menu a comparsa "Soluzioni e cartelle". Selezionarlo e Visual Studio aprirà la soluzione.

   Se nel repository non è disponibile un file di soluzione, il menu a comparsa indicherà che "Non sono state trovate soluzioni". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

## <a name="next-steps"></a>Passaggi successivi

Se si è pronti a creare codice con Visual Studio 2017, approfondire una delle esercitazioni seguenti specifiche del linguaggio:

- [Visual Studio esercitazioni | **C#**](./csharp/index.yml)
- [Esercitazioni di Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Esercitazioni di Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Esercitazioni di Visual Studio | **Python**](../python/index.yml)
- [Esercitazioni di Visual Studio | **JavaScript**, **TypeScript** e **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Vedi anche

- [Aprire un progetto da un Visual Studio 2019](tutorial-open-project-from-repo-visual-studio-2019.md)
- [Nuova esperienza Git in Visual Studio 2019](../ide/git-with-visual-studio.md)
- [Azure DevOps Services: Introduzione a Azure Repos e Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Introduzione a Azure DevOps](/learn/modules/get-started-with-devops/)
