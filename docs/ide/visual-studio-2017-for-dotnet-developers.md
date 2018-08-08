---
title: Aumentare la produttività per lo sviluppo .NET
description: Panoramica di esplorazione, analisi del codice, testing unità e altre funzionalità che consentono di scrivere codice .NET in modo più efficiente e veloce.
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.date: 06/14/2018
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: d0f7ffbef8fade3e5723a84ac433ce95679c26c3
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381094"
---
# <a name="visual-studio-2017-c-productivity-guide"></a>Guida sulla produttività di Visual Studio 2017 in C#

[Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) consente agli sviluppatori di essere ancora più produttivi, grazie ai miglioramenti che interessano prestazioni e produttività, come l'esplorazione di assembly decompilati, suggerimenti di nomi di variabili durante la digitazione, una visualizzazione della gerarchia in **Esplora test**, l'uso di Vai a tutti (**CTRL**+**T**) per passare alle dichiarazioni di file/tipo/membro/simbolo, un **Helper eccezioni** intelligente, configurazione e imposizione dello stile del codice e molti refactoring e correzioni del codice.

##  <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Tasti di scelta rapida provenienti da un'estensione/editor/IDE diversi.

**Novità in Visual Studio 2017 versione 15.8** Se si passa da un IDE o un ambiente di codifica diverso, è possibile modificare lo schema della tastiera per *Visual Studio Code* o *ReSharper (Visual Studio)*:

![Schemi della tastiera di Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Alcune estensioni offrono anche gli schemi della tastiera:
- [HotKeys per Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emulazione Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Di seguito sono riportate alcune combinazioni di tasti di scelta rapida comuni di Visual Studio:

| Tasti di scelta rapida (tutti i profili) | Comando | Descrizione |
|-|-|-|
| **CTRL**+**T** | Vai a tutti | Consente di passare a qualsiasi dichiarazione di file/tipo/membro/simbolo |
| **F12** (o **CTRL**+**clic**) | Vai a definizione | Consente di passare al punto in cui si trova la definizione di un simbolo |
| **CTRL**+**F12** | Vai all'implementazione | Consente di passare da un tipo o membro di base alle varie implementazioni di questo. |
| **MAIUSC**+**F12** | Trova tutti i riferimenti | Consente di visualizzare tutti i riferimenti di simboli o valori letterali |
| **CTRL**+**.** (o **ALT**+**INVIO** in profilo C# ) | Azioni rapide e refactoring | Visualizza le correzioni e le azioni di generazione di codice, i refactoring e altre azioni rapide disponibili in corrispondenza della posizione del cursore o del codice selezionato |
| **Ctrl**+**D** | Duplicare una riga | Duplica la riga di codice in cui si trova il cursore (disponibile in **Visual Studio 2017 versione 15.6** e versioni successive) |
| **MAIUSC**+**ALT**+**+**/**-** | Espandi/Comprimi selezione | Espande o comprime la selezione corrente nell'editor (disponibile in **Visual Studio 2017 versione 15.5** e versioni successive) |
| **MAIUSC** + **ALT** + **INS** | Inserisci punto di inserimento corrispondente successivo | Aggiunge una selezione e un punto di inserimento nella posizione successiva che corrisponde alla selezione corrente (disponibile in **Visual Studio 2017 versione 15.8** e versioni successive) |
| **CTRL**+**Q** | Avvio veloce | Consente di effettuare una ricerca all'interno di tutte le impostazioni di Visual Studio |
| **F5** | Avvia debug | Avvia il debug dell'applicazione |
| **CTRL**+**F5** | Esecuzione senza debug | Esegue l'applicazione in locale senza debug |
| **CTRL**+**K**,**D** (profilo predefinito) o **CTRL**+**E**,**D** (profilo C#) | Formatta documento | Corregge le violazioni alle regole di formattazione nel file in base alle impostazioni relative alle nuove righe, alla spaziatura e ai rientri |
| **CTRL**+**\\**,**E** (profilo predefinito) o **CTRL**+**W**,**E** (profilo C#) | Visualizzazione dell'elenco errori | Consente di visualizzare tutti gli errori nel documento, nel progetto o nella soluzione |
| **ALT** + **PGSU/PGGIÙ** | Passa a problema successivo/precedente | Passa all'errore, avviso, suggerimento precedente/successivo nel documento (disponibile in **Visual Studio 2017 versione 15.8** e versioni successive) |

> [!NOTE]
> Alcune estensioni separano i tasti di scelta rapida predefiniti di Visual Studio. Per usare i comandi riportati in precedenza, ripristinare i tasti di scelta rapida sui valori predefiniti di Visual Studio in **Strumenti** > **Importa/Esporta impostazioni** > **Reimposta tutte le impostazioni** oppure **Strumenti** > **Opzioni** > **Tastiera** > **Reimposta**.

Altre informazioni sui tasti di scelta rapida e sui comandi sono disponibili nella [documentazione](..\ide\tips-and-tricks-for-visual-studio.md) di Visual Studio.

## <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>Serve un modo per spostarsi velocemente su file o tipi.
Visual Studio 2017 offre una funzionalità denominata **Vai a tutti** (**CTRL**+**T**). Vai a tutti consente di passare rapidamente a qualsiasi dichiarazione di file, tipo, membro o simbolo.
- Cambiare la posizione di questa barra di ricerca o disattivare 'anteprima di navigazione in tempo reale' con l'icona **ingranaggio**
- Filtrare i risultati usando la sintassi di query (ad esempio, "mytype t"). È inoltre possibile limitare l'ambito di ricerca al documento corrente.
- La corrispondenza camelCase è supportata.

![Vai a tutti in Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Il team impone regole di stile del codice nel CodeBase.
È possibile usare un file con estensione *editorconfig* per codificare le convenzioni di codifica e spostarle con l'origine.
- È consigliabile installare l'[estensione dei servizi di linguaggio EditorConfig](https://aka.ms/editorconfig) per aggiungere e modificare un file con estensione *editorconfig* in Visual Studio.
- Vedere la [documentazione](https://aka.ms/editorconfigDocs) per tutte le opzioni delle convenzioni di codifica di .NET.
- Vedere [questo gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) per un esempio di file con estensione *editorconfig*.

![Imposizione dello stile del codice in Visual Studio](../ide/media/VSGuide_CodeStyle.png)

## <a name="i-need-more-refactorings-and-code-fixes"></a>Servono ulteriori refactoring e correzioni del codice.
Visual Studio 2017 include molti refactoring, azioni di generazione del codice e correzioni del codice. Le sottolineature rosse rappresentano errori, quelle verdi rappresentano gli avvisi e tre punti grigi rappresentano suggerimenti per il codice. È possibile accedere alle correzioni del codice facendo clic sull'icona lampadina/cacciavite o premendo **CTRL**+**.** oppure **ALT**+**INVIO**. Ogni correzione è dotata di una finestra di anteprima che mostra come funziona la correzione in un diff di codice live.

- Le correzioni rapide e i refactoring più comuni includono:
  - *Rinomina*
  - *Estrai metodo*
  - *Cambia firma metodo*
  - *Genera costruttore*
  - *Genera metodo*
  - *Sposta il tipo in File*
  - *Aggiungi il controllo Null*
  - *Aggiungi parametro*
  - *Rimuovi istruzioni using non necessarie*
  - Per altre informazioni, vedere la [documentazione](https://aka.ms/refactorings)
- È possibile scrivere un proprio refactoring o correzione del codice con gli [analizzatori Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix).
- Diversi membri della community hanno scritto estensioni gratuite che aggiungono controlli aggiuntivi del codice:
  - [Analizzatori FXCop](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)
  - [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
  - [SonarLint per Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
  - [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)

![Refactoring in Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>Accesso agli utilizzi, all'implementazione e alle origini decompilate
Visual Studio 2017 include molte funzionalità che consentono di eseguire ricerche nella codebase e di esplorarla. Sono disponibili altre informazioni sulle [funzionalità di esplorazione del codice](../ide/navigating-code.md)

| Funzionalità | Collegamento | Dettagli/Miglioramenti |
|- | - | -|
| Trova tutti i riferimenti | **MAIUSC**+**F12**| I risultati sono colorati e possono essere raggruppati per progetto, definizione e così via. È anche possibile "bloccare" i risultati. |
| Vai all'implementazione | **CTRL**+**F12** | È possibile usare Vai a definizione nella parola chiave `override` per passare al membro sostituito |
| Vai a definizione | **F12** o **CTRL**+**clic**| È possibile tenere premuto **CTRL** mentre si fa clic per passare alla definizione |
| Visualizza definizione | **ALT**+**F12** | Visualizzazione inline di una definizione |
| Visualizzatore di struttura | Linee grigie tratteggiate tra parentesi graffe | Passare il mouse per visualizzare la struttura del codice |
| Spostamento agli assembly decompilati | **F12** o **CTRL**+**clic** | Passare all'origine esterna (decompilata con ILSpy) abilitando la funzionalità: **Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Avanzate** > **Abilita spostamento a origini decompilate**. |

![Vai a tutti e Trova tutti i riferimenti](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="i-want-to-run-and-see-my-unit-tests"></a>Eseguire e visualizzare gli unit test.
Sono stati apportati numerosi miglioramenti all'esperienza di test in Visual Studio 2017. Usare una delle esperienze di testing unità con i framework di test MSTest v1, MSTest v2, NUnit o XUnit.
- L'individuazione dei test di **Esplora test** è rapida nella versione 15.6. Per risultati ottimali, eseguire l'aggiornamento alla versione più recente dell'adattatore di test.
- Organizzare i test in Esplora test con il nuovo *ordinamento gerarchico* della versione 15.6.
- [Live Unit Testing](../test/live-unit-testing.md) esegue in modo continuo i test interessati dalle modifiche del codice e aggiorna le icone dell'editor inline per comunicare lo stato dei test. Includere o escludere progetti di test o test specifici dal *set di test attivi*.

![Visualizzazione della gerarchia per Esplora test in Visual Studio](../ide/media/VSGuide_Testing.png)

## <a name="i-want-to-debug-my-code"></a>Eseguire il debug del codice
Sono state aggiunte moltissime nuove funzionalità di debug in Visual Studio 2017.
- L'*esecuzione fino alla riga selezionata* consente di passare il puntatore del mouse accanto a una riga di codice, fare clic sull'icona verde di riproduzione ed eseguire il programma fino a raggiungere tale riga.
- Il nuovo **Helper eccezioni** inserisce le informazioni più importanti, ad esempio la variabile "null" in un'eccezione NullReferenceException, al primo livello della finestra di dialogo.
- Il debug [Torna indietro](../debugger/how-to-use-intellitrace-step-back.md) consente di tornare ai punti di interruzione o ai passaggi precedenti e visualizzare lo stato precedente dell'applicazione.
- [Debug snapshot](/azure/application-insights/app-insights-snapshot-debugger) consente di esaminare lo stato di un'applicazione Web attiva nel momento in cui è stata generata un'eccezione (è necessario essere in Azure).

![Nuovo Helper eccezioni in Visual Studio 2017](../ide/media/VSGuide_Debugging.png)

## <a name="i-want-to-use-version-control-with-my-projects"></a>Usare il controllo della versione con i progetti
È possibile usare Git o il controllo della versione di Team Foundation per archiviare e aggiornare il codice in Visual Studio.
- Organizzare le modifiche locali con **Team Explorer** e usare la barra di stato per tenere traccia di commit e modifiche in sospeso.
- Configurare l'integrazione e il recapito continui per i progetti all'interno di Visual Studio con l'estensione [Strumenti di recapito continuo per Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) e adottare il flusso di lavoro di sviluppo agile.

![Controllo del codice sorgente in Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-do-i-need-to-know-about"></a>Quali altre funzionalità occorre conoscere
Ecco un elenco di funzionalità editor e di produttività per rendere più efficiente la scrittura del codice. È possibile che alcune funzionalità debbano essere abilitate perché disabilitate per impostazione predefinita in quanto potrebbero indicizzare elementi del computer, essere controverse o essere ancora in forma sperimentale.

| Funzionalità | Dettagli | Abilitazione |
|-|-|-|
| Individuare il file in Esplora soluzioni | Evidenzia il file attivo in **Esplora soluzioni** | **Strumenti** > **Opzioni** > **Progetti e soluzioni** > **Tieni traccia degli elementi attivi in Esplora soluzioni** |
| Aggiungere le direttive using per i tipi in assembly di riferimento e pacchetti NuGet | Visualizza un'icona a forma di lampadina con una correzione del codice per installare un pacchetto NuGet per un tipo senza riferimenti | **Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Avanzate** > **Suggerisci le direttive using per i tipi in assembly di riferimento** e **Suggerisci le direttive using per i tipi in pacchetti NuGet** |
| Abilita analisi della soluzione completa | Visualizza tutti gli errori della soluzione in **Elenco errori** | **Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Avanzate** > **Abilita analisi della soluzione completa** |
| Abilita spostamento a origini decompilate | Consente l'uso di Vai a definizione per tipi o membri di origini esterne e del decompilatore ILSpy per visualizzare i corpi dei metodi | **Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Avanzate** > **Abilita spostamento a origini decompilate** |
| Modalità di terminazione/suggerimento | Modifica il comportamento del completamento in IntelliSense. Gli sviluppatori con esperienza IntelliJ tendono a cambiare l'impostazione predefinita in questo punto | **Menu** > **Modifica** > **IntelliSense** > **Attiva/disattiva modalità di terminazione** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Visualizza le informazioni di riferimento del codice e la cronologia modifiche nell'editor | **Strumenti** > **Opzioni** > **Editor di testo** > **Tutti i linguaggi** > **CodeLens** |
| [Frammenti di codice](../ide/visual-csharp-code-snippets.md) | Consente di generare il boilerplate comune |  Digitare un nome di frammento di codice e premere **TAB** due volte. |

## <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Manca una funzionalità che migliora la produttività o le prestazioni sono scadenti?
Esistono diversi modi per inviare commenti e suggerimenti:
- Registrare richieste di funzionalità .NET nell'[archivio GitHub](https://github.com/dotnet/roslyn/issues).
- Per registrare richieste di funzionalità, bug e problemi di prestazioni di Visual Studio usare l'icona **Commenti e suggerimenti** in alto a destra nella finestra di Visual Studio.
