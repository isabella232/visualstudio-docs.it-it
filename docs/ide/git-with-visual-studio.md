---
title: Esperienza git in Visual Studio
titleSuffix: ''
description: Scopri in che modo la nuova esperienza git integrata in Visual Studio 2019 può aiutarti a migliorare la produttività.
ms.date: 11/16/2020
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: e640d19659861a03d0f97abc799344bebb14b936
ms.sourcegitcommit: f78960320798e2c6b33145cee77a2221f031603c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2020
ms.locfileid: "94878309"
---
# <a name="git-experience-in-visual-studio"></a>Esperienza git in Visual Studio

Git è ora l'esperienza di controllo della versione predefinita in Visual Studio 2019. Dalla [versione 16,6](/visualstudio/releases/2019/release-notes-v16.6), abbiamo lavorato per creare il set di funzionalità e scorrerlo in base ai commenti e suggerimenti degli utenti. La nuova esperienza git è attivata per impostazione predefinita per tutti gli utenti con il rilascio della [versione 16,8](/visualstudio/releases/2019/release-notes/).

> [!TIP]
> Git è il sistema di controllo della versione moderno più diffuso, quindi se sei uno sviluppatore professionale o se stai imparando a usare il codice, Git può essere molto utile. Se non si ha familiarità con git, il https://git-scm.com/ sito Web è un valido punto di partenza. Qui troverai i fogli informativi, un popolare libro online e i video di base di git.

## <a name="how-to-use-git-in-visual-studio"></a>Come usare git in Visual Studio

Verrà illustrato come usare la nuova esperienza git in Visual Studio 2019, ma se si vuole iniziare prima una breve panoramica, vedere il video seguente: <br><br>*Lunghezza video: 5,27 minuti*

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

Sono disponibili tre modi per iniziare a usare git con Visual Studio per aumentare la produttività:

- [Aprire un repository Git esistente](#open-an-existing-local-repository). Se il codice è già presente nel computer, è possibile aprirlo usando **file**  >  **Apri**  >  **progetto/soluzione** (o **cartella**) e Visual Studio rileva automaticamente se dispone di un repository git inizializzato.
- [Creare un nuovo repository git](#create-a-new-git-repository). Se il codice non è associato a git, è possibile creare un nuovo repository git.
- [Clonare un repository Git esistente](#clone-an-existing-git-repository). Se il codice su cui si vuole lavorare non è presente nel computer, è possibile clonare tutti i repository remoti esistenti.

> [!NOTE]
> A partire dalla [versione 16,8](/visualstudio/releases/2019/release-notes/), Visual Studio 2019 include un'esperienza di account github completamente integrata. È ora possibile aggiungere gli account GitHub e GitHub Enterprise al keychain. Potrai aggiungerli e usarli come con gli account Microsoft, il che significa che avrai a disposizione un momento più semplice per accedere alle risorse di GitHub in Visual Studio. Per altre informazioni, vedere la pagina [work with GitHub Accounts in Visual Studio](work-with-github-accounts.md) .

## <a name="create-a-new-git-repository"></a>Creare un nuovo repository git

Se il codice non è associato a git, è possibile iniziare creando un nuovo repository git. A tale scopo, selezionare **git**  >  **Crea repository git** dalla barra dei menu. Quindi, nella finestra di dialogo **creare un repository git** immettere le informazioni.

:::image type="content" source="media/git-create-repository.png" alt-text="La finestra di dialogo creare un repository git in Visual Studio.":::

La finestra di dialogo **creare un repository git** consente di eseguire facilmente il push del nuovo repository in GitHub. Per impostazione predefinita, il nuovo repository è privato, ovvero l'unico utente che può accedervi. Se si deseleziona la casella, il repository sarà pubblico, il che significa che chiunque su GitHub potrà visualizzarlo.

> [!TIP]
> Se il repository è pubblico o privato, è preferibile disporre di un backup remoto del codice archiviato in modo sicuro su GitHub anche se non si lavora con un team. Questo rende anche il codice disponibile indipendentemente dal computer in uso.

È possibile scegliere di creare un repository git solo locale usando l'opzione **solo locale** . In alternativa, è possibile collegare il repository a qualsiasi repository remoto vuoto esistente in qualsiasi altro provider git usando l'opzione **remota esistente** .

## <a name="clone-an-existing-git-repository"></a>Clonare un repository Git esistente

Visual Studio include un'esperienza di clonazione semplice. Se si conosce l'URL del repository che si vuole clonare, è possibile incollare l'URL nella sezione **percorso repository** , quindi scegliere il percorso del disco in cui si vuole clonare Visual Studio.

:::image type="content" source="media/git-clone-repository.png" alt-text="La finestra di dialogo clonare un repository git in Visual Studio.":::

Se non si conosce l'URL del repository, Visual Studio semplifica la ricerca e quindi la clonazione del repository GitHub o Azure DevOps esistente.

### <a name="open-an-existing-local-repository"></a>Apre un repository locale esistente

Dopo aver clonato un repository o averne creato uno, Visual Studio rileva il repository git e lo aggiunge all'elenco dei repository **locali** nel menu git. Da qui è possibile accedere rapidamente e spostarsi tra i repository git.

:::image type="content" source="media/git-local-repositories.png" alt-text="Opzione repository locali dal menu git in Visual Studio ":::

## <a name="view-files-in-solution-explorer"></a>Visualizza file in Esplora soluzioni

Quando si clona un repository o si apre un repository locale, Visual Studio passa a tale contesto git salvando e chiudendo le soluzioni e i progetti aperti in precedenza. Esplora soluzioni carica la cartella nella radice del repository git e analizza l'albero di directory per tutti i file di visualizzazione. Sono inclusi i file, ad esempio CMakeLists.txt o quelli con estensione sln.

Visual Studio regola la visualizzazione in base al file di visualizzazione caricato Esplora soluzioni:

- Se si clona un repository che contiene un solo file con estensione sln, Esplora soluzioni carica direttamente la soluzione.
- Se Esplora soluzioni non rileva alcun file con estensione sln nel repository, per impostazione predefinita carica la visualizzazione cartelle.
- Se il repository contiene più di un file con estensione sln, Esplora soluzioni Visualizza l'elenco delle visualizzazioni disponibili tra cui scegliere.

È possibile passare dalla visualizzazione attualmente aperta all'elenco di visualizzazioni utilizzando il pulsante **Cambia viste** sulla barra degli strumenti Esplora soluzioni.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Esplora soluzioni con il pulsante Cambia viste selezionato in Visual Studio.":::

## <a name="git-changes-window"></a>Finestra modifiche git

Git tiene traccia delle modifiche apportate ai file nel repository mentre si lavora e separa i file del repository in tre categorie. Queste modifiche sono equivalenti a quanto visualizzato quando si immette il `git status` comando nella riga di comando:

- **File non modificati**: questi file non sono stati modificati dopo l'ultimo commit.
- **File modificati**: questi file presentano modifiche rispetto all'ultimo commit, ma non sono stati ancora gestiti per il commit successivo.
- **File** di gestione temporanea: questi file contengono modifiche che verranno aggiunte al commit successivo.

Quando si esegue il lavoro, Visual Studio tiene traccia delle modifiche apportate ai file nel progetto nella sezione **modifiche** della finestra **modifiche git** .

:::image type="content" source="media/git-changes-window.png" alt-text="La finestra git changes in Visual Studio.":::

Quando si è pronti per la gestione temporanea delle modifiche, fare clic sul **+** pulsante (segno più) in ogni file che si desidera inserire in una fase oppure fare clic con il pulsante destro del mouse su un file e scegliere **fase**. È anche possibile organizzare tutti i file modificati con un solo clic usando il pulsante staging All **+** (più) nella parte superiore della sezione **changes** .

Quando si esegue il staging di una modifica, Visual Studio crea una sezione di modifiche di gestione **temporanea** . Al commit successivo verranno aggiunte solo le modifiche apportate alla sezione modifiche di gestione **temporanea** . a tale scopo, è possibile selezionare **commit** staging. È anche possibile non installare le modifiche facendo clic sul pulsante **–** (meno). Il comando equivalente per questa azione è `git commit -m "Your commit message"` .

È anche possibile scegliere di non organizzare i file modificati ignorando l'area di gestione temporanea. In questo caso, Visual Studio consente di eseguire il commit delle modifiche direttamente senza doverle organizzare. È sufficiente immettere il messaggio di commit e quindi selezionare **commit tutti**. Il comando equivalente per questa azione è `git commit -a` .

Visual Studio semplifica anche il commit e la sincronizzazione con un solo clic usando i collegamenti **commit tutti e push** e **commit tutti e sincronizza** . Quando si fa doppio clic su un file nelle sezioni **modifiche** e **modifiche** di gestione temporanea, è possibile visualizzare un confronto riga per riga con la versione non modificata del file.

:::image type="content" source="media/git-file-version-compare.png" alt-text="Confronto riga per riga di versioni di file in Visual Studio ":::

> [!TIP]
> È possibile associare un elemento di lavoro di Azure DevOps a un commit usando il carattere "#" Se si è connessi al repository DevOps di Azure. È possibile connettere il repository di Azure DevOps tramite **Team Explorer**  >  **gestire le connessioni**.

### <a name="select-an-existing-branch"></a>Selezionare un ramo esistente

Visual Studio Visualizza il Current Branch nel selettore nella parte superiore della finestra delle **modifiche di git** .

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="I rami correnti che è possibile visualizzare usando il selettore nella parte superiore del selettore delle modifiche di Git in Visual Studio ":::

Current Branch è disponibile anche nella barra di stato nell'angolo inferiore destro dell'IDE di Visual Studio.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Rami correnti che è possibile visualizzare usando la barra di stato nell'angolo inferiore destro dell'IDE di Visual Studio ":::

Da entrambe le posizioni, è possibile passare da un ramo esistente all'altra.

### <a name="create-a-new-branch"></a>Creare un nuovo ramo

È anche possibile creare un nuovo ramo. Il comando equivalente per questa azione è `git checkout <branchname>` .

La creazione di un nuovo ramo è semplice come immettere il nome del ramo e basarlo su un ramo esistente.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Finestra di dialogo Crea un nuovo ramo in Visual Studio ":::

È possibile scegliere un ramo locale o remoto esistente come base. La casella di controllo **checkout Branch** passa automaticamente al ramo appena creato. Il comando equivalente per questa azione è `git checkout -b <new-branch><existing-branch>` .

## <a name="git-repository-window"></a>Finestra del repository git

Visual Studio include una nuova finestra del **repository git** , che è una visualizzazione consolidata di tutti i dettagli nel repository, inclusi tutti i rami, le cronologie e le cronologie di commit. È possibile accedere a questa finestra direttamente da **git** o dalla **visualizzazione** sulla barra dei menu o dalla barra di stato.

### <a name="manage-branches"></a>Gestisci rami

Quando si seleziona **Gestisci rami** dal menu **git** , viene visualizzata la visualizzazione albero rami nella finestra del **repository git** . Dal riquadro sinistro è possibile utilizzare il menu di scelta rapida per estrarre i rami, creare nuovi Branch, unire, riassegnare, cherry-pick e altro ancora. Quando si fa clic sul ramo, è possibile visualizzare un'anteprima della cronologia dei commit nel riquadro di destra.

### <a name="incoming-and-outgoing-commits"></a>Commit in ingresso e in uscita

Quando si recupera un ramo, la finestra **modifiche git** presenta un indicatore sotto l'elenco a discesa Branch, che Visualizza il numero di commit estratti dal ramo remoto. Questo indicatore mostra anche il numero di commit locali non sottoposto a push.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="La finestra modifiche git che mostra l'elemento dell'interfaccia utente a discesa indicatore in Visual Studio ":::

L'indicatore funziona anche come collegamento per passare alla cronologia di commit del branch nella finestra del **repository git** . Nella parte superiore della cronologia ora vengono visualizzati i dettagli di questi commit in ingresso e in uscita. Da qui è anche possibile scegliere di eseguire il pull o il push dei commit.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Finestra del repository git che mostra la cronologia dei commit di un ramo in Visual Studio ":::

#### <a name="commit-details"></a>Dettagli commit

Quando si fa doppio clic su un **commit**, Visual Studio apre i dettagli in una finestra degli strumenti separata. Da qui è possibile ripristinare il commit, reimpostare il commit, modificare il messaggio di commit o creare un tag nel commit. Quando si fa clic su un file modificato nel commit, Visual Studio apre la visualizzazione delle **differenze** affiancata del commit e del relativo elemento padre.

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Finestra di dialogo Dettagli commit in Visual Studio ":::

## <a name="handle-merge-conflicts"></a>Gestione dei conflitti di merge

Possono verificarsi conflitti durante un'operazione di merge se due sviluppatori modificano le stesse righe in un file e git non sa automaticamente quale sia la correttezza. Git interrompe l'Unione e informa che l'utente si trova in uno stato di conflitto.

Visual Studio semplifica l'identificazione e la risoluzione di un conflitto di merge. In primo luogo, la finestra del **repository git** Mostra una barra delle informazioni in oro nella parte superiore della finestra.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Messaggio &quot;merge completato con conflitti&quot; in Visual Studio ":::

La finestra **modifiche git** Visualizza anche un messaggio "*merge is in progress with Conflicts*", con i file non Uniti nella relativa sezione separata sotto.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Messaggio &quot;Unione in corso con conflitti&quot; in Visual Studio ":::

Tuttavia, se non si dispone di queste finestre aperte e si passa al file con conflitti di merge, non sarà necessario cercare il testo seguente:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Al contrario, Visual Studio Visualizza una barra informazioni in oro nella parte superiore della pagina che indica che il file aperto presenta conflitti. Quindi, è possibile fare clic sul collegamento per aprire l' **editor di merge**.

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Screenshot del messaggio ' file contains Merge Conflicts ' in Visual Studio ":::

### <a name="the-merge-editor"></a>Editor di merge

L'editor di merge in Visual Studio è uno strumento di merge a tre vie che visualizza le modifiche in ingresso, le modifiche correnti e il risultato dell'Unione. È possibile utilizzare la barra degli strumenti nel livello superiore dell' **editor di merge** per spostarsi tra i conflitti e le differenze di Unione automatica nel file.

:::image type="content" source="media/git-merge-editor.png" alt-text="Editor di merge in Visual Studio ":::

È anche possibile usare gli interruttori per visualizzare/nascondere le differenze, visualizzare/nascondere le differenze di parola e personalizzare il layout. Sono presenti caselle di controllo nella parte superiore di ogni lato che è possibile usare per eseguire tutte le modifiche da un lato o l'altro. Tuttavia, per modificare le singole modifiche, è possibile fare clic sulle caselle di controllo a sinistra delle righe in conflitto su entrambi i lati. Infine, al termine della risoluzione dei conflitti, è possibile selezionare il pulsante **accetta merge** nell'editor di merge. Si scrive quindi un messaggio di commit e si esegue il commit delle modifiche per completare la risoluzione.

## <a name="personalize-your-git-settings"></a>Personalizzare le impostazioni git

Per personalizzare e personalizzare le impostazioni git a livello di repository e a livello globale, passare a **git**  >  **Settings** sulla barra dei menu o a **strumenti**  >  **Opzioni**  >  **controllo del codice sorgente** sulla barra dei menu. Scegliere quindi le opzioni desiderate.

:::image type="content" source="media/git-options-settings.png" alt-text="La finestra di dialogo Opzioni in cui è possibile scegliere le impostazioni di personalizzazione e personalizzazione nell'IDE di Visual Studio ":::

## <a name="how-to-use-the-legacy-team-explorer-experience-in-visual-studio"></a>Come usare l'esperienza Team Explorer legacy in Visual Studio

La nuova esperienza git è il sistema di controllo della versione predefinito in Visual Studio 2019 dalla [versione 16,8](/visualstudio/releases/2019/release-notes/) e successive. Tuttavia, se si desidera disattivarla, è possibile. Passare a **strumenti**  >  **Opzioni**  >  **ambiente**  >  **Anteprima funzionalità** e quindi attivare o disattivare la casella di controllo **nuova esperienza utente git** , che consente di tornare all'esperienza Team Explorer legacy.

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Sezione funzionalità di anteprima della finestra di dialogo Opzioni in Visual Studio ":::

## <a name="whats-next"></a>Passaggi successivi

Anche se la nuova esperienza git è ora attiva per impostazione predefinita in Visual Studio 2019 [versione 16,8](/visualstudio/releases/2019/release-notes/), continuiamo ad aggiungere nuove funzionalità per migliorare l'esperienza. Per estrarre nuovi aggiornamenti per l'esperienza git in una versione di anteprima, è possibile scaricarli e installarli dalla pagina di anteprima di [Visual Studio](https://aka.ms/vspreview/) .

> [!IMPORTANT]
> Se si ha un suggerimento per Microsoft, è possibile inviarlo. Ci rendiamo conto dell'opportunità di partecipare alle decisioni di progettazione tramite il portale della [**community degli sviluppatori**](https://aka.ms/vs-suggest) .

## <a name="see-also"></a>Vedere anche

- [Annuncio del rilascio dell'esperienza git nel post di Blog di Visual Studio](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/)
- [Il lancio della nuova esperienza git](https://www.youtube.com/watch?v=UHrAg3iKoe0&t) su YouTube
- [La serie di strumenti di Visual Studio presenta: il nuovo video sull'esperienza git](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) su Channel 9 e su [YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be)
- [Nuovi aggiornamenti interessanti per l'esperienza git nel](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/) post di Blog di Visual Studio
- [Esperienza git migliorata nel post di Blog di Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)
- [Utilizzare gli account GitHub in Visual Studio](work-with-github-accounts.md)
- [Note sulla versione di Visual Studio 2019](/visualstudio/releases/2019/release-notes)
