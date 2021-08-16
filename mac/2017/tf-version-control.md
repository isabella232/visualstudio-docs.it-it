---
title: Controllo della versione di Team Foundation
description: Connessione da Visual Studio per Mac a Team Foundation Server/Azure DevOps con il controllo della versione di Team Foundation (TFVC).
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: e473746ce129352950a0e36ae25e44065facf5b780f45598c1366fdab9b39e9b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121350555"
---
# <a name="connecting-to-team-foundation-version-control"></a>Connessione al controllo della versione di Team Foundation

> [!NOTE]
> Per ottenere un'esperienza ottimale di controllo della versione in macOS, è consigliabile usare Git invece del controllo della versione di Team Foundation (TFVC). Git è supportato in Visual Studio per Mac e rappresenta l'opzione predefinita per i repository ospitati in Team Foundation Server (TFS) o Azure DevOps. Per altre informazioni sull'uso di Git con TFS/Azure DevOps, vedere l'articolo [Impostazione di un repository Git](./set-up-git-repository.md).
>
> Se è stata usata in precedenza la versione di anteprima dell'estensione TFVC per Visual Studio per Mac, non è più supportata in caso di aggiornamento a Visual Studio 2019 per Mac.

Azure Repos fornisce due modelli di controllo della versione: [Git](/azure/devops/repos/git/?view=azure-devops&preserve-view=true), un sistema di controllo della versione distribuito [e controllo della versione di Team Foundation](/azure/devops/repos/tfvc/index?view=azure-devops&preserve-view=true) (TFVC), un sistema di controllo della versione centralizzato.

Visual Studio per Mac offre il supporto completo per i repository Git, ma richiede alcune soluzioni alternative per usare il controllo della versione di Team Foundation. Se attualmente si usa il controllo della versione di Team Foundation, ecco alcune soluzioni che è possibile adottare per accedere al codice sorgente ospitato nel controllo della versione di Team Foundation:

* [Usare Visual Studio Code e l'estensione Azure Repos, per un'interfaccia utente grafica](#use-visual-studio-code-and-the-azure-repos-extension)
* [Connettersi al repository usando il client della riga di comando Team Explorer Everywhere (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Connettersi al controllo della versione di Team Foundation usando l'estensione di controllo della versione di Team Foundation (non supportata) per Visual Studio per Mac](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

Il resto di questo articolo illustra le opzioni elencate in precedenza.

## <a name="requirements"></a>Requisiti

* Visual Studio Community, Professional o Enterprise per Mac versione 7.8 e successive.
* Azure DevOps Services, Team Foundation Server 2013 e versioni successive o Azure DevOps Server 2018 e versioni successive.
* Un progetto in Azure DevOps Services o Team Foundation Server/Azure DevOps Server configurato per l'uso del controllo della versione di Team Foundation.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Usare Visual Studio Code e l'estensione Azure Repos

Se si preferisce lavorare con un'interfaccia grafica per gestire i file nel controllo della versione, l'estensione Azure Repos per Visual Studio Code offre una soluzione supportata da Microsoft. Per iniziare, scaricare [Visual Studio Code](https://code.visualstudio.com) e quindi scoprire come [configurare l'estensione Azure Repos](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Connessione tramite il client della riga di comando Team Explorer Everywhere (TEE-CLC)

Se si ha familiarità con il Terminale macOS, il client della riga di comando Team Explorer Everywhere (TEE-CLC) offre un metodo supportato per la connessione all'origine nel controllo della versione di Team Foundation.

È possibile seguire la procedura seguente per configurare la connessione al controllo della versione di Team Foundation ed eseguire il commit delle modifiche.

### <a name="setting-up-the-tee-clc"></a>Configurare TEE-CLC

Esistono due modi per configurare TEE-CLC.

* Usare Homebrew per installare il client, o
* Scaricare e installare manualmente il client

La soluzione più semplice prevede l'**uso di HomeBrew**, ovvero una gestione pacchetti per macOS. Per eseguire l'installazione con questo metodo:

1. Avviare l'applicazione Terminale di macOS.
1. Installare Homebrew con il Terminale e seguendo le istruzioni riportate nella [home page di Homebrew](https://brew.sh/).
1. Dopo aver installato Homebrew, eseguire il comando seguente dal Terminale: `brew install tee-clc`

Per **configurare manualmente TEE-CLC**:

1. [Scaricare la versione più recente di TEE-CLC](https://github.com/Microsoft/team-explorer-everywhere/releases) dalla pagina delle versioni del repository di GitHub per Team Explorer Everywhere (ad esempio tee-clc-14.134.0.zip al momento della stesura di questo articolo).
1. Estrarre il contenuto del file ZIP in una cartella su disco.
1. Aprire l'app Terminale di macOS e usare il comando `cd` per passare alla cartella usata nel passaggio precedente.
1. Da questa cartella eseguire il comando `./tf` per verificare che il client della riga di comando possa essere eseguito. Potrebbe essere richiesto di installare Java o altre dipendenze.

Dopo aver installato TEE-CLC, è possibile eseguire il comando `tf eula` per visualizzare e accettare il contratto di licenza per il client.

Infine, per l'autenticazione nell'ambiente TFS/Azure DevOps, sarà necessario creare un token di accesso personale nel server. Altre informazioni sull'[autenticazione con token di accesso personali](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops&preserve-view=true). Quando si crea un token di accesso personale da usare con il controllo della versione di Team Foundation, assicurarsi di assegnare l'accesso completo quando si configura il token.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Uso di TEE-CLC per la connessione al repository

Per connettersi al codice sorgente, è innanzitutto necessario creare un'area di lavoro usando il comando `tf workspace`. I comandi seguenti, ad esempio, consentono la connessione a un'organizzazione in Azure DevOps Services chiamata "MyOrganization": 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

L'impostazione di ambiente `TF_AUTO_SAVE_CREDENTIALS` viene usata per salvare le credenziali in modo che non venga richiesto di immetterle più volte. Quando viene richiesto un nome utente, usare il token di accesso personale creato nella sezione precedente e una password vuota.

Per creare un mapping dei file di origine in una cartella locale, si userà il comando `tf workfold`. Nell'esempio seguente verrà eseguito il mapping di una cartella denominata "WebApp.Services" dal progetto di controllo della versione di Team Foundation "MyRepository" e tale cartella verrà configurata per la copia nella cartella ~/Projects/ locale (ad esempio una cartella "Progetti" nella home directory degli utenti correnti).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Infine, si usa il comando seguente per ottenere i file di origine dal server e copiarli in locale:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>Eseguire il commit delle modifiche tramite TEE-CLC

Dopo aver apportato le modifiche ai file in Visual Studio per Mac, è possibile tornare al Terminale per archiviare le modifiche. Il comando `tf add` viene usato per aggiungere file all'elenco delle modifiche in sospeso da archiviare e il comando `tf checkin` esegue l'archiviazione effettiva nel server. Il comando `checkin` include parametri per aggiungere un commento o associare un elemento di lavoro correlato. Nel frammento di codice seguente vengono aggiunti tutti i file in una cartella `WebApp.Services`, in modo ricorsivo, al processo di archiviazione. Il codice viene quindi archiviato con un commento e associato a un elemento di lavoro con ID "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Per altre informazioni sui comandi qui indicati o su altri comandi, è possibile usare il comando seguente dal Terminale:

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Connettersi al controllo della versione di Team Foundation tramite l'estensione

> [!NOTE]
> Per ottenere un'esperienza ottimale di controllo della versione in macOS, è consigliabile usare Git invece del controllo della versione di Team Foundation (TFVC). Git è supportato in Visual Studio per Mac e rappresenta l'opzione predefinita per i repository ospitati in Team Foundation Server (TFS) o Azure DevOps. Per altre informazioni sull'uso di Git con TFS/Azure DevOps, vedere l'articolo [Impostazione di un repository Git](./set-up-git-repository.md).
>
> Se è stata usata in precedenza la versione di anteprima dell'estensione TFVC per Visual Studio per Mac, non è più supportata in caso di aggiornamento a Visual Studio 2019 per Mac.

La raccolta delle estensioni per Visual Studio per Mac include un'estensione del controllo della versione di Team Foundation che offre un supporto limitato per la connessione al controllo della versione di Team Foundation. L'estensione non è supportata e presenta numerosi problemi noti, quindi l'esperienza di uso potrebbe essere variabile.

Per installare l'estensione, avviare Visual Studio per Mac e scegliere il menu **Visual Studio > Estensioni**. Nella scheda **Raccolta** selezionare **Controllo della versione > Controllo della versione di Team Foundation per TFS e Azure DevOps** e fare clic su **Installa**:

![Gestione estensioni](media/tfvc-install.png)

Seguire i prompt per installare l'estensione. Al termine dell'installazione, riavviare l'IDE.

### <a name="updating-the-extension"></a>Aggiornamento dell'estensione

Periodicamente vengono rilasciati aggiornamenti per l'estensione TFVC. Per accedere agli aggiornamenti, **scegliere Visual Studio > dal** menu e selezionare la **scheda** Aggiornamenti. Selezionare l'estensione nell'elenco e fare clic **sul pulsante** Aggiorna:

Scegliere **Installa** nella finestra di dialogo successiva per disinstallare il pacchetto precedente e installare quello nuovo.

### <a name="using-the-extension"></a>Uso dell'estensione

Dopo aver installato l'estensione, selezionare la voce di menu **Version Control > TFS/Azure DevOps > Open from Remote Repository** (Controllo della versione > TFS/Azure DevOps > Apri da repository remoto).

![Voce di menu per aprire l'estensione](media/tfvc-source-control-explorer-devops.png)

Scegliere VSTS o Team Foundation Server per iniziare e premere **Continue** (Continua):

![Connettersi con un server](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Autenticazione Azure Repos

Quando si seleziona un progetto ospitato in Azure Repos, viene richiesto di immettere i dati dell'account Microsoft:

![Connettersi con Azure Repos](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>Autenticazione TFS

Per connettersi a TFS, immettere i dettagli del server e le credenziali dell'account. Immettere un dominio per usare l'autenticazione NTLM oppure lasciare il campo vuoto per usare l'autenticazione di base. Selezionare **Aggiungi server**:

![Accedere a un server TFS](media/tfvc-login.png)

### <a name="selecting-a-project"></a>Selezione di un progetto

Dopo aver eseguito l'autenticazione, è possibile visualizzare un elenco dei repository associati all'account nella finestra di dialogo **Apri dal controllo del codice sorgente**:

![Finestra di dialogo Apri dal controllo del codice sorgente con progetti visualizzati](media/tfvc-vsts-projects.png)

Questa finestra di dialogo è suddivisa nei nodi seguenti:

- Organizzazione o raccolta di Azure DevOps: vengono visualizzate tutte le organizzazioni connesse all'account Microsoft usato per eseguire l'accesso.
- Progetti: ogni organizzazione o raccolta può contenere una serie di progetti. Il progetto è la posizione in cui sono ospitati il codice sorgente, gli elementi di lavoro e le compilazioni automatiche.

È possibile eseguire ricerche e applicare filtri in base al nome di un progetto o di un'organizzazione.

#### <a name="adding-a-new-server"></a>Aggiunta di un nuovo server

Per aggiungere un nuovo server all'elenco, scegliere il pulsante **Aggiungi host** nella finestra di dialogo **Apri dal controllo del codice sorgente**:

![Pulsante Aggiungi per l'aggiunta di un nuovo server all'elenco](media/tfvc-add-new-server.png)

Selezionare il provider dall'elenco e immettere le credenziali:

![Finestra di dialogo con l'opzione per il provider del controllo del codice sorgente](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>Creazione di una nuova area di lavoro

Per iniziare a lavorare con un progetto, è necessaria un'_area di lavoro_. Se non è già disponibile un'area di lavoro, è possibile crearne una dalla casella combinata **Area di lavoro** nella finestra di dialogo **Apri dal controllo del codice sorgente**:

![Creare una nuova opzione di casella combinata dell'area di lavoro](media/tfvc-create-new-workspace.png)

Impostare il nome e il percorso locale per la nuova area di lavoro e selezionare **Crea area di lavoro**:

![Immettere un nome e un percorso locale per la nuova area di lavoro](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>Uso di Esplora controllo codice sorgente

Dopo aver creato un'area di lavoro e aver eseguito il mapping del progetto, è possibile iniziare a usare _Esplora controllo codice sorgente_.

Per aprire Esplora controllo codice sorgente, selezionare **Controllo della versione > TFS/Azure DevOps > Esplora controllo codice sorgente**.

Esplora controllo codice sorgente consente di esplorare tutti i progetti mappati e i relativi file e cartelle. Consente anche di eseguire tutte le azioni di base per il controllo del codice sorgente, ad esempio:

- Ottenere la versione più recente
- Ottenere una versione specifica
- Archiviare ed estrarre file
- Bloccare e sbloccare i file
- Aggiungere, eliminare e rinominare i file
- Visualizzare la cronologia
- Confronto delle modifiche.

Molte di queste azioni sono disponibili tramite i menu di scelta rapida del progetto:

![Azioni dei menu di scelta rapida di un progetto](media/tfvc-sourcecode-actions.png)

### <a name="managing-workspaces"></a>Gestione delle aree di lavoro

Se non è ancora stata creata un'area di lavoro, come descritto nella sezione [Creazione di una nuova area di lavoro](#creating-a-new-workspace), Esplora controllo codice sorgente è vuoto:

![Esplora controllo codice sorgente vuoto](media/tfvc-setup-empty-sce.png)

Per configurare il progetto remoto con un'area di lavoro locale, seguire questa procedura:

1. Selezionare il **Server** dalla casella combinata.
1. Si noti che non sono presenti aree di lavoro e che il percorso locale non è mappato. Selezionare il collegamento **Non mappato** per visualizzare la finestra di dialogo **Crea nuova area di lavoro**.
1. Specificare un nome per l'area di lavoro e quindi fare clic su **Aggiungi Cartella di lavoro** per eseguire il mapping del progetto in una cartella locale nel computer:

    ![Creare una nuova finestra dell'area di lavoro con le opzioni predefinite](media/tfvc-workspace1.png)

1. Selezionare la cartella "$" per eseguire il mapping di tutti i progetti del server alla stessa area di lavoro o selezionare un singolo progetto e fare clic su **OK**:

    ![Finestra di dialogo Cerca cartella con tutti i progetti visualizzati](media/tfvc-workspace2.png)

1. Selezionare il percorso del computer locale a cui si vuole mappare il progetto o i progetti e fare clic su **Seleziona cartella**.
1. Confermare i dettagli della nuova area di lavoro scegliendo **OK**

    ![Creare una nuova finestra dell'area di lavoro con la cartella di lavoro aggiunta](media/tfvc-workspace3.png)

Dopo aver configurato l'area di lavoro, è possibile modificarla o rimuoverla facendo clic sul pulsante **Gestisci aree di lavoro** in Esplora controllo codice sorgente.

![Gestisci aree di lavoro](media/tfvc-workspace4.png)

## <a name="troubleshooting-and-known-issues"></a>Risoluzione dei problemi e problemi noti

#### <a name="problems-using-basic-authentication"></a>Problemi relativi all'uso dell'autenticazione di base

Le opzioni seguenti possono essere usate eseguire l'autenticazione in un server:

- Oauth
- Basic
- NTLM

Per usare l'autenticazione di base è necessario abilitare le **credenziali di autenticazione alternative** in Azure DevOps Services seguendo questa procedura:

1. Accedere all'organizzazione di Azure DevOps come proprietario (https:\//dev.azure.com/{organizzazione}/{project}).

2. Dalla barra degli strumenti dell'organizzazione selezionare l'icona a forma di ingranaggio, quindi **Policy** (Criteri):

    ![Screenshot della barra Azure DevOps dell'organizzazione con l'icona a forma di ingranaggio selezionata e criteri selezionati nel menu a discesa.](media/tfvc-auth2.png)

3. Verificare le impostazioni di connessione dell'applicazione. Modificare queste impostazioni in base ai propri criteri di sicurezza:

    ![Screenshot della schermata Criteri in Azure DevOps Services, che mostra le impostazioni per i criteri di connessione dell'applicazione.](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>Nel controllo della versione di Team Foundation non viene visualizzato nulla

Per configurare il controllo della versione di Team Foundation nel computer di sviluppo, **è necessario** creare un'area di lavoro, come descritto nella sezione [Gestione delle aree di lavoro](#managing-workspaces).

In Esplora controllo codice sorgente premere il pulsante **Gestisci aree di lavoro**. Seguire la procedura per eseguire il mapping del progetto team a una cartella sul computer di sviluppo.

#### <a name="i-do-not-see-any--all-of-my-projects"></a>Non viene visualizzato alcun progetto

Dopo l'autenticazione viene visualizzato l'elenco dei progetti. Per impostazione predefinita, vengono visualizzati solo i progetti Team Foundation Server. Per visualizzare altri tipi di progetti, selezionare la casella "See all projects" (Visualizza tutti i progetti).

Tenere presente che i progetti contenuti nel server non verranno visualizzati se non si hanno i privilegi corretti.

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Viene visualizzato l'errore "Cannot create the workspace. Please, try again" (Impossibile creare l'area di lavoro. Riprovare.)

Quando si tenta di [creare una nuova area di lavoro](#creating-a-new-workspace), verificare che siano soddisfatte le condizioni seguenti:

- Il nome dell'area di lavoro non deve contenere caratteri non validi.
- Il nome deve essere composto da un massimo di 64 caratteri.
- Il percorso locale non può essere usato da altre aree di lavoro.

### <a name="see-also"></a>Vedi anche

- [Sviluppare e condividere il codice nel controllo della versione di Team Foundation usando Visual Studio (in Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)