---
title: Connettersi a progetti in Team Explorer
description: Informazioni su come usare Team Explorer in Visual Studio per collaborare con i membri del team per sviluppare e gestire i progetti.
ms.date: 11/17/2020
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 4e4fdfb26c601ce6b706c1c946ea9afe9b18ecb2
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850091"
---
# <a name="connect-to-projects-in-team-explorer"></a>Connettersi a progetti in Team Explorer

::: moniker range="vs-2017"

Usare le finestra degli strumenti di **Team Explorer** per coordinare le attività relative al codice con altri membri del team per sviluppare un progetto e gestire il lavoro assegnato all'utente, al team o ai progetti. **Team Explorer** connette Visual Studio ai repository GIT e GitHub, ai repository del controllo della versione di Team Foundation e ai progetti ospitati su [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) o su un'istanza di [Azure DevOps Server](/azure/devops/index-all) (precedentemente denominato TFS). È possibile gestire codice sorgente, elementi di lavoro e compilazioni.

::: moniker-end

::: moniker range="vs-2019"

È possibile utilizzare la finestra degli strumenti **Team Explorer** per coordinare le attività di codice con altri membri del team per sviluppare un progetto e per gestire il lavoro assegnato all'utente, al team o ai progetti.

> [!IMPORTANT]
> Con la versione recente di Visual Studio 2019 [versione 16,8](/visualstudio/releases/2019/release-notes/), la nuova esperienza di controllo della versione di Git è ora attiva per impostazione predefinita. Tuttavia, se si preferisce continuare a usare Team Explorer, passare a **strumenti**  >  **Opzioni**  >  **ambiente**  >  **Anteprima funzionalità** e quindi selezionare la casella di controllo **nuova esperienza utente git** . Per altre informazioni, vedere la pagina relativa all' [esperienza git in Visual Studio](git-with-visual-studio.md) .

**Team Explorer** connette Visual Studio ai repository GIT e GitHub, ai repository del controllo della versione di Team Foundation e ai progetti ospitati su [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) o su un'istanza di [Azure DevOps Server](/azure/devops/index-all) (precedentemente denominato TFS). È possibile gestire codice sorgente, elementi di lavoro e compilazioni.

::: moniker-end

![Pagina Home di Team Explorer in Visual Studio](media/team-explorer/team-explorer.png)

::: moniker range="vs-2017"

> [!TIP]
> Se si apre Visual Studio e **Team Explorer** non viene visualizzato, aprirlo scegliendo **Visualizza**  >  **Team Explorer** dalla barra dei menu o premendo **CTRL** + **&#92;**, **CTRL** + **M**.

::: moniker-end

## <a name="connect-to-a-project-or-repository"></a>Connettersi a un progetto o a un repository

Connettersi a un progetto o a un repository nella pagina **Connessione**.

![Pagina Connessione di Team Explorer](media/team-explorer/connect.png)

Per connettersi a un progetto:

1. Aprire la pagina **Connessione** scegliendo l'icona **Gestione connessioni**.

   ![Pulsante Gestione connessioni in Team Explorer](media/team-explorer/manage-connections.png)

1. Nella pagina **Connessione** scegliere **Gestisci connessioni** > **Connetti a un progetto**.

   ![Connettersi a un progetto in Team Explorer](media/team-explorer/connect-project.png)

> [!TIP]
> Se si vuole aprire un progetto da un repository, vedere [aprire un progetto da un repository](../get-started/tutorial-open-project-from-repo.md). Se si vuole creare un nuovo progetto o aggiungere utenti a un progetto, vedere [creare un progetto (Azure DevOps)](/azure/devops/organizations/projects/create-project) e [aggiungere utenti a un progetto o a un team (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

## <a name="see-also"></a>Vedere anche

- [Nuova esperienza git in Visual Studio](git-with-visual-studio.md)
- [Esercitazione: aprire un progetto da un repository](../get-started/tutorial-open-project-from-repo.md)
- [Informazioni di riferimento su Team Explorer](reference/team-explorer-reference.md)
- [Connect to a project (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects) (Connettersi a un progetto (Azure DevOps))
- [Risolvere i problemi di connessione a un progetto](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
