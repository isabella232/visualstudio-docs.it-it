---
title: Impostazioni Git in Visual Studio
titleSuffix: ''
description: Informazioni su Visual Studio i file con estensione gitconfig e le impostazioni Git per gestire le preferenze
ms.date: 06/08/2021
ms.topic: conceptual
ms.author: prnadago
author: prnadago
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.manager: jmartens
monikerRange: '>=vs-2019'
ms.openlocfilehash: 5a92d27aa170afe365b878368bc32599bfe87030aacf5ef15fe3ef056b8d19e2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121226978"
---
# <a name="git-settings-and-preferences-in-visual-studio"></a>Impostazioni e preferenze git in Visual Studio

In Visual Studio è possibile configurare e visualizzare le impostazioni e le preferenze git comuni, ad esempio il nome e l'indirizzo di posta elettronica, gli strumenti preferiti per diff e merge e altro ancora. Queste impostazioni e preferenze possono essere  visualizzate e configurate nella finestra di dialogo Opzioni nella pagina Git **Global Impostazioni** (si applica a tutti i repository) o nella pagina Git **Repository Impostazioni** (si applica al repository corrente).

È possibile configurare due tipi di impostazioni:

- [Impostazioni Git:](#git-settings) le impostazioni in questa sezione corrispondono alle impostazioni Git salvate nei file di configurazione Git. Queste impostazioni possono essere visualizzate e modificate in Visual Studio, ma sono gestite dai file di configurazione Git.
- [Visual Studio impostazioni:](#visual-studio-settings) le impostazioni in questa sezione configurano le impostazioni e le preferenze correlate a Git gestite da Visual Studio.

## <a name="how-to-configure-settings"></a>Come configurare le impostazioni

1. Per configurare le impostazioni Git Visual Studio, scegliere **Impostazioni** dal menu Git di primo livello.

   :::image type="content" source="media/git-menu-settings.png" alt-text="Menu Git con un callout al Impostazioni comando.":::

2. Scegliere **Git Global Impostazioni** o Git Repository **Impostazioni** visualizzare e configurare le impostazioni a livello globale o a livello di repository.

   :::image type="content" source="media/source-control-settings.png" alt-text="Riquadro di spostamento nella finestra di dialogo Opzioni con un callout per le impostazioni Git.":::

3. È possibile configurare diverse impostazioni Git comuni, come descritto nelle sezioni seguenti di questo articolo. Dopo aver configurato le impostazioni desiderate, selezionare **OK** per salvare le impostazioni aggiornate.

   :::image type="content" source="media/ok-button.png" alt-text="Area di visualizzazione della finestra di dialogo Opzioni con un callout per il pulsante OK.":::

## <a name="git-settings"></a>Impostazioni git

È anche possibile configurare e controllare alcune delle impostazioni di configurazione Git più comuni. È possibile visualizzare e modificare le impostazioni seguenti in Visual Studio, anche se sono gestite da file di configurazione Git.

- [Nome e indirizzo di posta elettronica](#name-and-email)
- [Eliminare rami remoti durante il recupero](#prune-remote-branches-during-fetch)
- [Riasserzione del ramo locale durante il pull](#rebase-local-branch-when-pulling)
- [Provider di rete crittografica](#cryptographic-network-provider)
- [Helper credenziali](#credential-helper)
- [Strumenti di unione & diff](#diff--merge-tools)
- [File Git](#git-files)
- [Telecomandi](#remotes)
- [Altre impostazioni](#other-settings)

>[!NOTE]
>Le impostazioni Git configurate nel Impostazioni globale **di Visual Studio** corrispondono alle impostazioni nel file di configurazione specifico dell'utente di Git e le impostazioni in Repository **Impostazioni** corrispondono alle impostazioni nel file di configurazione specifico del repository. Per altre informazioni sulla configurazione di Git, vedere il capitolo Pro Git sulla personalizzazione di [Git,](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration)la documentazione di [git-config](https://git-scm.com/docs/git-config)e le informazioni di riferimento su Git Pro sui file [di configurazione.](https://git-scm.com/docs/git-config#FILES) Per configurare le impostazioni Git non esposte in Visual Studio, usare il comando per `git config` scrivere un valore nei file di configurazione: `git config [--local|--global|--system] section.key value` .

### <a name="name-and-email"></a>Nome e indirizzo di posta elettronica

Il nome e il messaggio di posta elettronica forniti verranno usati come informazioni sul commit per qualsiasi commit eseguito. Questa impostazione è disponibile sia nell'ambito globale che in quello del repository e corrisponde alle impostazioni user.name `git config` [](https://git-scm.com/docs/git-config#Documentation/git-config.txt-username) e [user.email](https://git-scm.com/docs/git-config#Documentation/git-config.txt-useremail) predefinite.

1. Dal menu Git passare a **Impostazioni**. Per impostare il nome utente e l'indirizzo di posta elettronica a livello globale, passare a **Git Global Impostazioni**; Per impostare il nome utente e l'indirizzo di posta elettronica a livello di repository, passare a **Repository Git Impostazioni**.

2. Specificare il nome utente e l'indirizzo di posta elettronica, quindi **scegliere OK** per salvare. 

   :::image type="content" source="media/user-email-setting.png" alt-text="Riquadro Impostazioni globali Git nella finestra di dialogo Opzioni con un callout per l'invio di un messaggio di posta elettronica a un nome utente.":::

### <a name="prune-remote-branches-during-fetch"></a>Eliminare rami remoti durante il recupero

L'eliminazione rimuove i rami di rilevamento remoto che non esistono più nel computer remoto e consente di mantenere pulito e aggiornato l'elenco dei rami. Questa impostazione è disponibile sia nell'ambito globale che in quello del repository e corrisponde `git config` [all'impostazione fetch.prune.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-fetchprune)

È consigliabile impostare questa opzione **su True** a livello globale. Le impostazioni valide sono le seguenti:

- True (scelta consigliata)
- Falso
- Non impostato (impostazione predefinita)

1. Dal menu Git passare a **Impostazioni**. Passare a **Git Global Impostazioni** per configurare questa opzione a livello globale. Passare a **Git Repository Impostazioni** per configurare questa opzione a livello di repository.

2. Impostare **Eliminare i rami remoti durante il recupero** su **True** (scelta consigliata). Selezionare **OK** per salvare.

:::image type="content" source="media/prune-setting.png" alt-text="Screenshot che mostra l'opzione &quot;Elimina rami remoti durante il recupero&quot; evidenziata e con l'opzione &quot;True&quot; selezionata nell'elenco a discesa.":::    

### <a name="rebase-local-branch-when-pulling"></a>Riasserzione del ramo locale durante il pull

La riasserzione riserva le modifiche apportate dai commit nel ramo corrente che non si trova nel ramo upstream, reimposta il ramo corrente sul ramo upstream, quindi applica le modifiche che sono state accantonati. Questa impostazione è disponibile sia nell'ambito globale che in quello del repository e corrisponde `git config` [all'impostazione pull.rebase.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-pullrebase) Le impostazioni valide sono le seguenti:

- True: riasssazione di Current Branch sul ramo upstream dopo il recupero.
- False: unisce il ramo corrente nel ramo upstream.
- Non impostato (impostazione predefinita): se non specificato in altri file di configurazione, unire il ramo corrente nel ramo upstream.
- Interattivo: riassseri in modalità interattiva.
- Mantieni: eseguire la riasserzione senza appiattire i commit di merge creati localmente.

1. Dal menu Git passare a **Impostazioni**. Passare a **Git Global Impostazioni** per configurare questa opzione a livello globale. Passare a **Git Repository Impostazioni** per configurare questa opzione a livello di repository.

2. Impostare **Rebase local branch (Ribase** ramo locale) quando si esegue il pull dell'impostazione desiderata e selezionare **OK** per salvare.

    :::image type="content" source="media/rebase-setting.png" alt-text="Screenshot che mostra 'Rebase local branch when pulling' evidenziato e 'True' selezionato dall'elenco a discesa.":::

Non è possibile configurare `pull.rebase` l'impostazione **Interattiva** in Visual Studio. Visual Studio non dispone del supporto interattivo per la riabase.
Per configurare `pull.rebase` per l'uso della modalità interattiva, usare la riga di comando.

### <a name="cryptographic-network-provider"></a>Provider di rete crittografica

Il provider di rete crittografica è un'impostazione di configurazione Git in ambito globale che configura il back-end TLS/SSL da usare in fase di esecuzione e corrisponde `git config` [all'impostazione http.sslBackend.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-httpsslBackend) I valori sono i seguenti:

- OpenSSL: usare [OpenSSL per](https://www.openssl.org/) i protocolli TLS e SSL.
- Canale sicuro: usare [il canale sicuro (schannel)](/windows/win32/secauthn/secure-channel) per i protocolli TLS e SSL. Schannel è la soluzione Windows nativa, che accede al Windows Credential Store, consentendo in tal modo la gestione dei certificati a livello aziendale.
- Non impostato (impostazione predefinita): se questa impostazione non è impostata, OpenSSL è l'impostazione predefinita.

1. Dal menu Git passare a **Impostazioni**. Passare a **Git Global Impostazioni** per configurare questa impostazione.

2. Impostare **Provider di rete crittografica** sul valore desiderato e selezionare OK **per** salvare.

   :::image type="content" source="media/network-provider-setting.png" alt-text="Screenshot che mostra l'opzione &quot;Provider di rete crittografica&quot; evidenziata con l'opzione &quot;OpenSSL&quot; selezionata nell'elenco a discesa.":::

### <a name="credential-helper"></a>Helper credenziali

Quando Visual Studio esegue un'operazione Git remota, l'endpoint remoto potrebbe rifiutare la richiesta perché richiede che le credenziali siano fornite con la richiesta. A quel punto, Git richiama un helper credenziali, che restituirà le credenziali necessarie per eseguire l'operazione e quindi proverà di nuovo la richiesta. L'helper credenziali usato corrisponde `git config` [all'impostazione credential.helper.](https://git-scm.com/docs/gitcredentials) È disponibile nell'ambito globale con i valori seguenti:

- GCM per Windows: usare [Git Gestione credenziali per Windows](https://github.com/microsoft/Git-Credential-Manager-for-Windows) come helper.
- GCM Core: usare [Git Gestione credenziali Core](https://github.com/microsoft/Git-Credential-Manager-Core) come helper.
- Non impostato (impostazione predefinita): se questa impostazione non è impostata, viene usato l'helper credenziali impostato nella configurazione di sistema. A livello di Git per Windows 2.29, l'helper credenziali predefinito è GCM Core.

1. Dal menu Git passare a **Impostazioni**. Passare a **Git Global Impostazioni** per configurare questa impostazione.

2. Impostare **Helper credenziali** sul valore desiderato e selezionare **OK** per salvare.

:::image type="content" source="media/credential-helper-setting.png" alt-text="Screenshot che mostra l'impostazione dell'helper credenziali nella finestra di dialogo Opzioni.":::

### <a name="diff--merge-tools"></a>Strumenti di unione & diff

Git mostrerà le diff e i conflitti di unione negli strumenti preferiti. Le impostazioni in questa sezione corrispondono alle `git config` [impostazioni diff.tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) [e merge.tool.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool) È possibile configurare Git per l'uso di Visual Studio come strumento di unione o diff in **Git Global Impostazioni** e git repository **Impostazioni** selezionando **Usa** Visual Studio . Per configurare altri strumenti diff e merge, usare `git config` con [l'opzione diff.tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) [o merge.tool.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool)

:::image type="content" source="media/tools-setting.png" alt-text="Screenshot che mostra la sezione per impostare lo strumento Diff predefinito e lo strumento Merge nella finestra di dialogo Opzioni.":::

### <a name="git-files"></a>File Git

È possibile usare la **sezione File Git** nell'ambito del repository Git **Impostazioni** per visualizzare e modificare i file [gitignore](https://git-scm.com/docs/gitignore) e [gitattributes](https://git-scm.com/docs/gitattributes) per il repository.

:::image type="content" source="media/git-files-setting.png" alt-text="Screenshot che mostra la sezione per visualizzare e modificare i file Ignore e attributes nel repository.":::

### <a name="remotes"></a>Telecomandi

È possibile usare il **riquadro Remotes** in **Git Repository Impostazioni** per configurare i remoti per il repository. Questa impostazione corrisponde al [comando remoto git](https://git-scm.com/docs/git-remote) e consente di aggiungere, modificare o rimuovere i remoti.

:::image type="content" source="media/remotes-settings.png" alt-text="Screenshot che mostra il riquadro Git Remotes nella finestra di dialogo Opzioni.":::

### <a name="other-settings"></a>Altre impostazioni

Per visualizzare tutte le altre impostazioni di configurazione git, è possibile aprire e visualizzare i file di configurazione oppure eseguire per `git config --list` visualizzare le impostazioni.

## <a name="visual-studio-settings"></a>Impostazioni di Visual Studio

Le impostazioni seguenti gestiscono le preferenze correlate a Git in Visual Studio e vengono gestite da Visual Studio anziché dai file di configurazione Git. Tutte le impostazioni in questa sezione sono configurate nella pagina **Git Global Impostazioni.**

- [Percorso predefinito](#default-location)
- [Chiudere le soluzioni aperte non in Git all'apertura di un repository](#close-open-solutions-not-under-git-when-opening-a-repository)
- [Abilitare il download di immagini di creazione da origini di terze parti](#enable-download-of-author-images-from-third-party-sources)
- [Eseguire il commit delle modifiche dopo l'unione per impostazione predefinita](#commit-changes-after-merge-by-default)
- [Abilitare push --force](#enable-push---force-with-lease)
- [Aprire una cartella in Esplora soluzioni all'apertura di un repository Git](#open-folder-in-solution-explorer-when-opening-a-git-repository)
- [Caricare automaticamente la soluzione all'apertura di un repository Git](#automatically-load-the-solution-when-opening-a-git-repository)
- [Estrarre automaticamente i rami con doppio clic o invio](#automatically-check-out-branches-with-double-click-or-the-enter-key)

### <a name="default-location"></a>Posizione predefinita

**Percorso predefinito** configura la cartella predefinita in cui vengono clonati i repository.

:::image type="content" source="media/default-location-setting.png" alt-text="Screenshot che mostra il campo percorso predefinito nella finestra di dialogo Opzioni.":::

### <a name="close-open-solutions-not-under-git-when-opening-a-repository"></a>Chiudere le soluzioni aperte non in Git all'apertura di un repository

Per impostazione predefinita, Visual Studio qualsiasi soluzione o cartella aperta quando si passa a un altro repository. In questo caso, potrebbe anche caricare la soluzione o la cartella del nuovo repository in base a se si sceglie Apri cartella in Esplora soluzioni all'apertura di un [repository Git](#open-folder-in-solution-explorer-when-opening-a-git-repository) e Carica automaticamente la soluzione all'apertura di un repository [Git](#automatically-load-the-solution-when-opening-a-git-repository). In questo modo viene mantenuta la coerenza tra il codice aperto e il repository aperto. Tuttavia, se la soluzione non si trova nella stessa radice della cartella del repository, è possibile mantenere aperta la soluzione quando si passa al relativo repository. È possibile eseguire questa operazione con questa impostazione. I valori sono i seguenti:

- Sì: quando viene aperto un repository, la soluzione attualmente aperta viene sempre chiusa
- No: quando viene aperto un repository, Visual Studio un controllo per verificare se la soluzione corrente si trova in Git. In caso contrario, la soluzione rimane aperta.
- Chiedi sempre (impostazione predefinita): quando questa opzione è impostata, è possibile effettuare una scelta tramite una finestra di dialogo per ogni repository aperta, indipendentemente dal fatto che la soluzione corrente sia aperta o chiusa.

:::image type="content" source="media/close-sln-setting.png" alt-text="Screenshot che mostra l'impostazione chiudi soluzione nella finestra di dialogo Opzioni.":::


### <a name="enable-download-of-author-images-from-third-party-sources"></a>Abilitare il download di immagini di creazione da origini di terze parti

Abilitare il download di immagini di autore da origini di terze parti è Visual Studio'impostazione specifica per l'ambito globale. Se l'opzione è selezionata, le immagini di creazione vengono scaricate dal servizio immagini [Gravatar,](https://en.gravatar.com/)se disponibile, e visualizzate nelle visualizzazioni di commit e cronologia.

:::image type="content" source="media/download-image-setting.png" alt-text="Screenshot che mostra la casella di controllo per abilitare il download delle immagini dell'autore da un'origine di terze parti nella finestra di dialogo Opzioni. ":::

>[!IMPORTANT]
>Per fornire immagini di autore nelle visualizzazioni Commit e Cronologia, lo strumento crea un hash MD5 per gli indirizzi di posta elettronica dell'autore archiviati nel repository attivo. Questo hash viene quindi inviato a Gravatar per trovare un valore hash corrispondente per gli utenti che si sono registrati in precedenza per il servizio. Se viene trovata una corrispondenza, l'immagine utente verrà recuperata dal servizio e visualizzata in Visual Studio. Gli utenti che non hanno configurato il servizio restituiranno un'immagine generata in modo casuale. Si noti che gli indirizzi di posta elettronica non vengono registrati da Visual Studio, né vengono mai condivisi con Gravatar o altre terze parti.

### <a name="commit-changes-after-merge-by-default"></a>Eseguire il commit delle modifiche dopo l'unione per impostazione predefinita

Quando **l'opzione Commit changes after merge (Commit** modifiche dopo l'unione) è abilitata per impostazione predefinita, Git crea automaticamente un nuovo commit quando un ramo viene unito al ramo corrente.

:::image type="content" source="media/merge-commit-setting.png" alt-text="Screenshot che mostra la casella di controllo per eseguire il commit delle modifiche dopo l'unione per impostazione predefinita nella finestra di dialogo Opzioni.":::

- Se selezionata, `git merge` i comandi emessi Visual Studio vengono eseguiti con `--commit` l'opzione .
- Se deselezionata, `git merge` i comandi emessi Visual Studio vengono eseguiti con le `--no-commit --no-ff` opzioni .

Per altre informazioni su queste opzioni, vedere [--commit e --no-commit](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---commit) e [--no-ff](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---no-ff).

### <a name="enable-push---force-with-lease"></a>Abilitare push --force-with-lease

Se abilitata, questa impostazione consente di `push --force-with-lease` eseguire questa operazione dall'interno Visual Studio. Per impostazione **predefinita, l'opzione Abilita push --force-with-lease** è disabilitata.

:::image type="content" source="media/push-force-setting.png" alt-text="Screenshot che mostra la casella di controllo per abilitare la forza push con lease nella finestra di dialogo Opzioni.":::

Per altre informazioni, vedere [push --force-with-lease](https://git-scm.com/docs/git-push#Documentation/git-push.txt---no-force-with-lease).

### <a name="open-folder-in-solution-explorer-when-opening-a-git-repository"></a>Aprire una cartella in Esplora soluzioni all'apertura di un repository Git
<!-- todo: write section -->
Quando si usa Visual Studio per aprire o passare a un repository Git, Visual Studio carica il contenuto Git in modo da poter visualizzare modifiche, commit, rami e gestire il repository dall'IDE. Inoltre, Visual Studio anche il codice del repository in Esplora soluzioni. Visual Studio la cartella del repository alla ricerca di soluzioni, CMakeLists.txt o qualsiasi altro file di visualizzazione riconosciuto e visualizzato come elenco in Esplora soluzioni. Da qui è possibile selezionare una soluzione da caricare o la cartella per visualizzare il contenuto della directory. Quando si disattiva questa casella di controllo, Visual Studio la cartella del repository non verrà aperta in Esplora soluzioni. Ciò consentirà essenzialmente di aprire il Visual Studio solo come gestore di repository Git. Questa impostazione è attiva per impostazione predefinita.

:::image type="content" source="media/open-folder-setting.png" alt-text="Screenshot che mostra la casella di controllo per aprire la cartella quando si apre un repository Git nella finestra di dialogo Opzioni.":::

### <a name="automatically-load-the-solution-when-opening-a-git-repository"></a>Caricare automaticamente la soluzione all'apertura di un repository Git

Questa impostazione è applicabile solo quando [l'impostazione Apri cartella in Esplora soluzioni all'apertura](#open-folder-in-solution-explorer-when-opening-a-git-repository) di un repository Git è attivata. Quando si apre un repository Git in Visual Studio e l'analisi delle cartelle successiva rileva che è presente una sola soluzione nel repository, Visual Studio carica automaticamente la soluzione. Se si disattiva l'impostazione, il Esplora soluzioni visualizza la singola soluzione presente nel repository nell'elenco di visualizzazioni. Ma non carica la soluzione. Per impostazione predefinita, questa impostazione è disattivata.

:::image type="content" source="media/load-solution-setting.png" alt-text="Screenshot che mostra la casella di controllo per caricare automaticamente la soluzione all'apertura di un repository Git nella finestra di dialogo Opzioni.":::

### <a name="automatically-check-out-branches-with-double-click-or-the-enter-key"></a>Estrarre automaticamente i rami con un doppio clic o il tasto INVIO

La finestra Repository Git include un elenco di rami visualizzati in una struttura ad albero. Se si seleziona un ramo, il riquadro cronologia commit verrà commutato per visualizzare i commit per il ramo selezionato. Per estrarre un ramo, è possibile fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida e scegliere **Checkout (Checkout).** Se si attiva questa impostazione, facendo doppio clic o premendo INVIO si estrarrà il ramo e ne verranno visualizzati i commit. 
  
:::image type="content" source="media/checkout-branch-setting.png" alt-text="Screenshot che mostra la casella di controllo per estrarre i rami con doppio clic o invio nella finestra di dialogo Opzioni.":::


## <a name="see-also"></a>Vedi anche

> [!IMPORTANT]
> Se hai un suggerimento per Microsoft, inviaci un suggerimento. È molto apprezzata l'opportunità di interagire con l'utente in base alle decisioni di progettazione tramite il portale [**Community**](https://aka.ms/vsgitsuggestions) developer.

- [Informazioni di base con Git e GitHub nell'esercitazione Visual Studio](/learn/modules/visual-studio-github-push/) su Microsoft Learn
- Video [Introduzione a Git in Visual Studio](https://www.youtube.com/watch?v=GCZ9x3yqkyc) su YouTube
- [Miglioramento della produttività con Git nel](https://devblogs.microsoft.com/visualstudio/enhanced-productivity-with-git-in-visual-studio/) post Visual Studio blog
- [Opzioni (finestra di dialogo)](../ide/reference/options-dialog-box-visual-studio.md)
