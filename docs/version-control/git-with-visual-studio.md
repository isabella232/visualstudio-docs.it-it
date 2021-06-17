---
title: Esperienza Git in Visual Studio 2019
titleSuffix: ''
description: Informazioni su come la nuova esperienza Git integrata in Visual Studio 2019 può aiutare a essere più produttivi.
ms.date: 04/01/2021
ms.topic: overview
ms.author: tglee
author: TerryGLee
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.manager: jmartens
ms.openlocfilehash: 7e8f428ea82fb36abf944b06c22e73f1b9ca9fb6
ms.sourcegitcommit: 113b7df611583307d3965984233a33355d6b0318
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2021
ms.locfileid: "112126560"
---
# <a name="git-experience-in-visual-studio"></a>Esperienza Git in Visual Studio

Git è ora l'esperienza di controllo della versione predefinita Visual Studio 2019. A [partire dalla versione 16.6,](/visualstudio/releases/2019/release-notes-v16.6)abbiamo lavorato alla creazione del set di funzionalità e all'iterazione in base ai commenti e suggerimenti degli utenti. La nuova esperienza Git è attivata per impostazione predefinita per tutti gli utenti con la versione [16.8.](/visualstudio/releases/2019/release-notes/)

> [!TIP]
> Git è il sistema di controllo della versione moderno più diffuso, quindi, sia che si sia uno sviluppatore professionale che si sta imparando a creare codice, Git può essere molto utile. Se non si ha di nuovo git, https://git-scm.com/ il sito Web è un buon punto di partenza. Qui sono disponibili fogli di informazioni, un libro online molto diffuso e video di git basics.

## <a name="how-to-use-git-in-visual-studio"></a>Come usare Git in Visual Studio

Verrà illustrato come usare la nuova esperienza Git in Visual Studio 2019, ma se si desidera eseguire prima una breve presentazione, vedere il video seguente: <br><br>*Lunghezza del video: 5,27 minuti*

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

Esistono tre modi per iniziare a usare Git con Visual Studio per essere più produttivi:

- [Aprire un repository Git esistente.](#open-an-existing-local-repository) Se il codice è già presente nel computer, è possibile aprirlo usando Apri   >    >  **progetto/soluzione** (o Cartella) e Visual Studio rileva automaticamente se ha un repository Git inizializzato.
- [Creare un nuovo repository Git](#create-a-new-git-repository). Se il codice non è associato a Git, è possibile creare un nuovo repository Git.
- [Clonare un repository Git esistente.](#clone-an-existing-git-repository) Se il codice su cui si vuole lavorare non è presente nel computer, è possibile clonare tutti i repository remoti esistenti.

> [!NOTE]
> A partire dalla [versione 16.8,](/visualstudio/releases/2019/release-notes/)Visual Studio 2019 include un'esperienza di account GitHub completamente integrata. È ora possibile aggiungere sia GitHub che GitHub Enterprise account al keychain. Sarà possibile aggiungerli e sfruttarli esattamente come si fa con gli account Microsoft, il che significa che l'accesso alle risorse GitHub sarà più semplice in tutti i Visual Studio. Per altre informazioni, vedere la pagina Usare gli account [GitHub Visual Studio](../ide/work-with-github-accounts.md) web.

## <a name="create-a-new-git-repository"></a>Creare un nuovo repository Git

Se il codice non è associato a Git, è possibile iniziare creando un nuovo repository Git. A tale scopo, selezionare **Git**  >  **Create Git Repository (Crea repository Git Git)** dalla barra dei menu. Quindi, nella **finestra di dialogo Crea un repository Git** immettere le informazioni.

:::image type="content" source="media/git-create-repository.png" alt-text="La finestra di dialogo Crea un repository Git in Visual Studio.":::

La **finestra di dialogo Crea un repository Git** semplifica il push del nuovo repository in GitHub. Per impostazione predefinita, il nuovo repository è privato, il che significa che l'utente è l'unico che può accedervi. Se si deseleziona la casella, il repository sarà pubblico, ovvero chiunque su GitHub potrà visualizzarlo.

> [!TIP]
> Indipendentemente dal fatto che il repository sia pubblico o privato, è meglio avere un backup remoto del codice archiviato in modo sicuro in GitHub anche se non si lavora con un team. In questo modo il codice sarà disponibile anche per l'utente, indipendentemente dal computer in uso.

È possibile scegliere di creare un repository Git solo locale usando **l'opzione Solo** locale. In caso contrario, è possibile collegare il progetto locale a un repository remoto vuoto esistente in Azure DevOps o a qualsiasi altro provider Git usando **l'opzione Existing Remote (Remoto** esistente).

## <a name="clone-an-existing-git-repository"></a>Clonare un repository Git esistente

Visual Studio un'esperienza di clonazione semplice. Se si conosce l'URL del repository che si vuole clonare, è possibile incollare l'URL nella sezione Percorso repository e quindi scegliere il percorso del disco in cui Visual Studio clonare. 

:::image type="content" source="media/git-clone-repository.png" alt-text="La finestra di dialogo Clona un repository Git Visual Studio.":::

Se non si conosce l'URL del repository, Visual Studio facile individuare e clonare il repository GitHub o Azure DevOps esistente.

### <a name="open-an-existing-local-repository"></a>Aprire un repository locale esistente

Dopo aver clonato o creato un repository, Visual Studio rileva il repository Git e  lo aggiunge all'elenco di repository locali nel menu Git. Da qui è possibile accedere rapidamente e passare da un repository Git all'altro.

:::image type="content" source="media/git-local-repositories.png" alt-text="Opzione Repository locali dal menu Git in Visual Studio ":::

## <a name="view-files-in-solution-explorer"></a>Visualizzare i file in Esplora soluzioni

Quando si clona un repository o si apre un repository locale, Visual Studio passa al contesto Git salvando e chiudendo eventuali soluzioni e progetti aperti in precedenza. Esplora soluzioni carica la cartella nella radice del repository Git ed esegue l'analisi dell'albero di directory per tutti i file di visualizzazione. Sono inclusi file come ad esempio CMakeLists.txt o quelli con estensione sln.

Visual Studio modifica la visualizzazione in base al file di visualizzazione caricato in Esplora soluzioni:

- Se si clona un repository che contiene un singolo file con estensione sln, Esplora soluzioni direttamente la soluzione.
- Se Esplora soluzioni non rileva alcun file con estensione sln nel repository, per impostazione predefinita carica Visualizzazione cartelle.
- Se il repository contiene più di un file con estensione sln, Esplora soluzioni visualizza l'elenco delle visualizzazioni disponibili tra cui scegliere.

È possibile passare dalla visualizzazione attualmente aperta all'elenco delle visualizzazioni usando il pulsante Cambia visualizzazioni nella barra degli strumenti Esplora soluzioni visualizzazione. 

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Esplora soluzioni con il pulsante Cambia visualizzazioni selezionato in Visual Studio.":::

## <a name="git-changes-window"></a>Finestra Modifiche Git

Git tiene traccia delle modifiche ai file nel repository mentre si lavora e separa i file nel repository in tre categorie. Queste modifiche sono equivalenti a quelle che verrebbero apportate quando si immette `git status` il comando nella riga di comando:

- **File non modificati:** questi file non sono stati modificati dall'ultimo commit.
- **File modificati:** questi file sono stati modificati dopo l'ultimo commit, ma non sono ancora stati modificati per il commit successivo.
- **File di stage:** questi file hanno modifiche che verranno aggiunte al commit successivo.

Durante l'attività, Visual Studio tiene traccia delle modifiche apportate al file nel progetto nella sezione **Modifiche** della **finestra Modifiche** Git.

:::image type="content" source="media/git-changes-window.png" alt-text="Finestra Git Changes (Modifiche Git) Visual Studio.":::

Quando si è pronti per la gestione delle modifiche, fare clic sul pulsante (segno più) in ogni file di cui si vuole eseguire lo stage oppure fare clic con il pulsante destro del mouse su un file e **+** quindi **scegliere Fase.** È anche possibile eseguire lo stage di tutti i file modificati con un solo clic usando il pulsante di gestione delle fasi (più) nella **+** parte superiore della **sezione** Modifiche.

Quando si crea una modifica per lo stage, Visual Studio una **sezione Modifiche di cui è stata creata una** fase. Al commit successivo **vengono aggiunte solo** le modifiche della sezione Modifiche di cui è stata apportata la fase, operazione che è possibile eseguire selezionando Esegui commit in più **fasi.** Il comando equivalente per questa azione è `git commit -m "Your commit message"` . È anche possibile annullare la configurazione delle modifiche facendo clic **sul pulsante -** (meno). Il comando equivalente per questa azione è `git reset <file_path>` l'annullamento della configurazione di un singolo file o l'annullamento della gestione temporanea di `git reset <directory_path>` tutti i file in una directory.

È anche possibile scegliere di non eseguire lo staging dei file modificati ignorando l'area di gestione temporanea. In questo caso, Visual Studio consente di eseguire direttamente il commit delle modifiche senza doverle creare per il commit. È sufficiente immettere il messaggio di commit e quindi selezionare **Commit All (Esegui commit di tutto).** Il comando equivalente per questa azione è `git commit -a` .

Visual Studio consente anche di eseguire facilmente il commit e la sincronizzazione con un solo clic usando i collegamenti Commit all (Esegui commit di tutto), **Push** (Esegui push) e Commit all (Esegui il commit di tutti) **e Sync (Sincronizza).** Quando si fa doppio clic  su  un file nelle sezioni Modifiche e Modifiche di gestione per fasi, è possibile visualizzare un confronto riga per riga con la versione non modificata del file.

:::image type="content" source="media/git-file-version-compare.png" alt-text="Confronto riga per riga delle versioni dei file in Visual Studio ":::

> [!TIP]
> È possibile associare un Azure DevOps di lavoro a un commit usando il carattere "#" se si è connessi al repository Azure DevOps. È possibile connettere il repository Azure DevOps tramite **Team Explorer**  >  **Gestisci connessioni**.

### <a name="select-an-existing-branch"></a>Selezionare un ramo esistente

Visual Studio visualizza il ramo corrente nel selettore nella parte superiore della **finestra Modifiche** Git.

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="I rami correnti che è possibile visualizzare usando il selettore nella parte superiore del selettore Modifiche Git in Visual Studio ":::

Current Branch è disponibile anche nella barra di stato nell'angolo inferiore destro dell'IDE Visual Studio.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Rami correnti che è possibile visualizzare usando la barra di stato nell'angolo inferiore destro nell'IDE Visual Studio ":::

Da entrambe le posizioni è possibile passare da un ramo all'altro esistente.

### <a name="create-a-new-branch"></a>Creare un nuovo ramo

È anche possibile creare un nuovo ramo. Il comando equivalente per questa azione è `git checkout -b <branchname>` .

La creazione di un nuovo ramo è semplice come immettere il nome del ramo e basarlo su un ramo esistente.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Finestra di dialogo Crea un nuovo ramo in Visual Studio ":::

È possibile scegliere un ramo locale o remoto esistente come base. La **casella di controllo Ramo** di estrazione consente di passare automaticamente al ramo appena creato. Il comando equivalente per questa azione è `git checkout -b <new-branch><existing-branch>` .

## <a name="git-repository-window"></a>Finestra Repository Git

Visual Studio è disponibile una nuova finestra **Repository Git,** ovvero una visualizzazione consolidata di tutti i dettagli nel repository, inclusi tutti i rami, i computer remoti e le cronologie di commit. È possibile accedere a questa finestra direttamente da **Git** o **Visualizza** sulla barra dei menu o dalla barra di stato.

### <a name="manage-branches"></a>Gestire i rami

Quando si seleziona **Gestisci rami** dal menu **Git,** la visualizzazione albero dei rami viene visualizzata nella **finestra Repository** Git. Nel riquadro sinistro è possibile usare il menu di scelta rapida facendo clic con il pulsante destro del mouse per estrarre rami, creare nuovi rami, unire, riassare, cherry-pick e altro ancora. Quando si fa clic sul ramo, è possibile visualizzare un'anteprima della relativa cronologia di commit nel riquadro di destra.

### <a name="incoming-and-outgoing-commits"></a>Commit in ingresso e in uscita

Quando si recupera un ramo, la finestra Modifiche **Git** include un indicatore sotto l'elenco a discesa del ramo, che visualizza il numero di commit nonpulled dal ramo remoto. Questo indicatore indica anche il numero di commit locali di cui non è stato eseguito il commit.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Finestra Git Changes (Modifiche Git) che mostra l'elemento dell'interfaccia utente a discesa dell'indicatore Visual Studio ":::

L'indicatore funziona anche come collegamento per visualizzare la cronologia di commit di tale ramo nella **finestra Repository** Git. Nella parte superiore della cronologia vengono ora visualizzati i dettagli di questi commit in ingresso e in uscita. Da qui è anche possibile decidere di eseguire il pull o il push dei commit.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Finestra Repository Git che mostra la cronologia di commit di un ramo in Visual Studio ":::

#### <a name="commit-details"></a>Dettagli commit

Quando si fa doppio clic **su** un commit, Visual Studio i relativi dettagli in una finestra degli strumenti separata. Da qui è possibile ripristinare il commit, reimpostarlo, modificare il messaggio di commit o creare un tag nel commit. Quando si fa clic su un file modificato nel commit, Visual Studio apre la visualizzazione **Diff** affiancata del commit e del relativo elemento padre.

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Finestra di dialogo Dettagli commit in Visual Studio ":::

## <a name="handle-merge-conflicts"></a>Gestire i conflitti di merge

Durante un'unione possono verificarsi conflitti se due sviluppatori modificano le stesse righe in un file e Git non sa automaticamente quale sia la risposta corretta. Git interrompe l'unione e informa l'utente che si è in uno stato di conflitto.

Visual Studio semplifica l'identificazione e la risoluzione di un conflitto di merge. In primo luogo, **la finestra Repository Git** mostra una barra informazioni color oro nella parte superiore della finestra.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Messaggio &quot;Unione completata con conflitti&quot; in Visual Studio ":::

Nella **finestra Git Changes** (Modifiche Git) viene visualizzato anche il messaggio *"Merge is in progress with conflicts"*(Unione in corso con conflitti), con i file non uniti nella relativa sezione separata sotto di esso.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Messaggio &quot;Merge in progress with conflicts&quot; (Unione in corso con conflitti) in Visual Studio ":::

Tuttavia, se nessuna di queste finestre è aperta e si passa invece al file con conflitti di unione, non sarà necessario cercare il testo seguente:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Al contrario, Visual Studio visualizza una barra informazioni color oro nella parte superiore della pagina che indica che il file aperto presenta conflitti. È quindi possibile fare clic sul collegamento per aprire **l'Editor di merge**.

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Screenshot del messaggio &quot;Il file contiene conflitti di merge&quot; in Visual Studio ":::

### <a name="the-merge-editor"></a>Editor di merge

L'editor di merge Visual Studio è uno strumento di merge a tre modalità che consente di visualizzare le modifiche in ingresso, le modifiche correnti e il risultato dell'unione. È possibile utilizzare la barra degli strumenti al livello superiore **dell'Editor** di merge per spostarsi tra conflitti e differenze di unione automatica nel file.

:::image type="content" source="media/git-merge-editor.png" alt-text="Editor di merge in Visual Studio ":::

È anche possibile usare gli interruttori per mostrare/nascondere le differenze, mostrare/nascondere le differenze tra parole e personalizzare il layout. Nella parte superiore di ogni lato sono presenti caselle di controllo che è possibile usare per eseguire tutte le modifiche da un lato o dall'altro. Tuttavia, per apportare singole modifiche, è possibile fare clic sulle caselle di controllo a sinistra delle righe in conflitto su entrambi i lati. Infine, al termine della risoluzione dei conflitti, è possibile selezionare il **pulsante** Accetta unione nell'editor di merge. Si scrive quindi un messaggio di commit e si esegue il commit delle modifiche per completare la risoluzione.

## <a name="personalize-your-git-settings"></a>Personalizzare le impostazioni git

Per personalizzare le impostazioni Git a livello di repository e a livello globale, passare a **Impostazioni Git** sulla barra dei menu o a Strumenti Opzioni Controllo del codice sorgente sulla barra  >   dei   >    >   menu. Scegliere quindi le [opzioni](git-settings.md) desiderate.

:::image type="content" source="media/git-options-settings.png" alt-text="Finestra di dialogo Opzioni in cui è possibile scegliere le impostazioni di personalizzazione e personalizzazione nell Visual Studio IDE ":::

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio"></a>Come usare l'esperienza Team Explorer completa in Visual Studio

La nuova esperienza Git è il sistema di controllo della versione predefinito Visual Studio 2019 a partire dalla [versione 16.8.](/visualstudio/releases/2019/release-notes/) Tuttavia, se si desidera disattivarlo, è possibile. Passare a **Strumenti Opzioni** Funzionalità di anteprima dell'ambiente e quindi attivare o disattivare la casella di controllo Nuova esperienza utente Git, che consente di tornare  >    >    >   Team Explorer per Git. 

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Sezione Funzionalità di anteprima della finestra di dialogo Opzioni in Visual Studio ":::

## <a name="whats-next"></a>Passaggi successivi

Anche se la nuova esperienza Git è ora disponibile per impostazione predefinita in Visual Studio 2019 [versione 16.8,](/visualstudio/releases/2019/release-notes/)microsoft continua ad aggiungere nuove funzionalità per migliorare l'esperienza. Se si desidera consultare i nuovi aggiornamenti per l'esperienza Git in una versione di anteprima, è possibile scaricarlo e [installarlo dalla](https://aka.ms/vspreview/) pagina Visual Studio Preview.

> [!IMPORTANT]
> Se hai un suggerimento, inviaci un suggerimento. L'opportunità di interagire con l'utente in caso di decisioni di progettazione tramite il [**portale Developer Community.**](https://aka.ms/vs-suggest)

## <a name="see-also"></a>Vedi anche

- [Introduzione a Git e GitHub in Visual Studio](/learn/modules/visual-studio-github-push/) esercitazione su Microsoft Learn
- Video [Introduzione a Git in Visual Studio](https://www.youtube.com/watch?v=GCZ9x3yqkyc) su YouTube
- Post di blog [announcing the Release of the Git Experience in Visual Studio](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/) (Annuncio del rilascio dell'esperienza Git in Visual Studio blog)
- [Video di lancio della nuova esperienza Git](https://www.youtube.com/watch?v=UHrAg3iKoe0&t) su YouTube
- [La Visual Studio Toolbox presenta: Il](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) nuovo video sull'esperienza Git su Channel 9 e [su YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be)
- [Nuovi interessanti aggiornamenti per l'esperienza Git nel](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/) post Visual Studio blog
- Post di blog [su Git Experience in Visual Studio 2019 (Esperienza Git migliorata in Visual Studio 2019)](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)
- [Utilizzare gli account GitHub in Visual Studio](../ide/work-with-github-accounts.md)
- [note sulla versione di Visual Studio 2019](/visualstudio/releases/2019/release-notes)
