---
title: 'Esercitazione: aprire un progetto da un repository in Visual Studio 2019'
description: Informazioni su come aprire un progetto in un repository git o Azure DevOps con Visual Studio 2019.
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
monikerRange: vs-2019
ms.openlocfilehash: b7197f9e21bb136f8444170dc8d62341b3b0c07d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886665"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Esercitazione: aprire un progetto da un repository

In questa esercitazione si userà Visual Studio per connettersi a un repository per la prima volta e quindi aprire un progetto dal repository.

Se Visual Studio non è ancora installato, passare alla pagina dei [download di Visual Studio](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

## <a name="open-a-project-from-a-github-repo"></a>Aprire un progetto da un repository GitHub

La modalità di apertura di un progetto da un repository GitHub con Visual Studio 2019 dipende dalla versione disponibile. In particolare, se è stata installata la versione [**16,8**](/visualstudio/releases/2019/release-notes/) o successiva, è disponibile un'esperienza git nuova e completamente integrata [in Visual Studio](../ide/git-with-visual-studio.md) .

Indipendentemente dalla versione installata, è sempre possibile aprire un progetto da un repository GitHub con Visual Studio.

#### <a name="168-and-later"></a>[16,8 e versioni successive](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Clonare un repository GitHub e quindi aprire un progetto

1. Aprire Visual Studio 2019.

1. Nella finestra di avvio selezionare **clona un repository**.

   ![Screenshot della finestra di dialogo Clona un repository in Visual Studio 2019 versione 16,8 e successive](../ide/media/vs-2019/clone-repository.png)

1. Immettere o digitare il percorso del repository, quindi selezionare **Clone**.

   ![Screenshot della finestra di dialogo Clona un repository in cui si immette l'URL di un repository git in Visual Studio 2019 versione 16,8 e successive](../ide/media/vs-2019/clone-repository-enter-location.png)

1. Nella finestra di dialogo **informazioni utente git** potrebbero essere richieste le informazioni di accesso utente. È possibile aggiungere o modificare le informazioni predefinite fornite.

   ![Screenshot della finestra di dialogo informazioni utente git in cui è possibile immettere o modificare le informazioni sull'account in Visual Studio 2019 versione 16,8 e successive](../ide/media/vs-2019/git-user-information-dialog.png)

    Selezionare **Save (Salva** ) per aggiungere le informazioni al file Global. gitconfig. (In alternativa, è possibile scegliere di eseguire questa operazione in un secondo momento selezionando **Annulla**).

    Successivamente, Visual Studio carica e apre automaticamente la soluzione dal repository.

   ![Screenshot di un progetto in git aperto in Esplora soluzioni in Visual Studio 2019 versione 16,8 e successive](../ide/media/vs-2019/git-solution-explorer.png )

1. Se il repository contiene più soluzioni, queste vengono visualizzate in Esplora soluzioni. È possibile visualizzare l'elenco delle soluzioni selezionando il pulsante **Cambia viste** in Esplora soluzioni.

   ![Screenshot di un progetto in git aperto in Esplora soluzioni, con il pulsante Cambia visualizzazioni evidenziato in Visual Studio 2019 versione 16,8 e successive](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Esplora soluzioni offre quindi la possibilità di aprire la cartella radice in **visualizzazione cartelle** o di selezionare un file di soluzione da aprire.

   ![Screenshot del file con estensione sln in git aperto in Esplora soluzioni, dopo aver selezionato il pulsante Cambia viste in Visual Studio 2019 versione 16,8 e successive](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Per attivare o disattivare la visualizzazione, selezionare di nuovo il pulsante **Cambia viste** .

    > [!TIP]
    > È anche possibile usare il menu **git** nell'IDE di Visual Studio per clonare un repository e aprire un progetto.
    >
    > ![Screenshot del menu git in Visual Studio 2019 versione 16,8 e successive](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Aprire un progetto localmente da un repository GitHub clonato in precedenza

1. Aprire Visual Studio 2019.

1. Nella finestra di avvio selezionare **Apri un progetto o una soluzione**.

    Visual Studio apre un'istanza di Esplora file, in cui è possibile passare alla soluzione o al progetto e quindi selezionarlo per aprirlo.

   ![Screenshot della finestra ' Apri progetto o soluzione ' in Visual Studio 2019 versione 16,8 e successive](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Se il progetto o la soluzione è stata aperta di recente, selezionarla dalla sezione **Apri recenti** per aprirla di nuovo rapidamente.

    > [!TIP]
    > È anche possibile usare il menu **git** nell'IDE di Visual Studio per aprire cartelle e file locali da un repository clonato in precedenza.
    >
    > ![Screenshot del menu git in Visual Studio 2019 versione 16,8 e successive, con l'opzione repository locali espansa](../ide/media/vs-2019/git-menu-local-repositories.png)


    Inizia a scrivere codice.

#### <a name="167-and-earlier"></a>[16,7 e versioni precedenti](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Clonare un repository GitHub e quindi aprire un progetto

1. Aprire Visual Studio 2019.

1. Nella finestra Start selezionare **clona o Estrai codice**.

   ![Screenshot della finestra ' Crea nuovo progetto ' in Visual Studio 2019 versione 16,7 e precedenti](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Immettere o digitare il percorso del repository, quindi selezionare **Clone**.

   ![Screenshot della finestra ' clona o codice di checkout ' in Visual Studio 2019 versione 16,7 e precedenti](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio apre il progetto dal repository.

1. Se si ha un file di soluzione disponibile, verrà visualizzato nel menu a comparsa "Soluzioni e cartelle". Selezionarlo e Visual Studio apre la soluzione.

   ![Screenshot dell'elenco a discesa Esplora soluzioni in Visual Studio 2019 versione 16,7 e precedenti](./media/open-proj-repo-github-solutions-folders-picker.png)

   Se nel repository non è presente un file di soluzione (in particolare un file con estensione sln), il menu di scelta rapida indica che non sono state trovate soluzioni. Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

    Inizia a scrivere codice.

---

## <a name="connect-to-an-azure-devops-server"></a>Connettersi a un server Azure DevOps

Ciò che viene visualizzato quando ci si connette a un server Azure DevOps con Visual Studio 2019 dipende dalla versione disponibile. In particolare, se è stata installata la versione [**16,8**](/visualstudio/releases/2019/release-notes/) o successiva, l'interfaccia utente è stata modificata in modo da supportare una nuova [esperienza git](../ide/git-with-visual-studio.md) completamente integrata in Visual Studio in Visual Studio.

Indipendentemente dalla versione installata, è sempre possibile connettersi a un server Azure DevOps con Visual Studio.

#### <a name="168-and-later"></a>[16,8 e versioni successive](#tab/vs168later)

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

#### <a name="167-and-earlier"></a>[16,7 e versioni precedenti](#tab/vs167earlier)

1. Aprire Visual Studio 2019.

1. Nella finestra Start selezionare **clona o Estrai codice**.

   ![Screenshot della finestra ' Crea nuovo progetto ' in Visual Studio 2019 versione 16,7 e precedenti](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Nella sezione **sfogliare un repository** selezionare **Azure DevOps**.

   ![Screenshot della finestra ' clona o Estrai codice ' con la sezione ' Sfoglia un repository ' che elenca Azure DevOps in Visual Studio 2019 versione 16,7 e precedenti](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Se viene visualizzata una finestra di accesso, accedere al proprio account.

1. Nella finestra di dialogo **Connetti a un progetto** scegliere il repository a cui si desidera connettersi e quindi selezionare **clona**.

      ![Screenshot della finestra di dialogo ' Connetti a un progetto ' generata da Visual Studio 2019 versione 16,7 e precedenti](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ciò che compare nella casella di riepilogo dipende dai repository Azure DevOps ai quali si ha accesso.

   Visual Studio apre **Team Explorer** e viene visualizzata una notifica quando il clone è stato completato.

     ![Screenshot della finestra di Team Explorer in Visual Studio 2019 versione 16,7 e precedenti, dopo il completamento del clone](./media/vs-2019/clone-complete-azure-devops.png)

1. Per visualizzare le cartelle e i file, selezionare il collegamento **Mostra visualizzazione cartelle** .

     ![Screenshot della sezione Solutions della finestra di Team Explorer in Visual Studio 2019 versione 16,7 e precedenti, dopo il completamento del clone](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio apre **Esplora soluzioni**.

1. Scegliere il collegamento **soluzioni e cartelle** per cercare un file di soluzione (in particolare un file con estensione sln) da aprire.

      ![Screenshot della notifica di "soluzioni e cartelle" da Team Explorer in Visual Studio 2019 versione 16,7 e precedenti](./media/open-proj-repo-solutions-folders.png)

   Se nel repository non è presente un file di soluzione, viene visualizzato il messaggio "nessuna soluzione trovata". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

---

## <a name="next-steps"></a>Passaggi successivi

Se è pronti a scrivere codice con Visual Studio, è possibile approfondire l'argomento in una delle esercitazioni specifiche per linguaggio seguenti:

- [Esercitazioni su Visual Studio | **C#**](./csharp/index.yml)
- [Esercitazioni di Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Esercitazioni di Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Esercitazioni di Visual Studio | **Python**](../python/index.yml)
- [Esercitazioni di Visual Studio | **JavaScript**, **TypeScript** e **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Vedi anche

- [Nuova esperienza Git in Visual Studio](../ide/git-with-visual-studio.md)
- [Azure DevOps Services: Introduzione a Azure Repos e Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: introduzione ad Azure DevOps](/learn/modules/get-started-with-devops/)