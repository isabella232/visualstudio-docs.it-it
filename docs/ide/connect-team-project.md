---
title: Connettersi a progetti in Team Explorer
description: Informazioni su come usare Team Explorer in Visual Studio collaborare con i membri del team per sviluppare e gestire progetti.
ms.custom: SEO-VS-2020
ms.date: 06/11/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jmartens
monikerRange: <=vs-2019
ms.openlocfilehash: fd95da37fc0f6dcf5d7c735bc1e8b1afe050b9f8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628835"
---
# <a name="connect-to-projects-in-team-explorer"></a>Connettersi a progetti in Team Explorer

::: moniker range="vs-2017"

Usare le finestra degli strumenti di **Team Explorer** per coordinare le attività relative al codice con altri membri del team per sviluppare un progetto e gestire il lavoro assegnato all'utente, al team o ai progetti. **Team Explorer** connette Visual Studio ai repository GIT e GitHub, ai repository del controllo della versione di Team Foundation e ai progetti ospitati su [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) o su un'istanza di [Azure DevOps Server](/azure/devops/index-all) (precedentemente denominato TFS). È possibile gestire codice sorgente, elementi di lavoro e compilazioni.

::: moniker-end

::: moniker range="vs-2019"

Team Explorer connette Visual Studio ai repository del controllo della versione di Team Foundation (TFVC) e ai progetti ospitati [in Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) o in un [Azure DevOps Server locale](/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops&preserve-view=true) (precedentemente noto come TFS). È possibile gestire codice sorgente, elementi di lavoro e compilazioni.

> [!IMPORTANT]
> Con il rilascio di Visual Studio 2019 [**versione 16.8,**](/visualstudio/releases/2019/release-notes-history)l'esperienza di controllo della versione di Git è disponibile per impostazione predefinita. Per altre informazioni sul confronto con Team Explorer, vedere la pagina Confronto [**side-by-side**](../version-control/git-team-explorer-feature-comparison.md) tra Git e Team Explorer.
>
> Tuttavia, se si preferisce continuare a usare Team Explorer, passare a Strumenti Opzioni Funzionalità di anteprima dell'ambiente e quindi attivare o disattivare la casella di controllo Nuova esperienza utente  >  >  >  **Git.**

La modalità Team Explorer per connettersi a un progetto dipende dalla versione di Visual Studio 2019 in uso.

## <a name="in-version-168-and-later"></a>Nella versione 16.8 e successive

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale selezionare **Clona un repository**.

   ![Screenshot della finestra di dialogo Clona un repository in Visual Studio 2019 versione 16.8 e successive, per Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. Nella sezione **Sfoglia un repository** selezionare Azure DevOps . 

    ![Screenshot della sezione "Sfoglia un repository" della finestra di dialogo "Da Connessione a un Project" in Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Se viene visualizzata una finestra di accesso, accedere al proprio account.

1. Nella finestra **Connessione a un Project** scegliere il repo a cui connettersi e quindi selezionare **Clona**.

      ![Screenshot della finestra di dialogo "Connessione a Project" generata da Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Se non viene visualizzato un elenco precompilato di repository a cui connettersi, selezionare **Aggiungi** Azure DevOps Server per immettere un URL del server. In alternativa, potrebbe essere visualizzato un prompt "Nessun server trovato" che include collegamenti per aggiungere un Azure DevOps Server esistente o per creare un account Azure DevOps locale.

   Successivamente, Visual Studio apre **Esplora soluzioni** che mostra le cartelle e i file.

1. Selezionare la **Team Explorer** per visualizzare le Azure DevOps azioni.

      ![Screenshot della finestra di dialogo "Team Explorer" generata da Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/team-explorer-azure-devops.png)

## <a name="in-version-167-and-earlier"></a>Nella versione 16.7 e precedenti

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale selezionare **Clona o estrai codice**.

   ![Screenshot della finestra "Crea un nuovo progetto" in Visual Studio 2019 versione 16.7 e precedenti](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Nella sezione **Sfoglia un repository** selezionare Azure DevOps . 

   ![Screenshot della finestra "Clona o estrai codice" con la sezione "Sfoglia un repository" che elenca Azure DevOps in Visual Studio 2019 versione 16.7 e precedenti](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Se viene visualizzata una finestra di accesso, accedere al proprio account.

1. Nella finestra **Connessione a un Project** scegliere il repo a cui connettersi e quindi selezionare **Clona**.

      ![Screenshot della finestra di dialogo "Connessione a Project" generata da Visual Studio 2019 versione 16.7 e precedenti](../get-started/media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ciò che compare nella casella di riepilogo dipende dai repository Azure DevOps ai quali si ha accesso.

   Visual Studio apre **Team Explorer** e viene visualizzata una notifica quando il clone è stato completato.

     ![Screenshot della finestra Team Explorer in Visual Studio 2019 versione 16.7 e precedenti, dopo il completamento del clone](../get-started/media/vs-2019/clone-complete-azure-devops.png)

1. Per visualizzare le cartelle e i file, selezionare il **collegamento Mostra visualizzazione** cartelle.

     ![Screenshot della sezione Soluzioni della finestra Team Explorer in Visual Studio 2019 versione 16.7 e precedenti, al termine della clonazione](../get-started/media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio apre **Esplora soluzioni**.

1. Scegliere il **collegamento Soluzioni e cartelle** per cercare un file di soluzione (in particolare un file con estensione sln) da aprire.

      ![Screenshot della notifica "Soluzioni e cartelle" Team Explorer in Visual Studio 2019 versione 16.7 e precedenti](../get-started/media/open-proj-repo-solutions-folders.png)

   Se nel repo non è presente un file di soluzione, viene visualizzato il messaggio "Nessuna soluzione trovata&quot;. Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

::: moniker-end

::: moniker range=&quot;vs-2017&quot;

![Pagina Home di Team Explorer in Visual Studio](media/team-explorer/team-explorer.png &quot;La Team Explorer - Home page in Visual Studio.")

> [!TIP]
> Se si apre Visual Studio e **Team Explorer** non viene visualizzato, aprirlo scegliendo Visualizza Team Explorer dalla barra dei menu o premendo  >   **CTRL** + **&#92;**, **CTRL** + **M**.

## <a name="connect-to-a-project-or-repository"></a>Connettersi a un progetto o a un repository

Connettersi a un progetto o a un repository nella pagina **Connessione**.

![Pagina Connessione di Team Explorer](media/team-explorer/connect.png "Pagina Team Explorer - Connessione in Visual Studio")

Per connettersi a un progetto:

1. Aprire la pagina **Connessione** scegliendo l'icona **Gestione connessioni**.

   ![Pulsante Gestione connessioni in Team Explorer](media/team-explorer/manage-connections.png "Pulsante Team Explorer - Gestisci connessioni in Visual Studio.")

1. Nella pagina **Connessione** scegliere **Gestisci** connessioni Connessione a > **un progetto**.

   ![Connettersi a un progetto in Team Explorer](media/team-explorer/connect-project.png "L Team Explorer- Connessione a un'Project in Visual Studio.")

> [!TIP]
> Per aprire un progetto da un repo, vedere [Aprire un progetto da un repo.](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md) Per creare un nuovo progetto o aggiungere utenti a un progetto, vedere Creare un progetto [(Azure DevOps)](/azure/devops/organizations/projects/create-project) e Aggiungere utenti a un progetto o a un [team (Azure DevOps).](/azure/devops/organizations/security/add-users-team-project)

::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Confrontare Git e Team Explorer side-by-side](git-team-explorer-feature-comparison.md)
- [La nuova esperienza Git in Visual Studio](git-with-visual-studio.md)
- [Informazioni di riferimento su Team Explorer](reference/team-explorer-reference.md)
- [Connect to a project (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects) (Connettersi a un progetto (Azure DevOps))
- [Risolvere i problemi di connessione a un progetto](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
