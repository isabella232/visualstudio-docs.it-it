---
title: Novità di Visual Studio 2019
titleSuffix: ''
description: Informazioni sulle nuove funzionalità di Visual Studio 2019.
ms.date: 02/08/2019
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 4667fd19f59453e9efc856aefeaaf8d43aff302d
ms.sourcegitcommit: 61dc40d6c707f8c79779ec1091b296530d5a7b81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987418"
---
# <a name="whats-new-in-visual-studio-2019-preview"></a>Novità di Visual Studio 2019 Preview

**Aggiornato per la [versione Preview 2](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)**

>[!div class="button"]
>[Scaricare l'anteprima](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+preview)

Visual Studio 2019 Preview include molti miglioramenti di carattere generale e nuove funzionalità che ottimizzano la produttività degli sviluppatori e la collaborazione in team. Indipendentemente dal fatto che si usi Visual Studio per la prima volta o lo si stia usando da anni, sarà possibile sfruttarne le funzionalità per tutti gli aspetti del ciclo di vita di sviluppo, dalla creazione di progetti e gestione dell'integrità del codice semplificate ai flussi di lavoro collaborativi open source e per i team.<br/><br/>

>[!VIDEO https://channel9.msdn.com/Events/Connect/Microsoft-Connect--2018/D190/player]

Ecco un riepilogo generale delle funzionalità offerte da Visual Studio:

* **[Produttività personale e in team](#personal-and-team-productivity)**. Produttività per tutti gli utenti dove è più necessaria.
* **[Supporto per lo sviluppo moderno](#modern-development-support)**. Supporto per i progetti correnti e le soluzioni future.
* **[Innovazione continua](#continuous-innovation)**. Codifica semplificata con supporto intelligente basato sul cloud.

> [!NOTE]
> Per un elenco completo delle nuove funzionalità di Visual Studio 2019 Preview, vedere le [note sulla versione](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017). Per una panoramica delle novità della seconda anteprima, vedere il post di blog [Visual Studio 2019 Preview 2 is now available](https://blogs.msdn.microsoft.com/visualstudio/2019/01/24/visual-studio-2019-preview-2-is-now-available/) (Visual Studio 2019 Preview 2 è ora disponibile).

## <a name="personal-and-team-productivity"></a>Produttività personale e in team

È un dato di fatto che i miglioramenti delle prestazioni sono l'obiettivo principale di ogni nuova versione di Visual Studio, ma vanno di pari passo con il miglioramento della produttività. Ecco quali sono le funzionalità principali.

### <a name="new-start-window"></a>Nuova finestra iniziale

La prima cosa che si nota quando si apre Visual Studio 2019 è la nuova finestra iniziale.

   ![Nuova finestra iniziale in Visual Studio 2019](media/start-window.png)

Questa nuova finestra iniziale offre una serie di opzioni per clonare o estrarre il codice, aprire un progetto o una soluzione, aprire una cartella locale o creare un nuovo progetto. Il fatto che queste opzioni siano immediatamente disponibili in una finestra di dialogo semplice consente sia ai principianti che agli utenti avanzati di Visual Studio di creare codice rapidamente.

Per altre informazioni, vedere il post di blog [Get to code: How we designed the new Visual Studio start window](https://blogs.msdn.microsoft.com/visualstudio/2018/12/13/get-to-code-how-we-designed-the-new-visual-studio-start-window/) (Vai al codice: come è stata progettata la nuova finestra iniziale di Visual Studio).

### <a name="better-search"></a>Ricerca migliorata

Precedentemente nota come Avvio veloce, la nuova esperienza di ricerca è più rapida ed efficiente. Ora i risultati della ricerca vengono visualizzati dinamicamente durante la digitazione. Includono inoltre tasti di scelta rapida per i comandi, in modo che sia possibile memorizzarli in modo più immediato per usarli in futuro.

   ![Nuova funzionalità di ricerca in Visual Studio 2019](media/search-feature.png)

Indipendentemente dal fatto che si stiano cercando comandi, impostazioni, documentazione o altri elementi utili, la nuova funzionalità di ricerca rende più semplice trovare quello che si sta cercando.

### <a name="one-click-code-cleanup"></a>Pulizia del codice con un clic

Abbinato a un nuovo indicatore di integrità dei documenti è disponibile un nuovo comando per la pulizia del codice. È possibile usare questo nuovo comando per identificare e quindi risolvere avvisi e suggerimenti con il semplice clic di un pulsante.

   ![Nuova funzionalità di pulizia del codice in Visual Studio 2019](media/code-cleanup.png)

L'operazione di pulizia formatterà il codice e applicherà eventuali correzioni del codice come suggerito dalle [impostazioni correnti](code-styles-and-quick-actions.md), dai [file con estensione editorconfig](create-portable-custom-editor-options.md) o dagli [analizzatori di Roslyn](../code-quality/roslyn-analyzers-overview.md).

### <a name="debugger-improvements"></a>Miglioramenti del debugger

#### <a name="search-within-a-watch-window-and-format-watch-values"></a>Eseguire ricerche all'interno di una finestra Espressioni di controllo e formattare i valori di Espressioni di controllo

Probabilmente la finestra Espressioni di controllo è già stata usata in precedenza, magari per la ricerca di una stringa tra un set di valori. In Visual Studio 2019 Preview è stata aggiunta la funzionalità di ricerca nelle finestre Espressioni di controllo, Variabili locali e Auto per consentire la ricerca degli oggetti e dei valori richiesti.

È anche possibile formattare il modo in cui un valore viene visualizzato all'interno delle finestre Espressioni di controllo, Variabili locali e Auto.  Fare doppio clic su uno degli elementi in una qualsiasi delle finestre e aggiungere una virgola (",") per accedere all'elenco a discesa dei possibili identificatori di formato, ognuno dei quali include una descrizione del relativo effetto desiderato.

   ![Nuova finestra Espressioni di controllo e funzionalità di formattazione dei valori in Visual Studio 2019](media/search-watch-window.png)

Per altre informazioni, vedere il post di blog [Enhanced in Visual Studio 2019: Search for Objects and Properties in the Watch, Autos, and Locals Windows](https://blogs.msdn.microsoft.com/visualstudio/2019/01/28/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) (Miglioramenti di Visual Studio 2019: Ricerca di oggetti e proprietà nelle finestre Espressione di controllo, Auto e Variabili locali).

### <a name="visual-studio-live-share"></a>Visual Studio Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) è un servizio per sviluppatori che consente di condividere una codebase e il relativo contesto con un collega e ottenere collaborazione bidirezionale immediata direttamente all'interno di Visual Studio. Con Live Share un collega può leggere, esplorare, modificare ed eseguire il debug di un progetto condiviso da un altro utente, in modo facile e sicuro.

Con Visual Studio 2019 Preview, questo servizio viene installato per impostazione predefinita.

   ![Un file GIF animato che illustra la funzionalità di collaborazione Live Share in Visual Studio 2019](media/live-share-collaboration.gif)

Per altre informazioni, vedere il post di blog [Visual Studio Live Share for real-time code reviews and interactive education](https://blogs.msdn.microsoft.com/visualstudio/2018/12/06/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) (Visual Studio Live Share per revisioni del codice in tempo reale e formazione interattiva).

## <a name="modern-development-support"></a>Supporto per lo sviluppo moderno

### <a name="manage-pull-requests-prs-from-the-ide"></a>Gestire le richieste pull (PR) dall'IDE

È ora possibile scaricare una nuova estensione da usare con Visual Studio 2019 Preview. Questa nuova estensione consente di esaminare, eseguire e addirittura eseguire il debug delle richieste pull del team senza uscire dall'[ambiente di sviluppo integrato](../get-started/visual-studio-ide.md) (IDE) di Visual Studio. Il codice è attualmente supportato in Azure Repos, ma è previsto anche il supporto in GitHub per un miglioramento dell'esperienza complessiva.

Per iniziare subito, scaricare l'estensione [Richieste pull per Visual Studio](https://aka.ms/pr4vs) da Visual Studio Marketplace.

### <a name="develop-with-net-core-3-preview"></a>Sviluppare con .NET Core 3 Preview

La versione di anteprima di Visual Studio 2019 supporta la creazione di applicazioni [.NET Core 3](https://dotnet.microsoft.com/download/dotnet-core/3.0) per qualsiasi piattaforma. Microsoft continuerà a supportare e migliorare lo sviluppo in C++ multipiattaforma, nonché lo sviluppo per dispositivi mobili in .NET per iOS e Android con Xamarin.

   ![Sviluppare app con .NET Core 3 Preview in Visual Studio 2019](media/dot-net-core-three-dev.png)

Per ulteriori informazioni, vedere i seguenti argomenti:

* Note sulla versione di [.NET Core 3 Preview 1](https://github.com/dotnet/core/blob/master/release-notes/3.0/preview/3.0.0-preview1.md) e [.NET Core 3 Preview 2](https://github.com/dotnet/core/blob/master/release-notes/3.0/preview/3.0.0-preview2.md)
* Post di blog di annuncio delle versioni di anteprima: [Announcing .NET Core 3 Preview 1](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/) e [Announcing .NET Core 3 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2019/01/29/announcing-net-core-3-preview-2/)

## <a name="continuous-innovation"></a>Innovazione continua

### <a name="per-monitor-aware-pma-rendering"></a>Rendering sensibile ai valori del monitor (PMA)

Se si usano monitor configurati con fattori di scala per lo schermo differenti o ci si connette in remoto a un computer con fattori di scala per lo schermo diversi dal dispositivo principale, si può notare che Visual Studio sembra sfocato o esegue il rendering con una scala errata.

Con la versione di Visual Studio 2019 Preview, Visual Studio si sta gradatamente trasformando in un'applicazione sensibile ai valori del monitor (PMA). Visual Studio sarà sempre più in grado di eseguire correttamente il rendering, indipendentemente dai fattori di scala per lo schermo in uso.

   ![Rendering sensibile ai valori del monitor (PMA) in Visual Studio 2019](media/per-monitor-aware-dpi-scaling.png)

Per altre informazioni, vedere il post di blog [Better multi-monitor experience with Visual Studio 2019](https://blogs.msdn.microsoft.com/visualstudio/2019/02/07/a-better-multi-monitor-experience-with-visual-studio-2019/) (Esperienza con più monitor migliore con Visual Studio 2019).

### <a name="visual-studio-intellicode"></a>Visual Studio IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) è un'estensione che ottimizza le attività di sviluppo software con l'uso dell'intelligenza artificiale. IntelliCode esegue il training tra 2000 progetti open source su GitHub&mdash;ognuno con oltre 100 stelle&mdash;per generare raccomandazioni.

Ecco alcuni modi in cui Visual Studio IntelliCode può essere utile per migliorare la produttività:

* Completamento del codice con riconoscimento del contesto
* Guida per gli sviluppatori per il rispetto dei criteri e degli stili usati dal team
* Individuazione di problemi del codice difficili da trovare
* Revisioni del codice mirate, che pongono al centro dell'attenzione le aree realmente importanti

 ![Esempio di un suggerimento IntelliSense](media/intellicode-intellisense-suggestion.png)

Per la versione di anteprima dell'estensione IntelliCode per Visual Studio è stato inizialmente previsto solo il supporto per C#. Attualmente è disponibile anche il supporto per C++ e XAML in Visual Studio.

Per chi usa C#, è stata inoltre aggiunta la possibilità di eseguire il training di un modello personalizzato nel proprio codice.

Per altre informazioni sugli aggiornamenti recenti, vedere il post di blog [Visual Studio IntelliCode supports more languages and learns from your code](https://blogs.msdn.microsoft.com/visualstudio/2018/12/05/visual-studio-intellicode-supports-more-languages-and-learns-from-your-code/) (Visual Studio IntelliCode supporta più lingue e apprende dal codice creato dall'utente). E per altre informazioni sull'estensione e su come scaricarla, vedere la pagina della [versione di anteprima di Visual Studio IntelliCode](https://go.microsoft.com/fwlink/?linkid=872707) in Microsoft DevLabs.

## <a name="give-us-feedback"></a>Commenti e suggerimenti

È possibile inviare commenti e suggerimenti al team di Visual Studio. Microsoft prende infatti in seria considerazione i commenti e suggerimenti ricevuti dai clienti, usandoli per migliorare i propri prodotti.

* Se si vuole inviare un suggerimento per il miglioramento di Visual Studio, è possibile usare lo strumento [Invia un suggerimento](talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features).

* Se si verifica un blocco, un arresto anomalo del sistema o un altro problema di prestazioni, è possibile condividere facilmente con Microsoft la procedura per riprodurre il problema e i file di supporto usando lo strumento [Segnala un problema](talk-to-us.md#i-want-to-report-a-problem-with-visual-studio).

## <a name="see-also"></a>Vedere anche

* [Note sulla versione di Visual Studio 2019](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)
* [Microsoft Connect(); 2018 conference](https://www.microsoft.com/connectevent)
* [Novità di Visual Studio 2017](whats-new-visual-studio-2017.md)
