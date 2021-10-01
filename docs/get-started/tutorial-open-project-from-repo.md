---
title: 'Esercitazione: Aprire un progetto da un Visual Studio'
description: Informazioni su come aprire un progetto in un repository Git o Azure DevOps con Visual Studio.
ms.custom: vs-acquisition, get-started
ms.date: 09/30/2021
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
ms.openlocfilehash: bb17ea748e0948584818993acf383f555872907a
ms.sourcegitcommit: 65a1b6aae8387735f05a83b45e1a6865e9805e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2021
ms.locfileid: "129366368"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Esercitazione: Aprire un progetto da un repo
F In questa esercitazione si userà Visual Studio per connettersi a un repository per la prima volta e quindi aprire un progetto da esso.

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker range="vs-2022"

## <a name="open-a-project-from-a-github-repo"></a>Aprire un progetto da un repository GitHub

Visual Studio semplifica l'apertura di un progetto da un repo. È possibile farlo all'avvio di Visual Studio oppure direttamente dall'interno [dell'IDE Visual Studio .](visual-studio-ide.md?view=vs-2022&preserve-view=true)

Ecco come.

### <a name="use-the-start-window"></a>Usare la finestra iniziale

1. Aprire Visual Studio.

1. Nella finestra iniziale selezionare **Clona un repository.**

    :::image type="content" source="../ide/media/vs-2022/clone-repository.png" alt-text="Screenshot della finestra di dialogo Clona un repository in Visual Studio.":::

1. Immettere o digitare il percorso del repository e quindi selezionare il **pulsante Clone (Clona).**

    :::image type="content" source="../ide/media/vs-2022/clone-repository-enter-location.png" alt-text="[Screenshot della finestra di dialogo Clona un repository in Visual Studio in cui si immette l'URL di un repository Git.":::

1. È possibile che venga richiesto di immettere le informazioni di accesso utente nella finestra **di dialogo Informazioni utente** Git. È possibile aggiungere le informazioni o modificare le informazioni predefinite fornite.

    :::image type="content" source="../ide/media/vs-2022/git-user-information-dialog.png" alt-text="Screenshot della finestra di dialogo Git User Information (Informazioni utente Git) in cui immettere o modificare le informazioni sull'account Visual Studio 2022.":::

    Selezionare **Salva** per aggiungere le informazioni al file con estensione gitconfig globale. In caso contrario, è possibile scegliere di eseguire questa operazione in un secondo momento selezionando **Annulla.**

    > [!TIP]
    > Per altre informazioni sull'accesso a Visual Studio, vedere la pagina [**Accedere Visual Studio**](../ide/signing-in-to-visual-studio.md?view=vs-2022&preserve-view=true) accesso. Per informazioni specifiche su come usare l'account GitHub per accedere, vedere la pagina Usare account GitHub [**in Visual Studio.**](../ide/work-with-github-accounts.md?view=vs-2022&preserve-view=true) Se si riceve una notifica di attendibilità e si desidera saperne di più, vedere la pagina Configurare le impostazioni di [attendibilità per file e](../ide/reference/trust-settings.md?view=vs-2022&preserve-view=true) cartelle.

1. Successivamente, Visual Studio le soluzioni dal repository usando la **visualizzazione cartelle** in [**Esplora soluzioni**](../ide/use-solution-explorer.md?view=vs-2022&preserve-view=true).

    :::image type="content" source="../ide/media/vs-2022/git-solution-explorer-folder-view.png" alt-text="Screenshot della visualizzazione cartelle in Esplora soluzioni in Visual Studio 2022.":::

    È possibile visualizzare una soluzione in **Visualizzazione soluzione facendo** doppio clic sul relativo file con estensione sln.

    In caso contrario, è possibile selezionare **il pulsante** Cambia visualizzazione e quindi **selezionare Program.cs** per visualizzare il codice di una soluzione.

    :::image type="content" source="../ide/media/vs-2022/git-solution-explorer-switch-views.png" alt-text="Screenshot di un progetto in Git aperto in Esplora soluzioni, con il pulsante Cambia visualizzazioni evidenziato in Visual Studio 2022.":::

> [!TIP]
> La visualizzazione predefinita è impostata su Visualizzazione cartelle. È possibile modificarlo in Visualizzazione soluzione dal menu **Git.** Selezionare **Impostazioni**  >  **controllo del codice sorgente** Git Global  >  **Impostazioni**  >  **caricare automaticamente la** soluzione all'apertura di un repository Git a tale scopo.

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Aprire un progetto in locale da un GitHub clonato in precedenza

1. Aprire Visual Studio.

1. Nella finestra iniziale selezionare Apri **un progetto o una soluzione.**

    Visual Studio apre un'istanza di Esplora file, in cui è possibile passare alla soluzione o al progetto e quindi selezionarla per aprirla.

    :::image type="content" source="../ide/media/vs-2022/open-local-project-from-cloned-repo.png" alt-text="Screenshot della finestra &quot;Apri un progetto o una soluzione&quot; in Visual Studio 2022.":::

    > [!TIP]
    > Se il progetto o la soluzione è stata aperta di recente, selezionarla dalla **sezione** Apri recente per aprirla di nuovo rapidamente.

    Inizia a scrivere codice.

### <a name="use-the-ide"></a>Usare l'IDE

È anche possibile usare il  menu **Git** o il controllo Seleziona repository nell'IDE Visual Studio per interagire con le cartelle e i file di un repository.

Ecco come.

#### <a name="to-clone-a-repo-and-open-a-project"></a>Per clonare un repo e aprire un progetto

1. Nell'IDE Visual Studio selezionare il menu **Git** e quindi selezionare **Clone Repository (Clona repository).**

    :::image type="content" source="../ide/media/vs-2022/git-menu-clone-repository.png" alt-text="Screenshot dello screenshot del menu Git in Visual Studio 2022 con l'opzione Clona repository selezionata.":::

1. Seguire le istruzioni per connettersi al repository Git che include i file che si stanno cercando.

#### <a name="to-open-local-folders-and-files"></a>Per aprire cartelle e file locali

1. Nell'IDE Visual Studio selezionare il menu **Git,** selezionare **Repository locali** e quindi **selezionare Apri repository locale.**

    :::image type="content" source="../ide/media/vs-2022/git-menu-local-repositories.png" alt-text="Screenshot dello screenshot del menu Git in Visual Studio 2022 con l'opzione Repository locale e Apri repository locale visualizzata.":::

    In alternativa, è possibile eseguire la stessa attività da **Esplora soluzioni**. A tale scopo,  scegliere il controllo  Seleziona repository, selezionare l'icona  con i puntini di sospensione accanto alla casella Filtra repository e quindi selezionare **Apri repository locale.**

    :::image type="content" source="../ide/media/vs-2022/select-repository-filter-ellipsis.png" alt-text="Screenshot del controllo Seleziona repository con l'icona con i puntini di sospensione selezionata e l'opzione Apri repository locale visualizzata.":::

1. Seguire le istruzioni per connettersi al repository Git che contiene i file che si stanno cercando.

## <a name="browse-to-an-azure-devops-server"></a>Passare a un Azure DevOps Server

Ecco come passare a un'Azure DevOps Server usando Visual Studio.

1. Aprire Visual Studio.

1. Nella finestra iniziale selezionare **Clona un repository.**

    :::image type="content" source="../ide/media/vs-2022/clone-repository.png" alt-text="Screenshot della finestra di dialogo Clona un repository Visual Studio, per Azure DevOps.":::

1. Nella sezione **Esplora un repository** selezionare **Azure DevOps**.

    :::image type="content" source="../ide/media/vs-2022/browse-repository-azure-devops.png" alt-text="Screenshot della sezione &quot;Esplora un repository&quot; della finestra di dialogo &quot;Clona un repository&quot; Visual Studio, Azure DevOps evidenziato.":::

1. Seguire le istruzioni per connettersi a un Azure DevOps Server che ospita i file che si stanno cercando.

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-a-project-from-a-github-repo-with-visual-studio-2019"></a>Aprire un progetto da un GitHub 2019 con Visual Studio 2019

La modalità di apertura di un progetto da un GitHub di lavoro usando Visual Studio dipende dalla versione in uso. In particolare, se è stata installata la versione Visual Studio 2019 [**versione 16.8**](/visualstudio/releases/2019/release-notes-history) o successiva, è disponibile un'esperienza Git nuova [e completamente integrata in Visual Studio.](../ide/git-with-visual-studio.md)

Tuttavia, indipendentemente dalla versione installata, è sempre possibile aprire un progetto da un GitHub con Visual Studio.

### <a name="168-and-later"></a>16.8 e versioni successive

Ecco come usare Git in Visual Studio 2019 [**versione 16.8 o**](/visualstudio/releases/2019/release-notes-history) successiva.

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Clonare un GitHub e quindi aprire un progetto

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale selezionare **Clona un repository.**

   ![Screenshot della finestra di dialogo Clona un repository in Visual Studio 2019 versione 16.8 e successive](../ide/media/vs-2019/clone-repository.png)

1. Immettere o digitare il percorso del repository e quindi selezionare **Clona.**

   ![Screenshot della finestra di dialogo Clona un repository in cui si immette l'URL di un repository Git Visual Studio 2019 versione 16.8 e successive.](../ide/media/vs-2019/clone-repository-enter-location.png)

1. È possibile che venga richiesto di immettere le informazioni di accesso utente nella finestra **di dialogo Informazioni utente** Git. È possibile aggiungere le informazioni o modificare le informazioni predefinite fornite.

   ![Screenshot della finestra di dialogo Informazioni utente Git in cui è possibile immettere o modificare le informazioni sull'account in Visual Studio 2019 versione 16.8 e successive.](../ide/media/vs-2019/git-user-information-dialog.png)

    Selezionare **Salva** per aggiungere le informazioni al file con estensione gitconfig globale. In caso contrario, è possibile scegliere di eseguire questa operazione in un secondo momento selezionando **Annulla.**

    > [!TIP]
    > Per altre informazioni sull'accesso a Visual Studio, vedere la pagina [Accedere Visual Studio](../ide/signing-in-to-visual-studio.md?view=vs-2019&preserve-view=true) accesso. Per informazioni specifiche su come usare l'account GitHub per accedere, vedere la pagina Usare account GitHub [in Visual Studio.](../ide/work-with-github-accounts.md?view=vs-2019&preserve-view=true)

    Successivamente, Visual Studio carica e apre automaticamente la soluzione dal repository.

   ![Screenshot di un progetto in Git aperto in Esplora soluzioni in Visual Studio 2019 versione 16.8 e successive.](../ide/media/vs-2019/git-solution-explorer.png )

1. Se il repository contiene più soluzioni, queste verranno Esplora soluzioni. È possibile visualizzare l'elenco delle soluzioni selezionando il **pulsante Cambia** visualizzazioni in Esplora soluzioni.

   ![Screenshot di un progetto in Git aperto in Esplora soluzioni, con il pulsante Cambia visualizzazioni evidenziato in Visual Studio 2019 versione 16.8 e successive.](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Esplora soluzioni quindi la possibilità di aprire la cartella radice in **Visualizzazione cartelle** o di selezionare un file di soluzione da aprire.

   ![Screenshot del file con estensione sln in Git aperto in Esplora soluzioni, dopo aver selezionato il pulsante Cambia visualizzazione in Visual Studio 2019 versione 16.8 e successive.](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Per attivare o disattivare la visualizzazione, selezionare **di nuovo il pulsante Cambia** visualizzazione.

    > [!TIP]
    > È anche possibile usare il menu **Git** nell'IDE Visual Studio per clonare un repository e aprire un progetto.
    >
    > ![Screenshot del menu Git in Visual Studio 2019 versione 16.8 e successive.](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Aprire un progetto in locale da un GitHub clonato in precedenza

1. Aprire Visual Studio 2019 versione 16.8 o successiva.

1. Nella finestra iniziale selezionare Apri **un progetto o una soluzione.**

    Visual Studio apre un'istanza di Esplora file, in cui è possibile passare alla soluzione o al progetto e quindi selezionarla per aprirla.

   ![Screenshot della finestra "Apri un progetto o una soluzione" in Visual Studio 2019 versione 16.8 e successive.](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Se il progetto o la soluzione è stata aperta di recente, selezionarla dalla **sezione** Apri recente per aprirla di nuovo rapidamente.

    > [!TIP]
    > È anche possibile usare il menu **Git** nell'IDE Visual Studio per aprire cartelle e file locali da un repository clonato in precedenza.
    >
    > ![Screenshot del menu Git in Visual Studio 2019 versione 16.8 e successive, con l'opzione Repository locali espansa.](../ide/media/vs-2019/git-menu-local-repositories.png)

    Inizia a scrivere codice.

### <a name="167-and-earlier"></a>16.7 e versioni precedenti

Ecco come usare Git in Visual Studio 2019 [**versione 16.7 o**](/visualstudio/releases/2019/release-notes-history) precedenti.

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Clonare GitHub e quindi aprire un progetto

1. Aprire Visual Studio 2019 versione 16.7 o precedente.

1. Nella finestra iniziale selezionare **Clona o estrai il codice**.

   ![Screenshot della finestra "Crea un nuovo progetto" in Visual Studio 2019 versione 16.7 e precedenti.](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Immettere o digitare il percorso del repository e quindi selezionare **Clona.**

   ![Screenshot della finestra "Clona o estrai codice" in Visual Studio 2019 versione 16.7 e precedenti.](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio apre il progetto dal repository.

1. Se si ha un file di soluzione disponibile, verrà visualizzato nel menu a comparsa "Soluzioni e cartelle". Selezionarlo e Visual Studio apre la soluzione.

   ![Screenshot dell'Esplora soluzioni elenco a discesa in Visual Studio 2019 versione 16.7 e precedenti.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Se non si dispone di un file di soluzione (in particolare un file con estensione sln) nel proprio repo, il menu a comparsa visualizza il messaggio "No Solutions Found" (Nessuna soluzione trovata). Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

    Inizia a scrivere codice.

## <a name="connect-to-an-azure-devops-server-with-visual-studio-2019"></a>Connessione a un Azure DevOps Server con Visual Studio 2019

Ciò che viene visualizzato quando ci si connette a un Azure DevOps Server usando Visual Studio 2019 dipende dalla versione in uso. In particolare, se è stata installata la versione [**16.8**](/visualstudio/releases/2019/release-notes-history) o successiva, l'interfaccia utente è stata modificata per supportare una nuova esperienza Git completamente integrata [in](../ide/git-with-visual-studio.md) Visual Studio in Visual Studio.

Tuttavia, indipendentemente dalla versione installata, è sempre possibile connettersi a un Azure DevOps Server con Visual Studio.

### <a name="168-and-later"></a>16.8 e versioni successive

1. Aprire Visual Studio 2019 [**versione 16.8 o**](/visualstudio/releases/2019/release-notes-history) successiva.

1. Nella finestra iniziale selezionare **Clona un repository.**

   ![Screenshot della finestra di dialogo Clona un repository Visual Studio 2019 versione 16.8 e successive, per Azure DevOps.](../ide/media/vs-2019/clone-repository.png)

1. Nella sezione **Esplora un repository** selezionare **Azure DevOps**.

    ![Screenshot della sezione "Esplora un repository" della finestra di dialogo "Connessione a un Project" in Visual Studio 2019 versione 16.8 e successive.](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Se viene visualizzata una finestra di accesso, accedere al proprio account.

1. Nella finestra **Connessione a un Project** scegliere il repo a cui connettersi e quindi selezionare **Clona.**

      ![Screenshot della finestra di Connessione a un Project' generata da Visual Studio 2019 versione 16.8 e successive.](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Se non viene visualizzato un elenco precompilato di repository a cui connettersi, selezionare **Aggiungi** Azure DevOps Server per immettere un URL del server. In alternativa, potrebbe essere visualizzato il prompt "Nessun server trovato" che include collegamenti per aggiungere un Azure DevOps Server esistente o per creare un account Azure DevOps.

   Successivamente, Visual Studio apre **Esplora soluzioni** che mostra le cartelle e i file.

1. Selezionare la **Team Explorer** per visualizzare le Azure DevOps seguenti.

      ![Screenshot della finestra Team Explorer finestra di dialogo generata da Visual Studio 2019 versione 16.8 e successive.](../ide/media/vs-2019/team-explorer-azure-devops.png)

#### <a name="167-and-earlier"></a>16.7 e versioni precedenti

1. Aprire Visual Studio 2019 [**versione 16.7 o**](/visualstudio/releases/2019/release-notes-history) precedente.

1. Nella finestra iniziale selezionare **Clona o estrai il codice**.

   ![Screenshot della finestra "Crea un nuovo progetto" in Visual Studio 2019 versione 16.7 e precedenti.](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Nella sezione **Esplora un repository** selezionare **Azure DevOps**.

   ![Screenshot della finestra "Clona o estrai codice" con la sezione "Esplora un repository" che elenca Azure DevOps in Visual Studio 2019 versione 16.7 e precedenti.](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Se viene visualizzata una finestra di accesso, accedere al proprio account.

1. Nella finestra **Connessione a un Project** scegliere il repo a cui connettersi e quindi selezionare **Clona.**

      ![Screenshot della finestra di Connessione a un Project' generata da Visual Studio 2019 versione 16.7 e precedenti.](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ciò che compare nella casella di riepilogo dipende dai repository Azure DevOps ai quali si ha accesso.

   Visual Studio apre **Team Explorer** e viene visualizzata una notifica quando il clone è stato completato.

     ![Screenshot della finestra Team Explorer in Visual Studio 2019 versione 16.7 e precedenti, dopo il completamento della clonazione.](./media/vs-2019/clone-complete-azure-devops.png)

1. Per visualizzare le cartelle e i file, selezionare il **collegamento Mostra visualizzazione** cartelle.

     ![Screenshot della sezione Soluzioni della finestra Team Explorer in Visual Studio 2019 versione 16.7 e precedenti, dopo il completamento della clonazione.](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio apre **Esplora soluzioni**.

1. Scegliere il **collegamento Soluzioni e** cartelle per cercare un file di soluzione (in particolare un file con estensione sln) da aprire.

      ![Screenshot della notifica "Soluzioni e cartelle" Team Explorer in Visual Studio 2019 versione 16.7 e precedenti.](./media/open-proj-repo-solutions-folders.png)

   Se nel repo non è presente un file di soluzione, viene visualizzato il messaggio "No Solutions Found" (Nessuna soluzione trovata). Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-project-from-a-github-repo-with-visual-studio-2017"></a>Aprire un progetto da un GitHub 2017 con Visual Studio 2017

1. Aprire Visual Studio 2017.

1. Nella barra dei menu superiore selezionare **Apri file** dal controllo del >  > **codice sorgente.**

   Si apre il riquadro **Team Explorer - Connetti**.

    ![Finestra Team Explorer nell'IDE di Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Nella sezione **Repository Git locali** selezionare **Clona.**

    ![Scegliere Clona dalla sezione Repository Git locali](./media/open-proj-repo-local-git-repo-clone.png)

1. Nella casella * Immettere **l'URL** di un repository Git per clonare _, digitare o incollare l'URL del repository e quindi premere _*Invio**. Se viene visualizzata la richiesta di accedere a GitHub, eseguire questa operazione.

   Quando Visual Studio ha clonato il repository, Team Explorer si chiude e si apre Esplora soluzioni. Viene visualizzato il messaggio *Fare clic sopra su "Soluzioni e cartelle" per visualizzare un elenco di soluzioni*. Scegliere **Soluzioni e cartelle**.

   ![Scegliere "Soluzioni e cartelle" in Esplora soluzioni](./media/open-proj-repo-github-solutions-folders.png)

1. Se si ha un file di soluzione disponibile, verrà visualizzato nel menu a comparsa "Soluzioni e cartelle". Selezionarlo e Visual Studio aprirà la soluzione.

   ![Scegliere gli elementi da aprire dall'Esplora soluzioni a discesa.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Se nel repository non è disponibile un file di soluzione (con estensione sln), il menu a comparsa indicherà che "Non sono state trovate soluzioni". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

### <a name="review-your-work"></a>Esaminare il lavoro

Visualizzare l'animazione seguente per verificare il lavoro completato nella sezione precedente.

   ![Animazione dell'apertura di un progetto in un GitHub usando Visual Studio 2017.](./media/open-project-from-github.gif)

## <a name="open-a-project-from-an-azure-devops-repo-with-visual-studio-2017"></a>Aprire un progetto da un Azure DevOps 2017 con Visual Studio 2017

1. Aprire Visual Studio 2017.

1. Nella barra dei menu superiore selezionare **Apri file** dal controllo del >  > **codice sorgente.**

   Si apre il riquadro **Team Explorer - Connetti**.

    ![Finestra Team Explorer all'interno dell Visual Studio IDE.](./media/open-proj-repo-team-explorer.png)

1. Esistono due modi per connettersi al repository Azure DevOps:

      - Nella sezione **Provider di servizi ospitati** selezionare **Connessione...**.

        ![Sezione Provider di servizi ospitati della finestra Team Explorer all'interno dell Visual Studio IDE.](./media/open-proj-repo-azure-devops.png)

      - **Nell'elenco a** discesa Gestisci connessioni selezionare Connessione **a un Project...**.

        ![La sezione Gestisci connessioni della finestra Team Explorer all'interno dell'IDE Visual Studio.](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Nella finestra **Connessione a un Project** scegliere il repo a cui connettersi e quindi selezionare **Clona.**

      ![Finestra di Connessione a un Project' generata da Visual Studio.](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Ciò che compare nella casella di riepilogo dipende dai repository Azure DevOps ai quali si ha accesso.

1. Quando Visual Studio ha clonato il repository, Team Explorer si chiude e si apre Esplora soluzioni. Viene visualizzato il messaggio *Fare clic sopra su "Soluzioni e cartelle" per visualizzare un elenco di soluzioni*. Scegliere **Soluzioni e cartelle**.

      ![La notifica "Soluzioni e cartelle" Team Explorer in Visual Studio.](./media/open-proj-repo-solutions-folders.png)

   Un file di soluzione (con estensione sln) verrà visualizzato nel menu a comparsa "Soluzioni e cartelle". Selezionarlo e Visual Studio aprirà la soluzione.

   Se nel repository non è disponibile un file di soluzione, il menu a comparsa indicherà che "Non sono state trovate soluzioni". Tuttavia, è possibile fare doppio clic su qualsiasi file nel menu della cartella per aprirlo nell'editor di codice di Visual Studio.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

È possibile approfondire una delle esercitazioni seguenti specifiche del linguaggio:

- [Visual Studio esercitazioni | **C#**](./csharp/index.yml)
- [Esercitazioni di Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Esercitazioni di Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Esercitazioni di Visual Studio | **Python**](../python/index.yml)
- [Esercitazioni di Visual Studio | **JavaScript**, **TypeScript** e **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Vedi anche

- [Esperienza Git in Visual Studio](../ide/git-with-visual-studio.md)
- [Confrontare Git e Team Explorer side-by-side](../ide/git-team-explorer-feature-comparison.md)
- [Microsoft Learn: Introduzione a Git e GitHub in Visual Studio](/learn/modules/visual-studio-github-push/)
- [Microsoft Learn: Introduzione a Azure DevOps](/learn/modules/get-started-with-devops/)
- [Azure DevOps Services: Introduzione a Azure Repos e Visual Studio](/azure/devops/repos/git/gitquickstart/)