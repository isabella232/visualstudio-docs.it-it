---
title: Connettersi a progetti in Team Explorer
description: Informazioni su come usare Team Explorer in Visual Studio per collaborare con i membri del team per sviluppare e gestire i progetti.
ms.custom: SEO-VS-2020
ms.date: 03/31/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 78a71911bb4334e04a085d91ff51238d34981beb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216605"
---
# <a name="connect-to-projects-in-team-explorer"></a>Connettersi a progetti in Team Explorer

::: moniker range="vs-2017"

Usare le finestra degli strumenti di **Team Explorer** per coordinare le attività relative al codice con altri membri del team per sviluppare un progetto e gestire il lavoro assegnato all'utente, al team o ai progetti. **Team Explorer** connette Visual Studio ai repository GIT e GitHub, ai repository del controllo della versione di Team Foundation e ai progetti ospitati su [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) o su un'istanza di [Azure DevOps Server](/azure/devops/index-all) (precedentemente denominato TFS). È possibile gestire codice sorgente, elementi di lavoro e compilazioni.

::: moniker-end

::: moniker range="vs-2019"

Team Explorer connette Visual Studio ai repository del controllo della versione di Team Foundation (TFVC) e ai progetti ospitati in [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) o in un [Azure DevOps server](/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops&preserve-view=true) locale (precedentemente noto come TFS). È possibile gestire codice sorgente, elementi di lavoro e compilazioni.

> [!IMPORTANT]
> Con la versione recente di Visual Studio 2019 [**versione 16,8**](/visualstudio/releases/2019/release-notes/), la nuova esperienza di controllo della versione di Git è ora attiva per impostazione predefinita. Per ulteriori informazioni sul confronto con Team Explorer, vedere il [**confronto affiancato tra git e la pagina di Team Explorer**](git-team-explorer-feature-comparison.md) .
>
> Tuttavia, se si preferisce continuare a usare Team Explorer, passare a **strumenti** > **Opzioni** > **ambiente** > **Anteprima funzionalità** e quindi selezionare la casella di controllo **nuova esperienza utente git** .

Il modo in cui si usa Team Explorer per connettersi a un progetto dipende dalla versione di Visual Studio 2019 che si sta usando.

## <a name="in-version-168-and-later"></a>Nella versione 16,8 e successive

1. Aprire Visual Studio 2019.

1. Nella finestra di avvio selezionare **clona un repository**.

   ![Screenshot della finestra di dialogo Clona un repository in Visual Studio 2019 versione 16,8 e successive per Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. Nella sezione **sfogliare un repository** selezionare **Azure DevOps**.

    ![Screenshot della sezione ' Sfoglia un repository ' della finestra di dialogo ' Connetti a un progetto ' in Visual Studio 2019 versione 16,8 e versioni successive](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Se viene visualizzata una finestra di accesso, accedere al proprio account.

1. Nella finestra di dialogo **Connetti a un progetto** scegliere il repository a cui si desidera connettersi e quindi selezionare **clona**.

      ![Screenshot della finestra di dialogo ' Connetti a un progetto ' generata da Visual Studio 2019 versione 16,8 e successive](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Se non viene visualizzato un elenco pre-popolato di repository a cui connettersi, selezionare **aggiungi Azure DevOps server** per immettere un URL server. In alternativa, è possibile che venga visualizzato il messaggio "non sono stati trovati server" che include collegamenti per aggiungere un Azure DevOps Server esistente o creare un account Azure DevOps.)

   Visual Studio apre quindi **Esplora soluzioni** che mostra le cartelle e i file.

1. Selezionare la scheda **Team Explorer** per visualizzare le azioni di Azure DevOps.

      ![Screenshot della finestra di dialogo ' Team Explorer ' generata da Visual Studio 2019 versione 16,8 e successive](../ide/media/vs-2019/team-explorer-azure-devops.png)

## <a name="in-version-167-and-earlier"></a>Nella versione 16,7 e versioni precedenti

1. Aprire Visual Studio 2019.

1. Nella finestra Start selezionare **clona o Estrai codice**.

   ![Screenshot della finestra ' Crea nuovo progetto ' in Visual Studio 2019 versione 16,7 e precedenti](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Nella sezione **sfogliare un repository** selezionare **Azure DevOps**.

   ![Screenshot della finestra ' clona o Estrai codice ' con la sezione ' Sfoglia un repository ' che elenca Azure DevOps in Visual Studio 2019 versione 16,7 e precedenti](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Se viene visualizzata una finestra di accesso, accedere al proprio account.

1. Nella finestra di dialogo **Connetti a un progetto** scegliere il repository a cui si desidera connettersi e quindi selezionare **clona**.

      ![Screenshot della finestra di dialogo ' Connetti a un progetto ' generata da Visual Studio 2019 versione 16,7 e precedenti](../get-started/media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ciò che compare nella casella di riepilogo dipende dai repository Azure DevOps ai quali si ha accesso.

   Visual Studio apre **Team Explorer** e viene visualizzata una notifica quando il clone è stato completato.

     ![Screenshot della finestra di Team Explorer in Visual Studio 2019 versione 16,7 e precedenti, dopo il completamento del clone](../get-started/media/vs-2019/clone-complete-azure-devops.png)

1. Per visualizzare le cartelle e i file, selezionare il collegamento **Mostra visualizzazione cartelle** .

     ![Screenshot della sezione Solutions della finestra di Team Explorer in Visual Studio 2019 versione 16,7 e precedenti, dopo il completamento del clone](../get-started/media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio apre **Esplora soluzioni**.

1. Scegliere il collegamento **soluzioni e cartelle** per cercare un file di soluzione (in particolare un file con estensione sln) da aprire.

      ![Screenshot della notifica di "soluzioni e cartelle" da Team Explorer in Visual Studio 2019 versione 16,7 e precedenti](../get-started/media/open-proj-repo-solutions-folders.png)

   Se nel repository non è presente un file di soluzione, viene visualizzato il messaggio "nessuna soluzione trovata". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

::: moniker-end

::: moniker range="vs-2017"

![Pagina Home di Team Explorer in Visual Studio](media/team-explorer/team-explorer.png "La Home page di Team Explorer in Visual Studio.")

> [!TIP]
> Se si apre Visual Studio e **Team Explorer** non viene visualizzato, aprirlo scegliendo **Visualizza**  >  **Team Explorer** dalla barra dei menu o premendo **CTRL** + **&#92;**, **CTRL** + **M**.

## <a name="connect-to-a-project-or-repository"></a>Connettersi a un progetto o a un repository

Connettersi a un progetto o a un repository nella pagina **Connessione**.

![Pagina Connessione di Team Explorer](media/team-explorer/connect.png "Pagina Team Explorer-Connect in Visual Studio")

Per connettersi a un progetto:

1. Aprire la pagina **Connessione** scegliendo l'icona **Gestione connessioni**.

   ![Pulsante Gestione connessioni in Team Explorer](media/team-explorer/manage-connections.png "Pulsante Team Explorer-Manage Connections in Visual Studio.")

1. Nella pagina **Connessione** scegliere **Gestisci connessioni** > **Connetti a un progetto**.

   ![Connettersi a un progetto in Team Explorer](media/team-explorer/connect-project.png "L'opzione Team Explorer-Connetti a un progetto in Visual Studio.")

> [!TIP]
> Se si vuole aprire un progetto da un repository, vedere [aprire un progetto da un repository](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md). Se si vuole creare un nuovo progetto o aggiungere utenti a un progetto, vedere [creare un progetto (Azure DevOps)](/azure/devops/organizations/projects/create-project) e [aggiungere utenti a un progetto o a un team (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Confrontare git e Team Explorer side-by-side](git-team-explorer-feature-comparison.md)
- [Nuova esperienza git in Visual Studio](git-with-visual-studio.md)
- [Informazioni di riferimento su Team Explorer](reference/team-explorer-reference.md)
- [Connect to a project (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects) (Connettersi a un progetto (Azure DevOps))
- [Risolvere i problemi di connessione a un progetto](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
