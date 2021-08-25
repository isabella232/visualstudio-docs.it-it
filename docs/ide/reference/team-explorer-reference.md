---
title: Informazioni di riferimento su Team Explorer
description: Informazioni sulle varie funzioni in Team Explorer gestire il lavoro e coordinarsi con altri membri del team per sviluppare un progetto.
ms.custom: SEO-VS-2020
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jmartens
ms.openlocfilehash: 85d007ae7aec5bb56b85e4b1861845f81687dd68
ms.sourcegitcommit: aef3e3f99e022675d339b7fe381cb37202be5be2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2021
ms.locfileid: "122785871"
---
# <a name="team-explorer-reference"></a>Informazioni di riferimento su Team Explorer

Questo articolo contiene collegamenti ad articoli di Azure DevOps sulle varie funzioni disponibili in **Team Explorer**.

Usare le finestra degli strumenti di **Team Explorer** per coordinare le attività relative al codice con altri membri del team per sviluppare un progetto e gestire il lavoro assegnato all'utente, al team o ai progetti. **Team Explorer** connette Visual Studio ai repository GIT e GitHub, ai repository del controllo della versione di Team Foundation e ai progetti ospitati su [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) o su un'istanza di [Azure DevOps Server](/azure/devops/index-all) (precedentemente denominato TFS). È possibile gestire codice sorgente, elementi di lavoro e compilazioni.

## <a name="home-page"></a>Home page

Dopo essersi [connessi a un progetto](../connect-team-project.md) in **Team Explorer**, nella sezione **Progetto** vengono visualizzati i collegamenti seguenti:

- [Clona repository](/azure/devops/repos/git/clone)
- [Portale Web](/azure/devops/project/navigation/index)
- [Lavagna delle attività](/azure/devops/boards/sprints/task-board)

La page **Home** offre diverse funzioni a seconda che ci si sia connessi a un repository [GIT](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio&preserve-view=true) o un repository del [controllo della versione di Team Foundation](/azure/devops/repos/tfvc/overview).

> [!TIP]
> Per un confronto tra i due sistemi di controllo delle versioni, vedere [Choose the right version control for your project (Azure DevOps)](/azure/devops/repos/tfvc/comparison-git-tfvc) (Scegliere il controllo della versione corretto per il progetto (Azure DevOps)).

| Pagina **Home** con GIT | Pagina **Home** con il controllo della versione di Team Foundation |
| - | - |
| ![Pagina Home di Team Explorer con GIT in Visual Studio 2019](media/team-explorer-reference/team-explorer-git.png) | ![Pagina Home di Team Explorer con il controllo della versione di Team Foundation in Visual Studio](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Pagina Modifiche (GIT)

Vedere, [Save work with commits](/azure/devops/repos/git/commits) (Salvare il lavoro con i commit).

## <a name="branches-page-git"></a>Pagina Rami (GIT)

Vedere [Create work in branches](/azure/devops/repos/git/branches) (Suddividere il lavoro in rami).

## <a name="pull-requests-page-git"></a>Pagina Richieste pull (GIT)

Vedere [Review code with pull requests](/azure/devops/repos/git/pullrequest) (Rivedere il codice con richieste pull).

## <a name="sync-page-git"></a>Pagina Sincronizzazione (GIT)

Vedere [Update code with fetch and pull](/azure/devops/repos/git/pulling) (Aggiornare il codice con fetch e pull).

## <a name="tags-page-git"></a>Pagina Tag (GIT)

Vedere [Work with Git tags](/azure/devops/repos/git/git-tags) (Usare tag GIT).

## <a name="my-work-page-tfvc"></a>Pagina Lavoro (controllo della versione di Team Foundation)

Vedere [Suspend/resume work](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) (Sospendere/riprendere il lavoro) [Code review](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review) (Revisione del codice).

## <a name="pending-changes-page-tfvc"></a>Pagina Modifiche in sospeso (controllo della versione di Team Foundation)

Vedere [Manage pending changes](/azure/devops/repos/tfvc/develop-code-manage-pending-changes) (Gestire le modifiche in sospeso), [Find shelvesets](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) (Trovare i shelveset) e [Resolve conflicts](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts) (Risolvere i conflitti).

## <a name="source-control-explorer-page-tfvc"></a>Pagina Esplora controllo codice sorgente (controllo della versione di Team Foundation)

Vedere [Add/view files and folders](/azure/devops/repos/tfvc/add-files-server) (Aggiungere/visualizzare file e cartelle).

## <a name="work-items-page"></a>Pagina Elementi di lavoro

Nella pagina **Elemento di lavoro** è possibile visualizzare le query degli [elementi di lavoro](/azure/devops/boards/work-items/about-work-items). Vedere:

- [Add work items](/azure/devops/boards/backlogs/add-work-items) (Aggiungere elementi di lavoro)
- [Use the query editor to list and manage queries](/azure/devops/boards/queries/using-queries) (Usare l'editor di query per elencare e gestire le query)
- [Organize query folders and set query permissions](/azure/devops/boards/queries/set-query-permissions) (Organizzare cartelle query e impostare autorizzazioni di query)
- [Open query in Excel](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel) (Aprire la query in Excel).
- [Open query in Project](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project) (Aprire la query in Project).
- [Email query results list using Outlook](/azure/devops/boards/queries/share-plans) (Elencare i risultati di query di posta elettronica usando Outlook)
- [Create reports from query in Excel](/azure/devops/report/excel/create-status-and-trend-excel-reports) (Creare report da query in Excel) (solo TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> In Visual Studio 2019 è disponibile una nuova [esperienza di Elementi di lavoro](/azure/devops/boards/work-items/set-work-item-experience-vs). Per informazioni sulla visualizzazione degli elementi di lavoro in Visual Studio 2019, vedere [View and add work items](/azure/devops/boards/work-items/view-add-work-items) (Visualizzare e aggiungere elementi di lavoro).

::: moniker-end

## <a name="builds-page"></a>Pagina Compilazioni

La pagina **Compilazioni** consente di visualizzare le definizioni di compilazione per il progetto.

Vedere:

- [Create build pipelines](/azure/devops/pipelines/tasks/index) (Creare pipeline di compilazione)
- [View and manage builds](/azure/devops/pipelines/overview) (Visualizzare e gestire le compilazioni)
- [Manage the build queue](/azure/devops/pipelines/agents/pools-queues) (Gestire la coda di compilazione)
- [Install continuous delivery (CD) tools for Visual Studio](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017) (Installare strumenti di recapito continuo per Visual Studio)
- [Configure and execute continuous delivery (CD) for your app](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app) (Configurare ed eseguire il recapito continuo per l'app)

## <a name="settings-page"></a>Pagina Impostazioni

La pagina **Impostazioni** consente di configurare le funzionalità amministrative per un progetto o una raccolta di progetti. Vedere gli articoli seguenti:

| Project | Raccolta di progetti | Altri |
| - | - | - |
| [Sicurezza, Appartenenza a gruppo](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Sicurezza, Controllo del codice sorgente (controllo della versione di Team Foundation)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[Aree elementi di lavoro](/azure/devops/organizations/settings/set-area-paths)<br/>[Iterazioni elementi di lavoro](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Impostazioni del portale](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Avvisi di progetto](/azure/devops/notifications/howto-manage-team-notifications) | [Sicurezza, Appartenenza a gruppo](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Controllo del codice sorgente (controllo della versione di Team Foundation)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[Gestione modelli di processo](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Impostazioni globali GIT](/azure/devops/repos/git/git-config)<br/>[Impostazioni del repository GIT](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Vedi anche

- [Connettersi a progetti in Team Explorer](../../ide/connect-team-project.md)