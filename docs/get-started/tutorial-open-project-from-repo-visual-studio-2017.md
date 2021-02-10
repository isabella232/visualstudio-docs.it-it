---
title: 'Esercitazione: aprire un progetto da un repository in Visual Studio 2017'
description: Informazioni su come aprire un progetto in un repository git o Azure DevOps con Visual Studio 2017.
ms.custom: get-started
ms.date: 01/25/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2017
ms.openlocfilehash: 97bfe7178d3bd744d1e441f8428cd38e8241b721
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951927"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>Esercitazione: aprire un progetto da un repository in Visual Studio 2017

In questa esercitazione si userà Visual Studio 2017 per connettersi a un repository per la prima volta e quindi si aprirà un progetto.

> [!TIP]
> Per la connessione a un repository GitHub in [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)è disponibile un nuovo metodo completamente integrato. Per ulteriori informazioni, vedere la pagina relativa alla [**nuova esperienza git in Visual Studio 2019**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true) .

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Aprire un progetto da un repository GitHub usando Visual Studio 2017

1. Aprire Visual Studio 2017.

1. Dalla barra dei menu superiore selezionare **file**  >  **Apri**  >  **Apri dal controllo del codice sorgente**.

   Si apre il riquadro **Team Explorer - Connetti**.

    ![Finestra Team Explorer nell'IDE di Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Nella sezione **repository git locali** selezionare **Clone**.

    ![Scegliere Clona dalla sezione Repository Git locali](./media/open-proj-repo-local-git-repo-clone.png)

1. Nella casella che indica ***immettere l'URL di un repository git da clonare** _, digitare o incollare l'URL per il repository, quindi premere _ * Enter * *. Se viene visualizzata la richiesta di accedere a GitHub, eseguire questa operazione.

   Quando Visual Studio ha clonato il repository, Team Explorer si chiude e si apre Esplora soluzioni. Viene visualizzato il messaggio *Fare clic sopra su "Soluzioni e cartelle" per visualizzare un elenco di soluzioni*. Scegliere **Soluzioni e cartelle**.

   ![Scegliere "Soluzioni e cartelle" in Esplora soluzioni](./media/open-proj-repo-github-solutions-folders.png)

1. Se si ha un file di soluzione disponibile, verrà visualizzato nel menu a comparsa "Soluzioni e cartelle". Selezionarlo e Visual Studio aprirà la soluzione.

   ![Scegliere cosa si vuole aprire nell'elenco a discesa Esplora soluzioni](./media/open-proj-repo-github-solutions-folders-picker.png)

   Se nel repository non è disponibile un file di soluzione (con estensione sln), il menu a comparsa indicherà che "Non sono state trovate soluzioni". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

### <a name="review-your-work"></a>Esaminare il lavoro

Visualizzare l'animazione seguente per verificare il lavoro completato nella sezione precedente.

   ![Animazione dell'apertura di un progetto in un repository GitHub con Visual Studio](./media/open-project-from-github.gif)

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Aprire un progetto da un repository DevOps di Azure usando Visual Studio 2017

1. Aprire Visual Studio 2017.

1. Dalla barra dei menu superiore selezionare **file**  >  **Apri**  >  **Apri dal controllo del codice sorgente**.

   Si apre il riquadro **Team Explorer - Connetti**.

    ![Finestra Team Explorer nell'IDE di Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Esistono due modi per connettersi al repository Azure DevOps:

      - Nella sezione **provider di servizi ospitati** selezionare **Connetti...**.

        ![La sezione Provider di servizi ospitati della finestra Team Explorer nell'IDE di Visual Studio](./media/open-proj-repo-azure-devops.png)

      - Nell'elenco a discesa **Gestisci connessioni** selezionare **Connetti a un progetto.**

        ![La sezione Gestione connessioni della finestra Team Explorer nell'IDE di Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Nella finestra di dialogo **Connetti a un progetto** scegliere il repository a cui si desidera connettersi e quindi selezionare **clona**.

      ![Finestra di dialogo ' Connetti a un progetto ' generata da Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ciò che compare nella casella di riepilogo dipende dai repository Azure DevOps ai quali si ha accesso.

1. Quando Visual Studio ha clonato il repository, Team Explorer si chiude e si apre Esplora soluzioni. Viene visualizzato il messaggio *Fare clic sopra su "Soluzioni e cartelle" per visualizzare un elenco di soluzioni*. Scegliere **Soluzioni e cartelle**.

      ![La notifica "Soluzioni e cartelle" da Team Explorer in Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Un file di soluzione (con estensione sln) verrà visualizzato nel menu a comparsa "Soluzioni e cartelle". Selezionarlo e Visual Studio aprirà la soluzione.

   Se nel repository non è disponibile un file di soluzione, il menu a comparsa indicherà che "Non sono state trovate soluzioni". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

## <a name="next-steps"></a>Passaggi successivi

Se si è pronti per il codice con Visual Studio 2017, esaminare le esercitazioni specifiche della lingua seguenti:

- [Esercitazioni su Visual Studio | **C#**](./csharp/index.yml)
- [Esercitazioni di Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Esercitazioni di Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Esercitazioni di Visual Studio | **Python**](../python/index.yml)
- [Esercitazioni di Visual Studio | **JavaScript**, **TypeScript** e **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Vedi anche

- [Azure DevOps Services: Introduzione a Azure Repos e Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: introduzione ad Azure DevOps](/learn/modules/get-started-with-devops/)
- [Nuova esperienza git in Visual Studio 2019](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true)
