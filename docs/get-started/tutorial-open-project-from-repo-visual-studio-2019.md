---
title: 'Esercitazione: Aprire un progetto da un repo in Visual Studio 2019'
description: Informazioni su come aprire un progetto in un repository Git o Azure DevOps usando Visual Studio 2019.
ms.custom: vs-acquisition, get-started
ms.date: 03/18/2021
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
monikerRange: vs-2019
ms.openlocfilehash: b6f7cd57a1753ca5926ac73a9bb4c8c918d1bd10
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389943"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Esercitazione: Aprire un progetto da un repo

In questa esercitazione si userà Visual Studio per connettersi a un repository per la prima volta e quindi aprire un progetto dal repository.

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

## <a name="open-a-project-from-a-github-repo"></a>Aprire un progetto da un repository GitHub

La modalità di apertura di un progetto da un repository GitHub Visual Studio 2019 dipende dalla versione disponibile. In particolare, se è stata installata la versione [**16.8**](/visualstudio/releases/2019/release-notes/) o successiva, è disponibile una nuova esperienza [Git](../ide/git-with-visual-studio.md) Visual Studio completamente integrata.

Tuttavia, indipendentemente dalla versione installata, è sempre possibile aprire un progetto da un repository GitHub con Visual Studio.

#### <a name="168-and-later"></a>[16.8 e versioni successive](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Clonare un repository GitHub e quindi aprire un progetto

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale selezionare **Clona un repository**.

   ![Screenshot della finestra di dialogo Clona un repository in Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/clone-repository.png)

1. Immettere o digitare il percorso del repository e quindi selezionare **Clona**.

   ![Screenshot della finestra di dialogo Clona un repository in cui si immette un URL del repository Git in Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/clone-repository-enter-location.png)

1. È possibile che venga richiesto di immettere le informazioni di accesso utente nella finestra di dialogo **Informazioni utente** Git. È possibile aggiungere le informazioni o modificare le informazioni predefinite fornite.

   ![Screenshot della finestra di dialogo Informazioni utente Git in cui si immettono o si modificano le informazioni dell'account in Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/git-user-information-dialog.png)

    Selezionare **Salva** per aggiungere le informazioni al file .gitconfig globale. In caso contrario, è possibile scegliere di eseguire questa operazione in un secondo momento selezionando **Annulla.**

    > [!TIP]
    > Per altre informazioni sull'accesso a Visual Studio, vedere la pagina Accedi a [Visual Studio.](../ide/signing-in-to-visual-studio.md) Per informazioni specifiche su come usare l'account GitHub per l'accesso, vedere la pagina Usare gli account [GitHub in](../ide/work-with-github-accounts.md) Visual Studio.

    Successivamente, Visual Studio carica e apre automaticamente la soluzione dal repository.

   ![Screenshot di un progetto in Git aperto in Esplora soluzioni in Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/git-solution-explorer.png )

1. Se il repository contiene più soluzioni, verranno visualizzati in Esplora soluzioni. È possibile visualizzare l'elenco delle soluzioni selezionando il **pulsante Cambia** visualizzazioni in Esplora soluzioni.

   ![Screenshot di un progetto in Git aperto in Esplora soluzioni, con il pulsante Cambia visualizzazioni evidenziato in Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Esplora soluzioni quindi consente di aprire la cartella radice in **Visualizzazione** cartelle o di selezionare un file di soluzione da aprire.

   ![Screenshot del file sln in Git aperto in Esplora soluzioni, dopo aver selezionato il pulsante Cambia visualizzazioni in Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Per attivare o disattivare la visualizzazione, selezionare **di nuovo il pulsante** Cambia visualizzazioni.

    > [!TIP]
    > È anche possibile usare il menu **Git** nell'IDE Visual Studio per clonare un repository e aprire un progetto.
    >
    > ![Screenshot del menu Git in Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Aprire un progetto in locale da un repository GitHub clonato in precedenza

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale selezionare Apri **un progetto o una soluzione.**

    Visual Studio apre un'istanza di Esplora file, in cui è possibile passare alla soluzione o al progetto e quindi selezionarla per aprirla.

   ![Screenshot della finestra "Apri un progetto o una soluzione" in Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Se il progetto o la soluzione è stata aperta di recente, selezionarla **nella** sezione Apri recente per aprirla di nuovo rapidamente.

    > [!TIP]
    > È anche possibile usare il menu **Git** nell'IDE Visual Studio per aprire cartelle e file locali da un repository clonato in precedenza.
    >
    > ![Screenshot del menu Git in Visual Studio 2019 versione 16.8 e successive, con l'opzione Repository locali espansa](../ide/media/vs-2019/git-menu-local-repositories.png)

    Iniziare a scrivere codice.

#### <a name="167-and-earlier"></a>[16.7 e versioni precedenti](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Clonare un repository GitHub e quindi aprire un progetto

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale selezionare **Clona o estrai codice**.

   ![Screenshot della finestra "Crea un nuovo progetto" in Visual Studio 2019 versione 16.7 e precedenti](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Immettere o digitare il percorso del repository e quindi selezionare **Clona**.

   ![Screenshot della finestra "Clona o estrai codice" in Visual Studio 2019 versione 16.7 e precedenti](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio apre il progetto dal repository.

1. Se si ha un file di soluzione disponibile, verrà visualizzato nel menu a comparsa "Soluzioni e cartelle". Selezionarlo e Visual Studio la soluzione.

   ![Screenshot dell'elenco Esplora soluzioni a discesa in Visual Studio 2019 versione 16.7 e precedenti](./media/open-proj-repo-github-solutions-folders-picker.png)

   Se nel repo non è presente un file di soluzione (in particolare un file sln), nel menu a comparsa viene visualizzato il messaggio "Nessuna soluzione trovata". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

    Iniziare a scrivere codice.

---

> [!NOTE]
> Per informazioni specifiche di Visual Studio 2017, vedere la pagina Aprire un progetto da un Visual Studio [2017.](tutorial-open-project-from-repo-visual-studio-2017.md)

## <a name="connect-to-an-azure-devops-server"></a>Connettersi a un Azure DevOps server

Ciò che viene visualizzato quando ci si connette a un server Azure DevOps usando Visual Studio 2019 dipende dalla versione disponibile. In particolare, se è stata installata la versione [**16.8**](/visualstudio/releases/2019/release-notes/) o successiva, l'interfaccia utente è stata modificata per supportare una nuova esperienza Git completamente integrata [in](../ide/git-with-visual-studio.md) Visual Studio in Visual Studio.

Tuttavia, indipendentemente dalla versione installata, è sempre possibile connettersi a un server Azure DevOps con Visual Studio.

#### <a name="168-and-later"></a>[16.8 e versioni successive](#tab/vs168later)

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale selezionare **Clona un repository**.

   ![Screenshot della finestra di dialogo Clona un repository in Visual Studio 2019 versione 16.8 e successive, per Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. Nella sezione **Sfoglia un repository** selezionare Azure DevOps . 

    ![Screenshot della sezione "Sfoglia un repository" della finestra di dialogo "Connetti a un progetto" in Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Se viene visualizzata una finestra di accesso, accedere al proprio account.

1. Nella finestra **di dialogo Connetti a un** progetto scegliere il repo a cui connettersi e quindi selezionare **Clona**.

      ![Screenshot della finestra di dialogo "Connetti a un progetto" generata da Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Se non viene visualizzato un elenco precompilato di repository a cui connettersi, selezionare **Aggiungi** Azure DevOps Server per immettere un URL del server. In alternativa, potrebbe essere visualizzato un prompt "Nessun server trovato" che include collegamenti per aggiungere un Azure DevOps Server esistente o per creare un account Azure DevOps locale.

   Successivamente, Visual Studio apre **Esplora soluzioni** che mostra le cartelle e i file.

1. Selezionare la **Team Explorer** per visualizzare le Azure DevOps azioni.

      ![Screenshot della finestra di dialogo "Team Explorer" generata da Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/team-explorer-azure-devops.png)

#### <a name="167-and-earlier"></a>[16.7 e versioni precedenti](#tab/vs167earlier)

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale selezionare **Clona o estrai codice**.

   ![Screenshot della finestra "Crea un nuovo progetto" in Visual Studio 2019 versione 16.7 e precedenti](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Nella sezione **Sfoglia un repository** selezionare Azure DevOps . 

   ![Screenshot della finestra "Clona o estrai codice" con la sezione "Sfoglia un repository" che elenca Azure DevOps in Visual Studio 2019 versione 16.7 e precedenti](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Se viene visualizzata una finestra di accesso, accedere al proprio account.

1. Nella finestra **di dialogo Connetti a un** progetto scegliere il repo a cui connettersi e quindi selezionare **Clona**.

      ![Screenshot della finestra di dialogo "Connetti a un progetto" generata da Visual Studio 2019 versione 16.7 e precedenti](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ciò che compare nella casella di riepilogo dipende dai repository Azure DevOps ai quali si ha accesso.

   Visual Studio apre **Team Explorer** e viene visualizzata una notifica quando il clone è stato completato.

     ![Screenshot della finestra Team Explorer in Visual Studio 2019 versione 16.7 e precedenti, dopo il completamento del clone](./media/vs-2019/clone-complete-azure-devops.png)

1. Per visualizzare le cartelle e i file, selezionare il **collegamento Mostra visualizzazione** cartelle.

     ![Screenshot della sezione Soluzioni della finestra Team Explorer in Visual Studio 2019 versione 16.7 e precedenti, dopo il completamento del clone](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio apre **Esplora soluzioni**.

1. Scegliere il **collegamento Soluzioni e cartelle** per cercare un file di soluzione (in particolare un file con estensione sln) da aprire.

      ![Screenshot della notifica "Soluzioni e cartelle" Team Explorer in Visual Studio 2019 versione 16.7 e precedenti](./media/open-proj-repo-solutions-folders.png)

   Se nel repo non è presente un file di soluzione, viene visualizzato il messaggio "Nessuna soluzione trovata". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

---

## <a name="next-steps"></a>Passaggi successivi

Se è pronti a scrivere codice con Visual Studio, è possibile approfondire l'argomento in una delle esercitazioni specifiche per linguaggio seguenti:

- [Visual Studio esercitazioni | **C#**](./csharp/index.yml)
- [Esercitazioni di Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Esercitazioni di Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Esercitazioni di Visual Studio | **Python**](../python/index.yml)
- [Esercitazioni di Visual Studio | **JavaScript**, **TypeScript** e **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Vedi anche

- [Aprire un progetto da un repo in Visual Studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md)
- [Nuova esperienza Git in Visual Studio 2019](../ide/git-with-visual-studio.md)
- [Confrontare Git e Team Explorer side-by-side](../ide/git-team-explorer-feature-comparison.md)
- [Azure DevOps Services: Introduzione a Azure Repos e Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Introduzione a Azure DevOps](/learn/modules/get-started-with-devops/)
