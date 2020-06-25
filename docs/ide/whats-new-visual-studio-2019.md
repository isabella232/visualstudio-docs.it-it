---
title: Novità di Visual Studio 2019
titleSuffix: ''
description: Informazioni sulle nuove funzionalità di Visual Studio 2019.
ms.date: 05/20/2020
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 6b5058e0f1fabbf834a1adfb20d4f3a9a11094f5
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283593"
---
# <a name="whats-new-in-visual-studio-2019"></a>Novità di Visual Studio 2019

**Aggiornamento per la [versione 16,6](/visualstudio/releases/2019/release-notes/)**

>[!div class="button"]
>[Scarica Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

Visual Studio è in continua evoluzione per soddisfare le esigenze degli sviluppatori. Nel video seguente della **[Microsoft Build](https://mybuild.microsoft.com/)** Library partecipa a una presentazione di alcune delle [funzionalità più recenti](/visualstudio/releases/2019/release-notes/) e a una [sbirciatina](/visualstudio/releases/2019/release-notes-preview/) in merito alle novità: <br><br>*Lunghezza video: 44,58 minuti*

> [!VIDEO https://channel9.msdn.com/Events/Build/2020/BOD111/player]

Visual Studio 2019 include gli strumenti e i servizi migliori del settore per qualsiasi sviluppatore, app e piattaforma. Che tu stia usando Visual Studio per la prima volta o che sei stato usato per anni, la versione più recente è molto simile.

Di seguito è riportato un riepilogo generale delle novità, tutte:

* **[Sviluppo](#develop)**: rimanere concentrati e produttivi con migliori prestazioni, pulizia immediata del codice e risultati di ricerca migliori.
* **[Collaborare](#collaborate)**: sfruttare la collaborazione naturale tramite un flusso di lavoro git-First, la modifica e il debug in tempo reale e le revisioni del codice direttamente in Visual Studio.
* **[Debug](#debug)**: evidenziare e passare a valori specifici, ottimizzare l'uso della memoria e creare snapshot automatici dell'esecuzione dell'applicazione.

Per un elenco completo di tutte le novità in questa versione, vedere le [note sulla versione](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Sviluppo

Vedere il video seguente per altre informazioni su come è possibile risparmiare tempo con le nuove funzionalità. <br><br>*Lunghezza video: 3,00 minuti*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Miglioramento della ricerca

Precedentemente nota come Avvio veloce, la nuova esperienza di ricerca è più rapida ed efficiente. Ora i risultati della ricerca vengono visualizzati dinamicamente durante la digitazione. Possono anche spesso includere tasti di scelta rapida per i comandi, in modo da poterli memorizzare più facilmente per usarli in futuro.

   ![Animazione della nuova esperienza di ricerca in Visual Studio 2019](media/vs-2019/new-search-feature.gif)

La nuova logica di ricerca fuzzy consentirà di trovare tutto quello che serve, anche se sono presenti errori di digitazione. Indipendentemente dal fatto che si stiano cercando comandi, impostazioni, documentazione o altri elementi utili, la nuova funzionalità di ricerca rende più semplice trovare quello che si sta cercando.

### <a name="refactorings"></a>Refactoring

Esistono molti refactoring nuovi ed estremamente utili in C# che rendono più semplice organizzare il codice. Vengono visualizzati come suggerimenti nella lampadina e includono azioni, ad esempio lo spostamento di membri in un'interfaccia o una classe di base, l'adattamento degli spazi dei nomi alla struttura delle cartelle, la conversione dei cicli foreach per le query Linq e altro ancora.

   ![Animazione dell'esperienza di refactoring in Visual Studio 2019](media/vs-2019/refactorings.gif)

È sufficiente richiamare i refactoring premendo **CTRL+.** e selezionando l'azione che si vuole eseguire.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) ottimizza le attività di sviluppo software con l'uso dell'intelligenza artificiale. IntelliCode esegue il training tra 2000 progetti open source su GitHub&mdash;ognuno con oltre 100 stelle&mdash;per generare raccomandazioni.

![Animazione di IntelliCode in Visual Studio 2019](media/vs-2019/IntelliCode.gif)

Ecco alcuni modi in cui Visual Studio IntelliCode può essere utile per migliorare la produttività:

* Completamento del codice con riconoscimento del contesto
* Guida per gli sviluppatori per il rispetto dei criteri e degli stili usati dal team
* Individuazione di problemi del codice difficili da trovare
* Revisioni del codice mirate, che pongono al centro dell'attenzione le aree realmente importanti

Per la versione di anteprima di IntelliCode come estensione per Visual Studio era stato inizialmente previsto solo il supporto per C#. Ora, come **novità della versione 16.1**, è stato aggiunto il supporto per C# e XAML come predefinito. (Il supporto per C++ e TypeScript/JavaScript sono, tuttavia, ancora in anteprima.)

Per chi usa C#, è stata inoltre aggiunta la possibilità di eseguire il training di un modello personalizzato nel proprio codice.

Per altre informazioni su IntelliCode, vedere i post di blog [Announcing the general availability of IntelliCode plus a sneak peek](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) (Annuncio della disponibilità generale di IntelliCode più un assaggio) e [Code more, scroll less with Visual Studio IntelliCode ](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) (Scrivere più codice e scorrere meno con Visual Studio IntelliCode).

### <a name="code-cleanup"></a>Pulizia del codice

Abbinato a un nuovo indicatore di integrità dei documenti è disponibile un nuovo comando per la pulizia del codice. È possibile usare questo nuovo comando per identificare e quindi risolvere avvisi e suggerimenti con il semplice clic di un pulsante.

L'operazione di pulizia formatterà il codice e applicherà eventuali correzioni del codice come suggerito dalle [impostazioni correnti](code-styles-and-code-cleanup.md) e dai [file con estensione editorconfig](create-portable-custom-editor-options.md).

   ![Screenshot del nuovo controllo di pulizia del codice in Visual Studio 2019](media/vs-2019/code-cleanup-profile.png)

È anche possibile salvare raccolte di utilità di correzione come profilo. Ad esempio, se si applica di frequente un piccolo set di utilità di correzione specifiche durante la scrittura del codice e poi si usa un altro set completo di utilità di correzione da applicare prima di una revisione del codice, è possibile configurare due profili per queste attività diverse.

   ![Screenshot del controllo di configurazione della pulizia del codice in Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png)

### <a name="per-monitor-aware-pma-rendering"></a>Rendering sensibile ai valori del monitor (PMA)

Se si usano monitor configurati con fattori di scala per lo schermo differenti o ci si connette in remoto a un computer con fattori di scala per lo schermo diversi dal dispositivo principale, si può notare che Visual Studio sembra sfocato o esegue il rendering con una scala errata.

Con la versione Visual Studio 2019, Visual Studio si sta trasformando in un'applicazione sensibile ai valori del monitor (PMA). Ora Visual Studio esegue il rendering correttamente indipendentemente dai fattori di scala del display utilizzati.

   ![Rendering sensibile ai valori del monitor (PMA) in Visual Studio 2019](media/vs-2019/pma-dpi-scaling.png)

Per altre informazioni, vedere il post di blog [Better multi-monitor experience with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) (Esperienza con più monitor migliore con Visual Studio 2019).

### <a name="test-explorer"></a>Esplora test

**Novità della 16,2**: è stato aggiornato Esplora test per offrire una gestione migliore di set di test di grandi dimensioni, un filtro più semplice, più comandi individuabili, visualizzazioni playlist a schede e colonne personalizzabili che consentono di ottimizzare le informazioni di test visualizzate.

   ![Screenshot che mostra i miglioramenti dell'interfaccia utente in Esplora test](media/vs-2019/test-explorer-ui.png)

### <a name="net-core"></a>.NET Core

**Novità della 16,3**: è stato incluso il supporto per .net core 3,0. Multi-piattaforma, Open Source &mdash; e completamente supportato da Microsoft.

Per altre informazioni, vedere il post di Blog relativo all' [annuncio di .NET Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) .

## <a name="collaborate"></a>Collaborare

Vedere il video seguente per altre informazioni su come è possibile lavorare in team per risolvere i problemi. <br><br>*Lunghezza video: 4,22 minuti*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Primo flusso di lavoro git

La nuova finestra iniziale non passa di certo inosservata alla prima apertura di Visual Studio 2019.

   ![Screenshot della nuova finestra iniziale in Visual Studio 2019](media/vs-2019/start-window-dark.png)

La finestra iniziale offre diverse opzioni per iniziare rapidamente con la scrittura del codice. In primo piano è stata posizionata l'opzione per clonare o eseguire il checkout del codice da un repository.

   ![Animazione dell'esperienza 'Git-first' in Visual Studio 2019](media/vs-2019/git-first.gif)

La finestra iniziale include anche le opzioni per aprire un progetto o una soluzione, aprire una cartella locale o creare un nuovo progetto.

Per altre informazioni, vedere il post di Blog relativo [a come è stato progettato il nuovo avvio di Visual Studio](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) .

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) è un servizio per sviluppatori che consente di condividere una codebase e il relativo contesto con un collega e ottenere collaborazione bidirezionale immediata direttamente all'interno di Visual Studio. Con Live Share un collega può leggere, esplorare, modificare ed eseguire il debug di un progetto condiviso da un altro utente, in modo facile e sicuro.

Con Visual Studio 2019, questo servizio viene installato per impostazione predefinita.

![Animazione che illustra la funzionalità di collaborazione Live Share in Visual Studio 2019](media/vs-2019/live-share.gif)

Per altre informazioni, vedere i post di blog [Visual Studio Live Share for real-time code reviews and interactive education](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) (Visual Studio Live Share per revisioni del codice in tempo reale e formazione interattiva) e [Live Share now included with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) (Live Share è ora incluso in Visual Studio 2019).

### <a name="integrated-code-reviews"></a>Revisioni del codice integrate

È ora possibile scaricare una nuova estensione da usare con Visual Studio 2019. Questa nuova estensione supporta la revisione, l'esecuzione e addirittura il debug delle richieste pull del team senza uscire da Visual Studio. È supportato il codice sia nei repository GitHub che Azure DevOps.

   ![Screenshot della nuova finestra iniziale in Visual Studio 2019](media/vs-2019/pr-experience.png)

Per altre informazioni, vedere il post di blog [Code reviews using the Visual Studio Pull Requests extension](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) (Revisioni del codice usando l'estensione richieste pull di Visual Studio).

## <a name="debug"></a>Debug

Vedere il video seguente per altre informazioni su come ottenere maggiore precisione con destinazioni più accurate durante il debug. <br><br>*Lunghezza video: 3,54 minuti*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Miglioramenti delle prestazioni

I punti di interruzione dei dati C++, una volta esclusivi, sono stati adattati per le applicazioni .NET Core.

   ![Animazione che mostra i punti di interruzione dei dati di debug in Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif)

Indipendentemente dal fatto che il codice venga scritto in C++ o .NET Core, quindi, i punti di interruzione dei dati possono essere una valida alternativa al semplice inserimento di punti di interruzione normali. I punti di interruzione dei dati sono anche ideali in situazioni in cui occorre ad esempio scoprire se un oggetto globale viene modificato o viene aggiunto o rimosso da un elenco.

Per gli sviluppatori C++ che realizzano applicazioni di grandi dimensioni, inoltre, i simboli in Visual Studio 2019 sono out-of-process e ciò consente di eseguire il debug di tali applicazioni senza sperimentare problemi correlati alla memoria.

### <a name="search-while-debugging"></a>Eseguire la ricerca durante il debug

Probabilmente la finestra Espressioni di controllo è già stata usata in precedenza, magari per la ricerca di una stringa tra un set di valori. In Visual Studio 2019 è stata aggiunta la funzionalità di ricerca nelle finestre Espressioni di controllo, Variabili locali e Auto per consentire la ricerca degli oggetti e dei valori richiesti.

   ![Animazione che mostra la finestra di ricerca di debug in Visual Studio 2019](media/vs-2019/debug-window-search.gif)

È anche possibile formattare il modo in cui un valore viene visualizzato all'interno delle finestre Espressioni di controllo, Variabili locali e Auto.  Fare doppio clic su uno degli elementi in una qualsiasi delle finestre e aggiungere una virgola (",") per accedere all'elenco a discesa dei possibili identificatori di formato, ognuno dei quali include una descrizione del relativo effetto desiderato.

   ![Nuova finestra Espressioni di controllo e funzionalità di formattazione dei valori in Visual Studio 2019](media/search-watch-window.png)

Per ulteriori informazioni, vedere il post di Blog relativo alla [funzionalità avanzata in Visual Studio 2019: ricerca di oggetti e proprietà nel post di Blog relativo alle finestre espressioni di controllo, auto e variabili locali](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) .

### <a name="snapshot-debugger"></a>Debugger di snapshot

Ottenere uno snapshot dell'esecuzione dell'app nel cloud per vedere esattamente ciò che accade. (Questa funzionalità è disponibile solo in Visual Studio Enterprise.)

   ![Animazione che mostra Snapshot Debugger in Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif)

È stato aggiunto il supporto per le applicazioni ASP.NET (Core e desktop) in esecuzione su una macchina virtuale di Azure. È stato anche aggiunto il supporto per le applicazioni eseguite in un servizio Azure Kubernetes. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

Per altre informazioni, vedere la pagina [Eseguire il debug di app di Azure ASP.NET attive con Snapshot Debugger](../debugger/debug-live-azure-applications.md) e il post di blog [Introducing Time Travel Debugging for Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) (Introduzione a Debug spostamento cronologico per Visual Studio Enterprise 2019).

### <a name="microsoft-edge-insider-support"></a>Supporto per Microsoft Edge Insider

**Novità in 16,2**: è possibile impostare un punto di interruzione in un'applicazione JavaScript e avviare una sessione di debug usando il browser [Microsoft Edge Insider](https://www.microsoftedgeinsider.com/) . In tal caso, Visual Studio apre una nuova finestra del browser con il debug abilitato, che è possibile usare per analizzare le singole istruzioni nell'applicazione JavaScript in Visual Studio.

   ![Screenshot che mostra il rendering del codice JavaScript in un browser](media/vs-2019/edge-chromium-breakpoint.png)

### <a name="pinnable-properties-tool"></a>Strumento Proprietà aggiungibili

**Novità in 16,4**: ora è più facile identificare gli oggetti in base alle relative proprietà durante il debug con il nuovo strumento Proprietà aggiungibili. È sufficiente passare il puntatore del mouse su una proprietà che si desidera visualizzare nella finestra del debugger delle finestre espressioni di controllo, auto e variabili locali, selezionare l'icona Aggiungi e visualizzare immediatamente le informazioni che si stanno cercando nella parte superiore della finestra.

   ![Un'animazione che Mostra come aggiungere proprietà nel debugger di Visual Studio usando lo strumento delle proprietà aggiungibili](media/vs-2019/debugger-pinnable-properties.gif)

Per altre informazioni, vedere il post di Blog relativo alle [proprietà di aggiungibili: Debug & Visualizza oggetti gestiti](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) .

## <a name="whats-next"></a>Passaggi successivi

Visual Studio 2019 viene aggiornato spesso con nuove funzionalità in grado di migliorare ulteriormente l'esperienza di sviluppo. Per ulteriori informazioni sulle ultime innovazioni, consultare il [Blog di Visual Studio](https://devblogs.microsoft.com/visualstudio/). Per un resoconto di quanto è stato rilasciato in anteprima, vedere le note sulla versione di [Anteprima](/visualstudio/releases/2019/release-notes-preview/). Per un elenco degli elementi che si prevede di rilasciare successivamente, vedere la [Roadmap di Visual Studio](/visualstudio/productinfo/vs-roadmap).

Per altri dettagli sulle funzionalità in corso di sviluppo per Visual Studio 2019, vedere la pagina [Visual Studio Roadmap](/visualstudio/productinfo/vs-roadmap/).

## <a name="give-us-feedback"></a>Commenti e suggerimenti

È possibile inviare commenti e suggerimenti al team di Visual Studio. Microsoft prende infatti in seria considerazione i commenti e suggerimenti ricevuti dai clienti, usandoli per migliorare i propri prodotti.

* Se si vuole inviare un suggerimento per migliorare Visual Studio, è possibile usare lo strumento [Suggerisci una funzionalità](suggest-a-feature.md).

* Se si verifica un blocco, un arresto anomalo del sistema o un altro problema di prestazioni, è possibile condividere facilmente con Microsoft la procedura per riprodurre il problema e i file di supporto usando lo strumento [Segnala un problema](how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Vedi anche

* [Note sulla versione di Visual Studio 2019](/visualstudio/releases/2019/release-notes/)
* [Note sulla versione di Visual Studio 2019 per Mac](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Novità di Visual Studio 2019 SDK](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Novità di C++ in Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio.md)
* [Novità di C# 8,0](/dotnet/csharp/whats-new/csharp-8.md)
* [Novità di .NET Core 3.1](/dotnet/core/whats-new/dotnet-core-3-1.md)
* [Novità di .NET Framework](/dotnet/framework/whats-new.md)
* [Microsoft Build Conference](https://www.microsoft.com/build)
* [Conferenza Microsoft Ignite](https://www.microsoft.com/ignite)
