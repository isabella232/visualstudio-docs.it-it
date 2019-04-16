---
title: Novità di Visual Studio 2019
titleSuffix: ''
description: Informazioni sulle nuove funzionalità di Visual Studio 2019.
ms.date: 04/04/2019
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
ms.openlocfilehash: 25a7f5f0e53518e9beb4b509ab27ae4de0f28fa7
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018155"
---
# <a name="whats-new-in-visual-studio-2019"></a>Novità di Visual Studio 2019

**Contenuto aggiornato per la [versione 16.0](/visualstudio/releases/2019/release-notes/)**

>[!div class="button"]
>[Scarica Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

Visual Studio 2019 include gli strumenti e i servizi migliori del settore per qualsiasi sviluppatore, app e piattaforma. Sia per gli utenti che usano Visual Studio per la prima volta che per quelli di lunga data, c'è molto da scoprire nella nuova versione.

Ecco un riepilogo generale delle novità:

* **[Sviluppo](#develop)**: rimanere concentrati e produttivi con prestazioni migliorate, pulizia del codice immediata e risultati di ricerca ottimizzati.
* **[Collaborazione](#collaborate)**: il piacere di collaborare in modo naturale grazie a un flusso di lavoro cloud-first, modifica e debug in tempo reale e revisioni del codice direttamente in Visual Studio.
* **[Debug](#debug)**: evidenziare e passare a valori specifici, ottimizzare l'uso della memoria e acquisire snapshot automatici dell'esecuzione dell'applicazione.

Per un elenco completo di tutte le novità in questa versione, vedere le [note sulla versione](/visualstudio/releases/2019/release-notes/). 

## <a name="develop"></a>Sviluppo

Risparmiare tempo con le nuove funzionalità.
<br><br>
> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Miglioramento della ricerca

Precedentemente nota come Avvio veloce, la nuova esperienza di ricerca è più rapida ed efficiente. Ora i risultati della ricerca vengono visualizzati dinamicamente durante la digitazione. Possono anche spesso includere tasti di scelta rapida per i comandi, in modo da poterli memorizzare più facilmente per usarli in futuro.

   ![Animazione della nuova esperienza di ricerca in Visual Studio 2019](media/vs-2019/new-search-feature.gif)

La nuova logica di ricerca fuzzy consentirà di trovare tutto quello che serve, anche se sono presenti errori di digitazione. Indipendentemente dal fatto che si stiano cercando comandi, impostazioni, documentazione o altri elementi utili, la nuova funzionalità di ricerca rende più semplice trovare quello che si sta cercando.

### <a name="refactorings"></a>Refactoring

I nuovi refactoring C# rendono più semplice organizzare il codice. È sufficiente richiamare i refactoring premendo **CTRL+.** e selezionando l'azione che si vuole eseguire. 

   ![Animazione dell'esperienza di refactoring in Visual Studio 2019](media/vs-2019/refactorings.gif)

Sono stati aggiunti molti nuovi refactoring, tra cui uno che consente di eseguire il wrapping dei parametri dei metodi.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) è un'estensione che ottimizza le attività di sviluppo software con l'uso dell'intelligenza artificiale. IntelliCode esegue il training tra 2000 progetti open source su GitHub&mdash;ognuno con oltre 100 stelle&mdash;per generare raccomandazioni.

 ![Animazione di IntelliCode in Visual Studio 2019](media/vs-2019/IntelliCode.gif)

Ecco alcuni modi in cui Visual Studio IntelliCode può essere utile per migliorare la produttività:

* Completamento del codice con riconoscimento del contesto
* Guida per gli sviluppatori per il rispetto dei criteri e degli stili usati dal team
* Individuazione di problemi del codice difficili da trovare
* Revisioni del codice mirate, che pongono al centro dell'attenzione le aree realmente importanti

Per la versione di anteprima dell'estensione IntelliCode per Visual Studio è stato inizialmente previsto solo il supporto per C#. Attualmente è disponibile anche il supporto per C++ e XAML in Visual Studio.

Per chi usa C#, è stata inoltre aggiunta la possibilità di eseguire il training di un modello personalizzato nel proprio codice.

Per altre informazioni su IntelliCode, vedere il post di blog [Code more, scroll less with Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) (Più codice, meno spostamenti con Visual Studio IntelliCode). 

### <a name="code-cleanup"></a>Pulizia del codice

Abbinato a un nuovo indicatore di integrità dei documenti è disponibile un nuovo comando per la pulizia del codice. È possibile usare questo nuovo comando per identificare e quindi risolvere avvisi e suggerimenti con il semplice clic di un pulsante.

L'operazione di pulizia formatterà il codice e applicherà eventuali correzioni del codice come suggerito dalle [impostazioni correnti](code-styles-and-quick-actions.md), dai [file con estensione editorconfig](create-portable-custom-editor-options.md) o dagli [analizzatori di Roslyn](../code-quality/roslyn-analyzers-overview.md).

   ![Screenshot del nuovo controllo di pulizia del codice in Visual Studio 2019](media/vs-2019/code-cleanup-profile.png)

È anche possibile salvare raccolte di utilità di correzione come profilo. Ad esempio, se si applica di frequente un piccolo set di utilità di correzione specifiche durante la scrittura del codice e poi si usa un altro set completo di utilità di correzione da applicare prima di una revisione del codice, è possibile configurare due profili per queste attività diverse.

   ![Screenshot del nuovo controllo di pulizia del codice in Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png)

## <a name="collaborate"></a>Collaborazione

Lavorare in team per risolvere i problemi.
<br><br>
> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="cloud-first-workflow"></a>Flusso di lavoro cloud-first

La nuova finestra iniziale non passa di certo inosservata alla prima apertura di Visual Studio 2019.

   ![Screenshot della nuova finestra iniziale in Visual Studio 2019](media/vs-2019/start-window-dark.png)

La finestra iniziale offre diverse opzioni per iniziare rapidamente con la scrittura del codice. In primo piano è stata posizionata l'opzione per clonare o eseguire il checkout del codice da un repository.  

   ![Animazione dell'esperienza 'Git-first' in Visual Studio 2019](media/vs-2019/git-first.gif)

La finestra iniziale include anche le opzioni per aprire un progetto o una soluzione, aprire una cartella locale o creare un nuovo progetto.

Per altre informazioni, vedere il post di blog [Get to code: How we designed the new Visual Studio start window](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) (Vai al codice: come è stata progettata la nuova finestra iniziale di Visual Studio).

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) è un servizio per sviluppatori che consente di condividere una codebase e il relativo contesto con un collega e ottenere collaborazione bidirezionale immediata direttamente all'interno di Visual Studio. Con Live Share un collega può leggere, esplorare, modificare ed eseguire il debug di un progetto condiviso da un altro utente, in modo facile e sicuro.

Con Visual Studio 2019, questo servizio viene installato per impostazione predefinita.

![Animazione che illustra la funzionalità di collaborazione Live Share in Visual Studio 2019](media/vs-2019/live-share.gif)

Per altre informazioni, vedere i post di blog [Visual Studio Live Share for real-time code reviews and interactive education](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) (Visual Studio Live Share per revisioni del codice in tempo reale e formazione interattiva) e [Live Share now included with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) (Live Share è ora incluso in Visual Studio 2019).

### <a name="integrated-code-reviews"></a>Revisioni del codice integrate

È ora possibile scaricare una nuova estensione da usare con Visual Studio 2019. Questa nuova estensione supporta la revisione, l'esecuzione e addirittura il debug delle richieste pull del team senza uscire da Visual Studio. È supportato il codice sia nei repository GitHub che Azure DevOps.

   ![Screenshot della nuova finestra iniziale in Visual Studio 2019](media/vs-2019/pr-experience.png)

Per iniziare subito, scaricare l'estensione [Richieste pull per Visual Studio](https://aka.ms/pr4vs) da Visual Studio Marketplace.

## <a name="debug"></a>Debug

Maggiore precisione con destinazioni di debug più accurate.
<br><br>
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

Per altre informazioni, vedere il post di blog [Enhanced in Visual Studio 2019: Search for Objects and Properties in the Watch, Autos, and Locals Windows](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) (Miglioramenti di Visual Studio 2019: Ricerca di oggetti e proprietà nelle finestre Espressione di controllo, Auto e Variabili locali).

### <a name="snapshot-debugger"></a>Debugger di snapshot

Ottenere uno snapshot dell'esecuzione dell'app nel cloud per vedere esattamente ciò che accade. (Questa funzionalità è disponibile solo in Visual Studio Enterprise.)

   ![Animazione che mostra Snapshot Debugger in Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif)

È stato aggiunto il supporto per le applicazioni ASP.NET (Core e desktop) in esecuzione su una macchina virtuale di Azure. È stato anche aggiunto il supporto per le applicazioni eseguite in un servizio Azure Kubernetes. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

Per altre informazioni, vedere la pagina [Eseguire il debug di app di Azure ASP.NET attive con Snapshot Debugger](../debugger/debug-live-azure-applications.md) e il post di blog [Introducing Time Travel Debugging for Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) (Introduzione a Debug spostamento cronologico per Visual Studio Enterprise 2019).

## <a name="give-us-feedback"></a>Commenti e suggerimenti

È possibile inviare commenti e suggerimenti al team di Visual Studio. Microsoft prende infatti in seria considerazione i commenti e suggerimenti ricevuti dai clienti, usandoli per migliorare i propri prodotti.

* Se si vuole inviare un suggerimento per il miglioramento di Visual Studio, è possibile usare lo strumento [Invia un suggerimento](talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features).

* Se si verifica un blocco, un arresto anomalo del sistema o un altro problema di prestazioni, è possibile condividere facilmente con Microsoft la procedura per riprodurre il problema e i file di supporto usando lo strumento [Segnala un problema](talk-to-us.md#i-want-to-report-a-problem-with-visual-studio).

## <a name="see-also"></a>Vedere anche

* [Annuncio di Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-code-faster-work-smarter-create-the-future/)
* [Note sulla versione di Visual Studio 2019](/visualstudio/releases/2019/release-notes/)
* [Novità di Visual Studio 2019 SDK](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Visual Studio 2019 per Mac è ora disponibile](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-for-mac-is-now-available/)
* [Conferenza Microsoft Connect(); 2018](https://www.microsoft.com/connectevent)
