---
title: Novità di Visual Studio 2019 Preview
titleSuffix: ''
description: Informazioni sulle nuove funzionalità della versione di anteprima di Visual Studio 2019.
ms.date: 12/19/2018
ms.prod: visual-studio-dev16
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e387485d2a11867944e980a9bad26261fd4a707c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848548"
---
# <a name="what39s-new-in-visual-studio-2019-preview"></a>Novità di Visual Studio 2019 Preview

**Aggiornato per la [versione 16.0 Preview 1](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)**

Visual Studio 2019 Preview include molti miglioramenti di carattere generale e nuove funzionalità che ottimizzano la produttività degli sviluppatori e la collaborazione in team. Indipendentemente dal fatto che si usi Visual Studio per la prima volta o lo si stia usando da anni, sarà possibile sfruttarne le funzionalità per tutti gli aspetti del ciclo di vita di sviluppo, dalla creazione di progetti e gestione dell'integrità del codice semplificate ai flussi di lavoro collaborativi open source e per i team.

Ecco un riepilogo generale delle funzionalità offerte da Visual Studio:

* **[Produttività personale e in team](#personal-and-team-productivity)**. Produttività per tutti gli utenti dove è più necessaria.
* **[Supporto per lo sviluppo moderno](#modern-development-support)**. Supporto per i progetti correnti e le soluzioni future.
* **[Innovazione continua](#continuous-innovation)**. Codifica semplificata con supporto intelligente basato sul cloud.

> [!NOTE]
> Per un elenco completo delle nuove funzionalità di Visual Studio 2019 Preview, vedere le [note sulla versione](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017).

## <a name="personal-and-team-productivity"></a>Produttività personale e in team

È un dato di fatto che i miglioramenti delle prestazioni sono l'obiettivo principale di ogni nuova versione di Visual Studio, ma vanno di pari passo con il miglioramento della produttività. Ecco quali sono le funzionalità principali.

### <a name="new-start-window"></a>Nuova finestra iniziale

La prima cosa che si nota quando si apre Visual Studio 2019 è la nuova finestra iniziale.

   ![Nuova finestra iniziale in Visual Studio 2019](../ide/media/start-window.png)

Questa nuova finestra iniziale offre una serie di opzioni per clonare o estrarre il codice, aprire un progetto o una soluzione, aprire una cartella locale o creare un nuovo progetto. Il fatto che queste opzioni siano immediatamente disponibili in una finestra di dialogo semplice consente sia ai principianti che agli utenti avanzati di Visual Studio di creare codice rapidamente.

Per altre informazioni, vedere il post di blog [Get to code: How we designed the new Visual Studio start window](https://blogs.msdn.microsoft.com/visualstudio/2018/12/13/get-to-code-how-we-designed-the-new-visual-studio-start-window/) (Vai al codice: come è stata progettata la nuova finestra iniziale di Visual Studio).

### <a name="better-search"></a>Ricerca migliorata

Precedentemente nota come Avvio veloce, la nuova esperienza di ricerca è più rapida ed efficiente. Ora i risultati della ricerca vengono visualizzati dinamicamente durante la digitazione. Includono inoltre tasti di scelta rapida per i comandi, in modo che sia possibile memorizzarli in modo più immediato per usarli in futuro.

   ![Nuova funzionalità di ricerca in Visual Studio 2019](../ide/media/search-feature.png)

Indipendentemente dal fatto che si stiano cercando comandi, impostazioni, documentazione o altri elementi utili, la nuova funzionalità di ricerca rende più semplice trovare quello che si sta cercando.

### <a name="one-click-code-cleanup"></a>Pulizia del codice con un clic

Abbinato a un nuovo indicatore di integrità dei documenti è disponibile un nuovo comando per la pulizia del codice. È possibile usare questo nuovo comando per identificare e quindi risolvere avvisi e suggerimenti con il semplice clic di un pulsante.

   ![Nuova funzionalità di pulizia del codice in Visual Studio 2019](../ide/media/code-cleanup.png)

L'operazione di pulizia formatterà il codice e applicherà eventuali correzioni del codice come suggerito dalle [impostazioni correnti](../ide/code-styles-and-quick-actions.md), dai [file con estensione editorconfig](../ide/create-portable-custom-editor-options.md) o dagli [analizzatori di Roslyn](../code-quality/roslyn-analyzers-overview.md).

### <a name="debugger-improvements"></a>Miglioramenti del debugger

#### <a name="search-within-a-watch-window-and-format-watch-values"></a>Eseguire ricerche all'interno di una finestra Espressioni di controllo e formattare i valori di Espressioni di controllo

Probabilmente la finestra Espressioni di controllo è già stata usata in precedenza, magari per la ricerca di una stringa tra un set di valori. In Visual Studio 2019 Preview è stata aggiunta la funzionalità di ricerca nelle finestre Espressioni di controllo, Variabili locali e Auto per consentire la ricerca degli oggetti e dei valori richiesti.

È anche possibile formattare il modo in cui un valore viene visualizzato all'interno delle finestre Espressioni di controllo, Variabili locali e Auto.  Fare doppio clic su uno degli elementi in una qualsiasi delle finestre e aggiungere una virgola (",") per accedere all'elenco a discesa dei possibili identificatori di formato, ognuno dei quali include una descrizione del relativo effetto desiderato.

   ![Nuova finestra Espressioni di controllo e funzionalità di formattazione dei valori in Visual Studio 2019](../ide/media/search-watch-window.png)

### <a name="visual-studio-live-share"></a>Visual Studio Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) è un servizio per sviluppatori che consente di condividere una codebase e il relativo contesto con un collega e ottenere collaborazione bidirezionale immediata direttamente all'interno di Visual Studio. Con Live Share un collega può leggere, esplorare, modificare ed eseguire il debug di un progetto condiviso da un altro utente, in modo facile e sicuro.

Con Visual Studio 2019 Preview, questo servizio viene installato per impostazione predefinita.

Per altre informazioni, vedere il post di blog [Visual Studio Live Share for real-time code reviews and interactive education](https://blogs.msdn.microsoft.com/visualstudio/2018/12/06/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) (Visual Studio Live Share per revisioni del codice in tempo reale e formazione interattiva).

## <a name="modern-development-support"></a>Supporto per lo sviluppo moderno

### <a name="manage-pull-requests-prs-from-the-ide"></a>Gestire le richieste pull (PR) dall'IDE

È ora possibile scaricare una nuova estensione da usare con Visual Studio 2019 Preview. Questa nuova estensione consente di esaminare, eseguire e addirittura eseguire il debug delle richieste pull del team senza uscire dall'[ambiente di sviluppo integrato](../get-started/visual-studio-ide.md) (IDE) di Visual Studio. Il codice è attualmente supportato in Azure Repos, ma è previsto anche il supporto in GitHub per un miglioramento dell'esperienza complessiva.

Per iniziare subito, scaricare l'estensione [Richieste pull per Visual Studio](https://aka.ms/pr4vs) da Visual Studio Marketplace.

### <a name="develop-with-net-core-3-preview-1"></a>Sviluppare con .NET Core 3 Preview 1

La versione di anteprima di Visual Studio 2019 supporta la creazione di applicazioni [.NET Core 3](http://aka.ms/netcore3preview1) per qualsiasi piattaforma. Microsoft continuerà a supportare e migliorare lo sviluppo in C++ multipiattaforma, nonché lo sviluppo per dispositivi mobili in .NET per iOS e Android con Xamarin.

   ![Sviluppare app con .NET Core 3 Preview 1 in Visual Studio 2019](../ide/media/dot-net-core-three-dev.png)

## <a name="continuous-innovation"></a>Innovazione continua

### <a name="per-monitor-aware-pma-rendering"></a>Rendering sensibile ai valori del monitor (PMA)

Se si usano monitor configurati con fattori di scala per lo schermo differenti o ci si connette in remoto a un computer con fattori di scala per lo schermo diversi dal dispositivo principale, si può notare che Visual Studio sembra sfocato o esegue il rendering con una scala errata.

Con la versione di Visual Studio 2019 Preview 1, Visual Studio si sta gradatamente trasformando in un'applicazione sensibile ai valori del monitor (PMA). Visual Studio sarà sempre più in grado di eseguire correttamente il rendering, indipendentemente dai fattori di scala per lo schermo in uso.

   ![Rendering sensibile ai valori del monitor (PMA) in Visual Studio 2019](../ide/media/per-monitor-aware-dpi-scaling.png)

### <a name="visual-studio-intellicode"></a>Visual Studio IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) è un'estensione che ottimizza le attività di sviluppo software con l'uso dell'intelligenza artificiale. IntelliCode esegue il training tra 2000 progetti open source su GitHub&mdash;ognuno con oltre 100 stelle&mdash;per generare raccomandazioni.

Ecco alcuni modi in cui Visual Studio IntelliCode può essere utile per migliorare la produttività:

* Completamento del codice con riconoscimento del contesto
* Guida per gli sviluppatori per il rispetto dei criteri e degli stili usati dal team
* Individuazione di problemi del codice difficili da trovare
* Revisioni del codice mirate, che pongono al centro dell'attenzione le aree realmente importanti

Per la versione di anteprima dell'estensione IntelliCode per Visual Studio è stato inizialmente previsto solo il supporto per C#. Attualmente è disponibile anche il supporto per C++ e XAML in Visual Studio.

Per chi usa C#, è stata inoltre aggiunta la possibilità di eseguire il training di un modello personalizzato nel proprio codice.

Per altre informazioni sugli aggiornamenti recenti, vedere il post di blog [Visual Studio IntelliCode supports more languages and learns from your code](https://blogs.msdn.microsoft.com/visualstudio/2018/12/05/visual-studio-intellicode-supports-more-languages-and-learns-from-your-code/) (Visual Studio IntelliCode supporta più lingue e apprende dal codice creato dall'utente). E per altre informazioni sull'estensione e su come scaricarla, vedere la pagina della [versione di anteprima di Visual Studio IntelliCode](https://go.microsoft.com/fwlink/?linkid=872707) in Microsoft DevLabs.

## <a name="give-us-feedback"></a>Commenti e suggerimenti

È possibile inviare commenti e suggerimenti al team di Visual Studio. Microsoft prende infatti in seria considerazione i commenti e suggerimenti ricevuti dai clienti, usandoli per migliorare i propri prodotti.

* Se si vuole inviare un suggerimento per il miglioramento di Visual Studio, è possibile usare lo strumento [Invia un suggerimento](../ide/talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features).

* Se si verifica un blocco, un arresto anomalo del sistema o un altro problema di prestazioni, è possibile condividere facilmente con Microsoft la procedura per riprodurre il problema e i file di supporto usando lo strumento [Segnala un problema](../ide/talk-to-us.md#i-want-to-report-a-problem-with-visual-studio).

## <a name="see-also"></a>Vedere anche

* [Note sulla versione di Visual Studio 2019](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)
* [Microsoft Connect(); 2018 conference](https://www.microsoft.com/connectevent)
* [Novità di Visual Studio 2017](whats-new-in-visual-studio.md)
