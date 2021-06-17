---
title: Novità di Visual Studio 2019
titleSuffix: ''
description: Informazioni sulle nuove funzionalità di Visual Studio 2019.
ms.date: 05/28/2021
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 1860c399318dbe68c55db9b07068c3dd635481c9
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113059"
---
# <a name="whats-new-in-visual-studio-2019"></a>Novità di Visual Studio 2019

**Aggiornamento per la versione 16.10.** Vedere [le note sulla versione](/visualstudio/releases/2019/release-notes/) | Visualizzare la [roadmap del prodotto](/visualstudio/productinfo/vs-roadmap)

>[!div class="button"]
>[Scarica Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

Visual Studio 2019 include gli strumenti e i servizi migliori del settore per qualsiasi sviluppatore, app e piattaforma. Se si usa Visual Studio per la prima volta o lo si usa da anni, la versione più recente è molto simile.

Ecco un riepilogo di alto livello delle novità:

* **[Sviluppare:](#develop)** rimanere concentrati e produttivi con prestazioni migliorate, pulizia immediata del codice e risultati di ricerca migliori.
* **[Collaborazione:](#collaborate)** è possibile usufruire della collaborazione naturale tramite un flusso di lavoro basato su Git, la modifica e il debug in tempo reale e le revisioni del codice direttamente Visual Studio.
* **[Debug:](#debug)** evidenzia e passa a valori specifici, ottimizza l'uso della memoria ed esegue snapshot automatici dell'esecuzione dell'applicazione.

Per un elenco completo di tutte le novità in questa versione, vedere le [note sulla versione](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Sviluppo

Vedere il video seguente per altre informazioni su come è possibile risparmiare tempo con le nuove funzionalità. <br><br>*Lunghezza del video: 3,00 minuti*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Miglioramento della ricerca

Precedentemente nota come Avvio veloce, la nuova esperienza di ricerca è più rapida ed efficiente. Ora i risultati della ricerca vengono visualizzati dinamicamente durante la digitazione. I risultati della ricerca possono spesso includere tasti di scelta rapida per i comandi, in modo da poterli memorizzare per un uso futuro.

   ![Animazione della nuova esperienza di ricerca in Visual Studio 2019](media/vs-2019/new-search-feature.gif "Nuova esperienza di ricerca in Visual Studio 2019.")

La nuova logica di ricerca fuzzy consentirà di trovare tutto quello che serve, anche se sono presenti errori di digitazione. Indipendentemente dal fatto che si stiano cercando comandi, impostazioni, documentazione o altri elementi utili, la nuova funzionalità di ricerca rende più semplice trovare quello che si sta cercando.

Per altre informazioni, vedere [Usare Visual Studio ricerca.](visual-studio-search.md)

#### <a name="intelligent-search-service"></a>Servizio di ricerca intelligente

**Novità della versione 16.9:** grazie all'uso di tecnologia basata sul cloud, intelligenza artificiale e Machine Learning, i risultati della ricerca sono stati migliorati. Ora, non solo la ricerca in Visual Studio produce risultati più rilevanti, ma può anche aiutare a individuare più facilmente le funzionalità del prodotto.

Per altre informazioni, vedere il post di blog intelligent Visual Studio search service (Servizio [di ricerca intelligente).](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/)

### <a name="refactorings"></a>Refactoring

Esistono molti refactoring nuovi ed estremamente utili in C# che rendono più semplice organizzare il codice. Vengono visualizzati come suggerimenti nella lampadina e includono azioni, ad esempio lo spostamento di membri in un'interfaccia o una classe di base, l'adattamento degli spazi dei nomi alla struttura delle cartelle, la conversione dei cicli foreach per le query Linq e altro ancora.

   ![Animazione dell'esperienza di refactoring in Visual Studio 2019](media/vs-2019/refactorings.gif "Esperienza di refactoring in Visual Studio 2019.")

È sufficiente richiamare i refactoring premendo **CTRL+.** e selezionando l'azione che si vuole eseguire.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) ottimizza le attività di sviluppo software con l'uso dell'intelligenza artificiale. IntelliCode esegue il training tra 2000 progetti open source su GitHub&mdash;ognuno con oltre 100 stelle&mdash;per generare raccomandazioni.

![Animazione di IntelliCode in Visual Studio 2019](media/vs-2019/IntelliCode.gif "IntelliCode in Visual Studio 2019.")

Ecco alcuni modi in cui Visual Studio IntelliCode può essere utile per migliorare la produttività:

* Completamento del codice con riconoscimento del contesto
* Guida per gli sviluppatori per il rispetto dei criteri e degli stili usati dal team
* Individuazione di problemi del codice difficili da trovare
* Revisioni del codice mirate, che pongono al centro dell'attenzione le aree realmente importanti

Per la versione di anteprima di IntelliCode come estensione per Visual Studio era stato inizialmente previsto solo il supporto per C#. Ora, come **novità della versione 16.1**, è stato aggiunto il supporto per C# e XAML come predefinito. (Il supporto per C++ e TypeScript/JavaScript sono, tuttavia, ancora in anteprima.)

Per chi usa C#, è stata inoltre aggiunta la possibilità di eseguire il training di un modello personalizzato nel proprio codice.

Per altre informazioni su IntelliCode, vedere i post di blog [Announcing the general availability of IntelliCode plus a sneak peek](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) (Annuncio della disponibilità generale di IntelliCode più un assaggio) e [Code more, scroll less with Visual Studio IntelliCode ](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) (Scrivere più codice e scorrere meno con Visual Studio IntelliCode).

### <a name="code-cleanup"></a>Pulizia del codice

Abbinato a un nuovo indicatore di integrità dei documenti è disponibile un nuovo comando per la pulizia del codice. È possibile usare questo nuovo comando per identificare e correggere avvisi e suggerimenti con una singola azione (o clic su un pulsante).

L'operazione di pulizia formatterà il codice e applicherà eventuali correzioni del codice come suggerito dalle [impostazioni correnti](code-styles-and-code-cleanup.md) e dai [file con estensione editorconfig](create-portable-custom-editor-options.md).

   ![Screenshot del nuovo controllo di pulizia del codice in Visual Studio 2019](media/vs-2019/code-cleanup-profile.png "Il nuovo controllo di pulizia del codice Visual Studio 2019.")

È anche possibile salvare raccolte di utilità di correzione come profilo. Ad esempio, se si applica di frequente un piccolo set di utilità di correzione specifiche durante la scrittura del codice e poi si usa un altro set completo di utilità di correzione da applicare prima di una revisione del codice, è possibile configurare due profili per queste attività diverse.

   ![Screenshot del controllo di configurazione della pulizia del codice in Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png "Configurare il controllo di pulizia del codice Visual Studio 2019.")

### <a name="per-monitor-aware-pma-rendering"></a>Rendering sensibile ai valori del monitor (PMA)

Se si usano monitor configurati con fattori di scala per lo schermo differenti o ci si connette in remoto a un computer con fattori di scala per lo schermo diversi dal dispositivo principale, si può notare che Visual Studio sembra sfocato o esegue il rendering con una scala errata.

Con la versione Visual Studio 2019, Visual Studio si sta trasformando in un'applicazione sensibile ai valori del monitor (PMA). Ora Visual Studio esegue il rendering correttamente indipendentemente dai fattori di scala del display utilizzati.

   ![Rendering sensibile ai valori del monitor (PMA) in Visual Studio 2019](media/vs-2019/pma-dpi-scaling.png "Rendering con supporto per monitor (PMA) in Visual Studio 2019.")

Per altre informazioni, vedere il post di blog [Better multi-monitor experience with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) (Esperienza con più monitor migliore con Visual Studio 2019).

### <a name="test-explorer"></a>Esplora test

Novità **della versione 16.2:** Esplora test è stato aggiornato per offrire una migliore gestione di set di test di grandi dimensioni, filtri più semplici, comandi più individuabili, visualizzazioni playlist a schede e colonne personalizzabili che consentono di ottimizzare le informazioni sui test visualizzate.

   ![Screenshot che mostra i miglioramenti dell'interfaccia utente in Esplora test](media/vs-2019/test-explorer-ui.png "Miglioramenti dell'interfaccia utente in Esplora test.")

### <a name="net-core"></a>.NET Core

**Novità della versione 16.3:** è stato incluso il supporto per .NET Core 3.0. Multipiattaforma, open source &mdash; e completamente supportato da Microsoft.

Per altre informazioni, vedere il post di blog [Announcing .NET Core 3.0 (Annuncio di .NET Core 3.0).](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/)

## <a name="collaborate"></a>Collaborazione

Vedere il video seguente per altre informazioni su come è possibile lavorare in team per risolvere i problemi. <br><br>*Lunghezza del video: 4,22 minuti*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Flusso di lavoro Git-first

La nuova finestra iniziale non passa di certo inosservata alla prima apertura di Visual Studio 2019.

   ![Screenshot della nuova finestra iniziale in Visual Studio 2019](media/vs-2019/start-window-dark.png "Nuova finestra iniziale in Visual Studio 2019.")

La finestra iniziale offre diverse opzioni per iniziare rapidamente con la scrittura del codice. In primo piano è stata posizionata l'opzione per clonare o eseguire il checkout del codice da un repository.

   ![Animazione dell'esperienza 'Git-first' in Visual Studio 2019](media/vs-2019/git-first.gif "Esperienza &quot;Git-first&quot; in Visual Studio 2019.")

La finestra iniziale include anche le opzioni per aprire un progetto o una soluzione, aprire una cartella locale o creare un nuovo progetto.

Per altre informazioni, vedere il post di blog [Get to code: How we designed the new Visual Studio start window](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) (Ottieni codice: come è stato progettato il nuovo Visual Studio iniziale).

### <a name="git-productivity"></a>Produttività di Git

**Novità della versione 16.8:** Git è ora l'esperienza di controllo della versione predefinita Visual Studio 2019. Il set di funzionalità è stato creato ed è stato iterato in base ai commenti e suggerimenti degli utenti durante le due versioni precedenti. La nuova esperienza è ora attivata per impostazione predefinita per tutti gli utenti. Dal nuovo menu Git è possibile clonare, creare o aprire i repository. Usare le finestre degli strumenti Git integrate per eseguire il commit e il push delle modifiche al codice, gestire i rami, rimanere aggiornati con i repository remoti e risolvere i conflitti di merge.

Per altre informazioni, vedere [l'esperienza Git in Visual Studio](../version-control/git-with-visual-studio.md) pagina.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) è un servizio per sviluppatori che consente di condividere una codebase e il relativo contesto con un collega e ottenere collaborazione bidirezionale immediata direttamente all'interno di Visual Studio. Con Live Share un collega può leggere, esplorare, modificare ed eseguire il debug di un progetto condiviso da un altro utente, in modo facile e sicuro.

Con Visual Studio 2019, questo servizio viene installato per impostazione predefinita.

![Animazione che illustra la funzionalità di collaborazione Live Share in Visual Studio 2019](media/vs-2019/live-share.gif "La Live Share di collaborazione in Visual Studio 2019.")

Per altre informazioni, vedere i post di blog [Visual Studio Live Share for real-time code reviews and interactive education](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) (Visual Studio Live Share per revisioni del codice in tempo reale e formazione interattiva) e [Live Share now included with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) (Live Share è ora incluso in Visual Studio 2019).

### <a name="integrated-code-reviews"></a>Revisioni del codice integrate

È ora possibile scaricare una nuova estensione da usare con Visual Studio 2019. Questa nuova estensione supporta la revisione, l'esecuzione e addirittura il debug delle richieste pull del team senza uscire da Visual Studio. È supportato il codice sia nei repository GitHub che Azure DevOps.

   ![Screenshot della nuova estensione Richieste pull in Visual Studio 2019](media/vs-2019/pr-experience.png "Nuova estensione richieste pull in Visual Studio 2019.")

Per altre informazioni, vedere il post di blog [Code reviews using the Visual Studio Pull Requests extension](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) (Revisioni del codice usando l'estensione richieste pull di Visual Studio).

## <a name="debug"></a>Debug

Vedere il video seguente per altre informazioni su come ottenere maggiore precisione con destinazioni più accurate durante il debug. <br><br>*Lunghezza video: 3,54 minuti*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Miglioramenti delle prestazioni

I punti di interruzione dei dati C++, una volta esclusivi, sono stati adattati per le applicazioni .NET Core.

   ![Animazione che mostra i punti di interruzione dei dati di debug in Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif "Punti di interruzione dei dati di debug Visual Studio 2019.")

Indipendentemente dal fatto che il codice venga scritto in C++ o .NET Core, quindi, i punti di interruzione dei dati possono essere una valida alternativa al semplice inserimento di punti di interruzione normali. I punti di interruzione dei dati sono anche ideali in situazioni in cui occorre ad esempio scoprire se un oggetto globale viene modificato o viene aggiunto o rimosso da un elenco.

Per gli sviluppatori C++ che realizzano applicazioni di grandi dimensioni, inoltre, i simboli in Visual Studio 2019 sono out-of-process e ciò consente di eseguire il debug di tali applicazioni senza sperimentare problemi correlati alla memoria.

### <a name="search-while-debugging"></a>Eseguire la ricerca durante il debug

Probabilmente la finestra Espressioni di controllo è già stata usata in precedenza, magari per la ricerca di una stringa tra un set di valori. In Visual Studio 2019 è stata aggiunta la funzionalità di ricerca nelle finestre Espressioni di controllo, Variabili locali e Auto per consentire la ricerca degli oggetti e dei valori richiesti.

   ![Animazione che mostra la finestra di ricerca di debug in Visual Studio 2019](media/vs-2019/debug-window-search.gif "Finestra di ricerca di debug in Visual Studio 2019.")

È anche possibile formattare il modo in cui un valore viene visualizzato all'interno delle finestre Espressioni di controllo, Variabili locali e Auto. Selezionare (facendo doppio clic su) uno degli elementi in una delle finestre e aggiungere una virgola (",") per accedere all'elenco a discesa dei possibili identificatori di formato, ognuno dei quali include una descrizione dell'effetto previsto.

   ![Nuova finestra Espressioni di controllo e funzionalità di formattazione dei valori in Visual Studio 2019](media/search-watch-window.png "La nuova finestra Espressioni di controllo e i valori di formato Visual Studio 2019.")

Per altre informazioni, vedere il post di blog [Enhanced in Visual Studio 2019: Search for Objects and Properties nel](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) post di blog di Windows Watch, Autos e Locals.

### <a name="snapshot-debugger"></a>Debugger di snapshot

Ottenere uno snapshot dell'esecuzione dell'app nel cloud per vedere esattamente ciò che accade. (Questa funzionalità è disponibile solo in Visual Studio Enterprise.)

   ![Animazione che mostra Snapshot Debugger in Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif "La Snapshot Debugger in Visual Studio 2019 Enterprise.")

È stato aggiunto il supporto per le applicazioni ASP.NET (Core e desktop) in esecuzione su una macchina virtuale di Azure. È stato anche aggiunto il supporto per le applicazioni eseguite in un servizio Azure Kubernetes. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

Per altre informazioni, vedere la pagina [Eseguire il debug di app di Azure ASP.NET attive con Snapshot Debugger](../debugger/debug-live-azure-applications.md) e il post di blog [Introducing Time Travel Debugging for Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) (Introduzione a Debug spostamento cronologico per Visual Studio Enterprise 2019).

### <a name="microsoft-edge-insider-support"></a>Supporto per Microsoft Edge Insider

**Novità della versione 16.2:** è possibile impostare un punto di interruzione in un'applicazione JavaScript e avviare una sessione di debug usando il browser [Microsoft Edge Insider.](https://www.microsoftedgeinsider.com/) In tal caso, Visual Studio apre una nuova finestra del browser con il debug abilitato, che è possibile usare per analizzare le singole istruzioni nell'applicazione JavaScript in Visual Studio.

   ![Screenshot che mostra il rendering del codice JavaScript in un browser](media/vs-2019/edge-chromium-breakpoint.png "Rendering del codice JavaScript in un browser.")

### <a name="pinnable-properties-tool"></a>Strumento Proprietà pinnable

**Novità della versione 16.4:** ora è più semplice identificare gli oggetti in base alle relative proprietà durante il debug con il nuovo strumento Proprietà pinnable. È sufficiente passare il cursore su una proprietà che si vuole visualizzare nella finestra del debugger delle finestre Espressioni di controllo, Auto e Variabili locali, selezionare l'icona della puntina e visualizzare immediatamente le informazioni che si stanno cercando nella parte superiore della finestra.

   ![Animazione che illustra come aggiungere proprietà nel debugger Visual Studio usando lo strumento Proprietà pinnable](media/vs-2019/debugger-pinnable-properties.gif "Aggiungere le proprietà nel debugger Visual Studio usando lo strumento Proprietà pinnable.")

Per altre informazioni, vedere il post di blog [Pinnable Properties: Debug & Display Managed Objects YOUR Way ( Proprietà pinnable: debug) & di](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) blog Display Managed Objects YOUR Way (Visualizzare oggetti gestiti in modo personale).

## <a name="whats-next"></a>Passaggi successivi

Visual Studio 2019 viene aggiornato spesso con nuove funzionalità in grado di migliorare ulteriormente l'esperienza di sviluppo. Per altre informazioni sulle innovazioni più recenti, vedere il [blog Visual Studio .](https://devblogs.microsoft.com/visualstudio/) Per un record di ciò che è stato rilasciato in anteprima fino ad oggi, vedere le [note sulla versione di anteprima](/visualstudio/releases/2019/release-notes-preview/). Per un elenco degli elementi che si prevede di rilasciare successivamente, vedere la guida Visual Studio [Roadmap](/visualstudio/productinfo/vs-roadmap).

Nel frattempo, ecco una nuova funzionalità attualmente in esecuzione.

- **Esperienza Git migliorata in Visual Studio 2019 (anteprima)**

   Anche se la nuova esperienza di controllo della versione di Git è ora disponibile per impostazione predefinita in Visual Studio 2019 [versione 16.8,](/visualstudio/releases/2019/release-notes/)si continuano ad aggiungere funzionalità per migliorare l'esperienza nella versione di anteprima più recente.

   Per altre informazioni, vedere il [controllo della versione nella Visual Studio.](/visualstudio/version-control/)

Per altre informazioni sulla versione di anteprima di Visual Studio 2019 e su un collegamento per il download, vedere la pagina &mdash; &mdash; Visual Studio Preview. **[](https://aka.ms/vspreview/)**

> [!TIP]
> Per altre informazioni sulla versione successiva, vedere il post di blog **[Visual Studio 2022.](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/)**

## <a name="give-us-feedback"></a>Commenti e suggerimenti

È possibile inviare commenti e suggerimenti al team di Visual Studio. Microsoft prende infatti in seria considerazione i commenti e suggerimenti ricevuti dai clienti, usandoli per migliorare i propri prodotti.

* Se si vuole inviare un suggerimento per migliorare Visual Studio, è possibile usare lo strumento [Suggerisci una funzionalità](suggest-a-feature.md).

* Se si verifica un problema per cui Visual Studio smette di rispondere, arresti anomali o altri problemi di prestazioni, è possibile condividere facilmente i passaggi di riproduzione e i file di supporto con Microsoft usando lo strumento Segnala un [problema.](how-to-report-a-problem-with-visual-studio.md)

## <a name="see-also"></a>Vedi anche

* [Novità della documentazione di Visual Studio](whats-new-visual-studio-docs.md)
* [Visual Studio versione 2019](/visualstudio/releases/2019/release-notes/)
* [Visual Studio 2019 per Mac](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Novità di Visual Studio 2019 SDK](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Novità di C++ in Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio/)
* [Novità di C# 9.0](/dotnet/csharp/whats-new/csharp-9)
* [Novità di .NET 5](/dotnet/core/dotnet-five)
* [Novità di .NET Framework](/dotnet/framework/whats-new/)
* [Conferenza di Microsoft Build](https://www.microsoft.com/build)
* [Conferenza Microsoft Ignite](https://www.microsoft.com/ignite)
