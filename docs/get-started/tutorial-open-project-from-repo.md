---
title: 'Esercitazione: Aprire un progetto da un repository'
description: Informazioni su come aprire un progetto in un repository Git o Azure DevOps con Visual Studio.
ms.custom: get-started
ms.date: 03/30/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3af54d663cee1ad2b2dd4e8241678b88c635d376
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180434"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Esercitazione: Aprire un progetto da un repository

In questa esercitazione si userà Visual Studio per connettersi a un repository per la prima volta e quindi aprire un progetto dal repository.

::: moniker range="vs-2017"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Aprire un progetto da un repository GitHub

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

1. Nella barra dei menu superiore scegliere **File**> **Apri** >**Apri dal controllo del codice sorgente**.

   Si apre il riquadro **Team Explorer - Connetti**.

    ![Finestra Team Explorer nell'IDE di Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Nella sezione **Repository Git locali** scegliere **Clone**.

    ![Scegliere Clona dalla sezione Repository Git locali](./media/open-proj-repo-local-git-repo-clone.png)

1. Nella casella ***Immetti l'URL di un repository Git da clonare***, digitare o incollare l'URL del repository e quindi premere **INVIO**. Se viene visualizzata la richiesta di accedere a GitHub, eseguire questa operazione.

   Quando Visual Studio ha clonato il repository, Team Explorer si chiude e si apre Esplora soluzioni. Viene visualizzato il messaggio *Fare clic sopra su "Soluzioni e cartelle" per visualizzare un elenco di soluzioni*. Scegliere **Soluzioni e cartelle**.

   ![Scegliere "Soluzioni e cartelle" in Esplora soluzioni](./media/open-proj-repo-github-solutions-folders.png)

1. Se si ha un file di soluzione disponibile, verrà visualizzato nel menu a comparsa "Soluzioni e cartelle". Selezionarlo e Visual Studio aprirà la soluzione.

   ![Scegliere cosa si vuole aprire nell'elenco a discesa Esplora soluzioni](./media/open-proj-repo-github-solutions-folders-picker.png)

   Se nel repository non è disponibile un file di soluzione (con estensione sln), il menu a comparsa indicherà che "Non sono state trovate soluzioni". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

### <a name="review-your-work"></a>Rivedere il lavoro

Visualizzare l'animazione seguente per verificare il lavoro completato nella sezione precedente.

   ![Animazione dell'apertura di un progetto in un repository GitHub con Visual Studio](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale scegliere **Clona o esegui checkout del codice**.

   ![Visualizzare la finestra Crea un nuovo progetto](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Immettere o digitare il percorso del repository e quindi scegliere **Clona**.

   ![Visualizzare la finestra Clona o esegui checkout del codice](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio apre il progetto dal repository.

1. Se si ha un file di soluzione disponibile, verrà visualizzato nel menu a comparsa "Soluzioni e cartelle". Selezionarlo e Visual Studio aprirà la soluzione.

   ![Scegliere cosa si vuole aprire nell'elenco a discesa Esplora soluzioni](./media/open-proj-repo-github-solutions-folders-picker.png)

   Se nel repository non è disponibile un file di soluzione (con estensione sln), il menu a comparsa indicherà che "Non sono state trovate soluzioni". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Aprire un progetto da un repository Azure DevOps

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

1. Nella barra dei menu superiore scegliere **File**> **Apri** >**Apri dal controllo del codice sorgente**.

   Si apre il riquadro **Team Explorer - Connetti**.

    ![Finestra Team Explorer nell'IDE di Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Esistono due modi per connettersi al repository Azure DevOps:

      - Nella sezione **Provider di servizi ospitati** scegliere **Connetti**.

        ![La sezione Provider di servizi ospitati della finestra Team Explorer nell'IDE di Visual Studio](./media/open-proj-repo-azure-devops.png)

      - Nell'elenco a discesa **Gestione connessioni** scegliere **Connetti a un progetto**.

        ![La sezione Gestione connessioni della finestra Team Explorer nell'IDE di Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Nella finestra di dialogo **Connetti a un progetto** scegliere il repository a cui connettersi e quindi scegliere **Clona**.

      ![La finestra di dialogo "Connetti a un progetto" generata da Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ciò che compare nella casella di riepilogo dipende dai repository Azure DevOps ai quali si ha accesso.

1. Quando Visual Studio ha clonato il repository, Team Explorer si chiude e si apre Esplora soluzioni. Viene visualizzato il messaggio *Fare clic sopra su "Soluzioni e cartelle" per visualizzare un elenco di soluzioni*. Scegliere **Soluzioni e cartelle**.

      ![La notifica "Soluzioni e cartelle" da Team Explorer in Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Un file di soluzione (con estensione sln) verrà visualizzato nel menu a comparsa "Soluzioni e cartelle". Selezionarlo e Visual Studio aprirà la soluzione.

   Se nel repository non è disponibile un file di soluzione, il menu a comparsa indicherà che "Non sono state trovate soluzioni". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale scegliere **Clona o esegui checkout del codice**.

   ![Visualizzare la finestra Crea un nuovo progetto](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Nella sezione **Sfoglia un repository** scegliere **Azure DevOps**.

   ![Visualizzare la finestra Clona o esegui checkout del codice](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Se viene visualizzata una finestra di accesso, accedere al proprio account.

1. Nella finestra di dialogo **Connetti a un progetto** scegliere il repository a cui connettersi e quindi scegliere **Clona**.

      ![La finestra di dialogo "Connetti a un progetto" generata da Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ciò che compare nella casella di riepilogo dipende dai repository Azure DevOps ai quali si ha accesso.

   Visual Studio apre **Team Explorer** e viene visualizzata una notifica quando il clone è stato completato.

     ![Finestra Team Explorer in Visual Studio dopo il completamento del clone](./media/vs-2019/clone-complete-azure-devops.png)

1. Per visualizzare le cartelle e i file, scegliere il collegamento **Mostra visualizzazione cartelle**.

     ![Sezione Soluzioni della finestra Team Explorer in Visual Studio dopo il completamento del clone](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio apre **Esplora soluzioni**.

1. Scegliere il collegamento **Soluzioni e cartelle** per cercare un file di soluzione (con estensione sln) da aprire.

      ![La notifica "Soluzioni e cartelle" da Team Explorer in Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Se nel repository non è disponibile un file di soluzione, verrà visualizzato il messaggio "Non sono state trovate soluzioni". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

Se è pronti a scrivere codice con Visual Studio, è possibile approfondire l'argomento in una delle esercitazioni specifiche per linguaggio seguenti:

- [Esercitazioni di Visual Studio | **C#** ](./csharp/index.yml)
- [Esercitazioni di Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Esercitazioni di Visual Studio | **C++** ](/cpp/get-started/tutorial-console-cpp)
- [Esercitazioni di Visual Studio | **Python**](/visualstudio/python/)
- [Esercitazioni di Visual Studio | **JavaScript**, **TypeScript** e **Node.js**](/visualstudio/javascript/)

## <a name="see-also"></a>Vedere anche

- [Azure DevOps Services: Get started with Azure Repos and Visual Studio](/azure/devops/repos/git/gitquickstart/) (Introduzione ad Azure Repos e Visual Studio)
- [Microsoft Learn: Introduzione ad Azure DevOps](/learn/modules/get-started-with-devops/)