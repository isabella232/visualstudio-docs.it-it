---
title: Visual Studio 2017 per sviluppatori .NET | Microsoft Docs
description: Panoramica delle funzionalità di Visual Studio 2017 che consentono di scrivere codice .NET più efficiente in modo più veloce.
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.date: 01/16/2018
ms.topic: article
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 7e910c50682d45d209d993cb883ca01d1ea436f2
ms.sourcegitcommit: 236c250bb97abdab99d00c6525d106fc0035d7d0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2018
---
# <a name="visual-studio-2017-productivity-guide-for-net-developers"></a>Guida per la produttività di Visual Studio 2017 per gli sviluppatori .NET

- [Guida per la produttività](#guide)
- [Panoramica di Visual Studio 2017](#overview)

## <a name="a-idguide-productivity-guide"></a><a id="guide"/>Guida per la produttività
[Visual Studio 2017](https://www.visualstudio.com/downloads/) consente agli sviluppatori di essere più produttivi che mai! Sono migliorate le prestazioni e l'affidabilità della soluzione in merito all'avvio, al caricamento, all'individuazione di test e alla latenza della digitazione. Sono state anche aggiunte e migliorate le funzionalità che aiutano a scrivere codice più efficace in modo più veloce. Alcune di queste funzionalità sono: navigazione su assembly decompilati, suggerimento di nomi di variabili durante la digitazione, vista gerarchia in Esplora test, utilizzo di Vai a tutti (**Ctrl + T**) per passare alle dichiarazioni di file/tipo/membro/simbolo, Helper eccezioni intelligente, configurazione e imposizione dello stile del codice e vari refactoring e correzioni del codice. 

Attenersi a questa guida per ottimizzare la produttività.

###  <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Tasti di scelta rapida provenienti da un'estensione/editor/IDE diversi.

Se fino a questo momento si è usato un altro ambiente IDE o di stesura di codice, può essere utile installare una di queste estensioni:

- [Emulazione Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [HotKeys per Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Di seguito sono riportate alcune combinazioni di tasti di scelta rapida comuni di Visual Studio. 

> [!NOTE]
> Dal momento che alcune estensioni annullano le combinazioni di tasti di scelta rapida, per usare i comandi riportati di seguito è necessario ripristinarle. Ripristinare i tasti di scelta rapida per le impostazioni predefinite di Visual Studio in **Strumenti > Importa/Esporta impostazioni... > Reimposta tutte le impostazioni** oppure **Strumenti > Opzioni > Tastiera > Reimposta**.

| Tasti di scelta rapida (tutti i profili) | Comando | Descrizione |
|-|-|-|
| **Ctrl+T** | Vai a tutti | Consente di passare a qualsiasi dichiarazione di file/tipo/membro/simbolo |
| **F12** (o **Ctrl + clic**) | Vai a definizione | Consente di passare al punto in cui si trova la definizione di un simbolo |
| **Ctrl+F12** | Vai all'implementazione | Consente di passare da un tipo o membro di base alle varie implementazioni di questo. |
| **Maiusc+F12** | Trova tutti i riferimenti | Consente di visualizzare tutti i riferimenti di simboli o valori letterali |
| **CTRL**+**.** (o **Alt+Enter** in Profilo C#) | Azioni rapide e refactoring | Visualizza le correzioni e le azioni di generazione di codice, i refactoring e altre azioni rapide disponibili in corrispondenza della posizione del cursore o del codice selezionato |
| **Ctrl**+**D** | Duplicare una riga | Duplica la riga di codice in cui si trova il cursore (disponibile in **Visual Studio 2017 versione 15.6** e versioni successive) |
| **MAIUSC**+**ALT**+**+**/**-** | Espandi/Comprimi selezione | Espande o comprime la selezione corrente nell'editor (disponibile in **Visual Studio 2017 versione 15.5** e versioni successive) |
| **Ctrl+Q** | Avvio veloce | Consente di effettuare una ricerca all'interno di tutte le impostazioni di Visual Studio |
| **F5** | Avvia debug | Avvia il debug dell'applicazione |
| **Ctrl+F5** | Esecuzione senza debug | Esegue l'applicazione in locale senza debug |
| **Ctrl+K,D** (profilo predefinito) o **Ctrl+E,D** (profilo C#) | Formatta documento | Corregge le violazioni alle regole di formattazione nel file in base alle impostazioni relative alle nuove righe, alla spaziatura e ai rientri |
| **CTRL+\\,E** (profilo predefinito) o **CTRL+W,E** (profilo C#) | Visualizzazione dell'elenco errori | Consente di visualizzare tutti gli errori nel documento, nel progetto o nella soluzione |

### <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>Serve un modo per spostarsi velocemente su file o tipi.
Visual Studio 2017 dispone di una funzionalità denominata _Vai a tutti_ (**Ctrl + T**). Vai a tutti consente di passare rapidamente a qualsiasi dichiarazione di file, tipo, membro o simbolo.
- Cambiare la posizione di questa barra di ricerca o disattivare 'anteprima di navigazione in tempo reale' con l'icona **ingranaggio**
- Filtrare i risultati usando la sintassi di query (ad esempio, "mytype t"). È inoltre possibile limitare l'ambito di ricerca al documento corrente.
- La corrispondenza camelCase è supportata.

![Vai a tutti in Visual Studio](../ide/media/VS2017Guide-go-to-all.png "VS2017Guide-go-to-all")

### <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Il team impone regole di stile del codice nel CodeBase.
È possibile utilizzare un file .editorconfig per codificare le convenzioni di scrittura codice. Si consiglia di installare l'[estensione dei servizi di linguaggio EditorConfig](https://aka.ms/editorconfig) per aggiungere e modificare un file .editorconfig. Si consiglia di consultare la [documentazione](https://aka.ms/editorconfigDocs) per tutte le opzioni delle convenzioni di scrittura codice di .NET.

Consultare [questo gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) per un esempio di .editorconfig.

![Imposizione dello stile del codice in Visual Studio code](../ide/media/VS2017Guide-code-style.png "VS2017Guide-code-style")

### <a name="i-need-more-refactorings-and-code-fixes"></a>Servono ulteriori refactoring e correzioni del codice.
Visual Studio 2017 viene fornito con molti refactoring, azioni di generazione del codice e correzioni del codice visualizzabili nella [documentazione](https://aka.ms/refactorings). Le sottolineature rosse rappresentano errori, quelle verdi rappresentano gli avvisi e tre punti grigi rappresentano suggerimenti per il codice.

È possibile accedere alle correzioni del codice facendo clic sull'icona lampadina/cacciavite o premendo **Ctrl +.** oppure **ALT+INVIO**. Ogni correzione è dotata di una finestra di anteprima che mostra come funziona la correzione in un diff di codice live.

Ecco alcuni esempi delle correzioni rapide e dei refactoring più diffusi: Rinomina, Estrai metodo, Cambia firma metodo, Genera costruttore, Genera metodo, Sposta il tipo in file, Aggiungi il controllo Null, Aggiungi parametro, Rimuovi istruzioni using non necessarie.

I refactoring e le correzioni di codice possono essere scritti facilmente con gli [analizzatori Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix). Diversi membri della community hanno scritto estensioni *gratuite* che aggiungono ulteriori controlli del codice: Roslynator e SonarLint per Visual Studio. 

![Refactoring in Visual Studio](../ide/media/VS2017Guide-refactoring.png "VS2017Guide-refactoring")

### <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>Accesso agli utilizzi, all'implementazione e alle origini decompilate
Visual Studio 2017 è dotato di molte funzionalità che consentono di eseguire ricerche e di spostarsi nel codebase, tra queste ci sono Trova tutti i riferimenti (**MAIUSC+F12**), Vai all'implementazione (**CTRL+F12**), Vai a definizione (**F12** oppure **CTRL+clic**). La funzionalità di spostamento alle origini decompilate è stata aggiunta nella versione 15.6. Per attivare questa funzionalità selezionare **Strumenti > Opzioni > Editor di testo > C# > Avanzate > Abilita spostamento a origini decompilate**.

![Spostamento a origini decompilate in Visual Studio](../ide/media/VS2017Guide-navigate-to-source.png "VS2017Guide-navigate-to-source")

### <a name="i-want-to-run-and-see-my-unit-tests"></a>Eseguire e visualizzare gli unit test.
Sono disponibili due offerte per gli unit test in Visual Studio 2017: Esplora test e _Live Unit Testing_. Nella versione 15.6 la velocità di individuazione dei test in Esplora test è migliorata notevolmente. Anche l'interfaccia utente è stata riprogettata per consentire l'ordinamento gerarchico.

Visual Studio è dotato anche di una funzionalità di unit test denominata [Live Unit Testing](/test/live-unit-testing). Live Unit Testing viene eseguita in modo continuo in background, esegue test interessati dalla modifica del codice e aggiorna le icone dell'Editor inline per comunicare lo stato dei test.

![Visualizzazione gerarchica per Esplora test in Visual Studio](../ide/media/VS2017Guide-hiearchy-test-explorer.png "VS2017Guide-hiearchy-test-explorer")

### <a name="what-other-features-do-i-need-to-know-about"></a>Quali altre funzionalità occorre conoscere
Ecco un elenco di funzionalità editor e di produttività per rendere più efficiente la scrittura del codice. È possibile che alcune funzionalità debbano essere abilitate perché disabilitate per impostazione predefinita in quanto potrebbero indicizzare elementi del computer, essere controverse o essere ancora in forma sperimentale.
- *Individuare i file in Esplora soluzioni* evidenzia il file attivo in Esplora soluzioni.
  - **Strumenti > Opzioni > Progetti e soluzioni > Tieni traccia degli elementi attivi in Esplora soluzioni**
- *Aggiungere direttive using per i tipi in assembly di riferimento e in pacchetti NuGet* mostra una lampadina con una correzione del codice per installare un pacchetto NuGet per un tipo senza riferimento.
  - **Strumenti > Opzioni > Editor di testo > C# > Avanzate > Suggerisci le direttive using per i tipi in assembly di riferimento** e **Suggerisci le direttive using per i tipi in pacchetti NuGet**
- *Abilita analisi della soluzione completa* per visualizzare tutti gli errori della soluzione nell'elenco errori.
  - **Strumenti > Opzioni > Editor di testo > c# > Avanzate > Abilita analisi della soluzione completa**
- *Abilita spostamento a origini decompilate* per abilitare Vai a definizione in tipi o membri da origini esterne e utilizzare il decompilatore ILSpy per mostrare i corpi dei metodi.
  - **Strumenti > Opzioni > Editor di testo > C# > Avanzate > Abilita spostamento a origini decompilate**
- La *Modalità di completamento/suggerimento* in IntelliSense cambia il comportamento del completamento. Gli sviluppatori con esperienza IntelliJ tendono a cambiare l'impostazione predefinita in questo punto.
  - **Menu > Modifica > IntelliSense -> Attiva/disattiva modalità di terminazione**
- Sono disponibili *frammenti di codice* per generare i boilerplate comuni (premere 'Tab' due volte). Visualizzare l'[elenco completo](/ide/visual-csharp-code-snippets).

![Frammenti di codice in Visual Studio](../ide/media/VS2017Guide-code-snippet.png "VS2017Guide-code-snippet")

### <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Manca una funzionalità che migliora la produttività o le prestazioni sono scadenti?
Esistono diversi modi per inviare commenti e suggerimenti:
- Registrare richieste di funzionalità .NET nell'[archivio GitHub](https://github.com/dotnet/roslyn/issues).
- Registrare richieste di funzionalità, bug e problemi di prestazioni di Visual Studio tramite l'icona **Commenti e suggerimenti** nella parte superiore della finestra di Visual Studio.


## <a name="a-idoverview-overview-of-visual-studio-2017-for-net-developers"></a><a id="overview"/> Panoramica di Visual Studio 2017 per sviluppatori .NET

### <a name="smart-code-editor"></a>Editor di codice intelligente

- [Documentazione: Uso di IntelliSense](using-intellisense.md)
- [Documentazione: Funzionalità dell'editor intelligente](writing-code-in-the-code-and-text-editor.md)

Visual Studio è in grado di comprendere in modo approfondito il codice grazie al compilatore .NET ("Roslyn") e offre funzionalità di modifica intelligenti quali la colorazione della sintassi, il completamento del codice, il controllo ortografico delle variabili, la risoluzione dei tipi non importati, la creazione della struttura, i visualizzatori di struttura, [CodeLens](find-code-changes-and-other-history-with-codelens.md), la gerarchia delle chiamate, la visualizzazione di informazioni rapide al passaggio del mouse, la Guida sui parametri, oltre a strumenti per il refactoring, l'applicazione di azioni rapide e la generazione di codice.

![Editor di codice intelligente di Visual Studio](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

### <a name="navigate-and-search-your-codebase"></a>Esplorare la codebase ed eseguire ricerche al suo interno

[Documentazione: Spostamento nel codice](navigating-code.md)

È possibile spostarsi rapidamente all'interno del codice .NET passando a qualsiasi dichiarazione di file, tipo, membro o simbolo con il collegamento *Vai a tutti* (**Ctrl + T**). È anche possibile trovare tutti i riferimenti di un simbolo o di un valore letterale nel codice, inclusi i riferimenti tra linguaggi .NET diversi (**Maiusc + F12**), nonché usare i comandi di esplorazione mirati per passare direttamente alle definizioni di simboli (**F12**) o alle implementazioni di questi (**Ctrl + F12**).

![Vai a tutti e Trova tutti i riferimenti](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

### <a name="live-code-analysis-for-code-quality"></a>Analisi codice in tempo reale per la qualità del codice

[Documentazione: Refactoring e azioni rapide](refactoring-code-generation-quick-actions.md)

Visual Studio mette a disposizione funzionalità di diagnostica del codice in tempo reale per migliorare la qualità del codice grazie al rilevamento di errori e di codice potenzialmente problematico. Sono anche disponibili azioni rapide (**CTRL**+**.**) per risolvere i problemi rilevati all'interno del documento, del progetto o della soluzione. Abilitare l'*analisi della soluzione completa* per individuare eventuali problemi all'interno dell'intera soluzione, anche se i relativi file non sono aperti nell'editor.

Con i tasti di scelta rapida **CTRL**+**.** è anche possibile usare i suggerimenti di codice per apprendere le procedure consigliate, effettuare lo stub, la generazione o il refactoring del codice e adottare nuove funzionalità del linguaggio .

![Applicare correzioni rapide e refactoring tramite il menu Lampadina](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

### <a name="unit-testing"></a>Testing unità

[Documentazione: Testing unità in Visual Studio](../test/improve-code-quality.md)

È possibile eseguire l'unit test, compreso il debug, con i framework di testing MSTest, NUnit o XUnit per qualsiasi applicazione destinata a .NET Framework, .NET Standard o .NET Core. È anche possibile esaminare e rivedere i test in *Esplora test* e rendersi conto immediatamente dell'impatto delle modifiche al codice sull'unit test all'interno dell'editor con *Live Unit Testing* (solo SKU Enterprise).

![Live Unit Testing in Visual Studio](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

### <a name="code-consistency-and-style"></a>Coerenza e stile del codice

- [Documentazione: Impostazioni personalizzate e portabili per l'editor](create-portable-custom-editor-options.md)
- [Documentazione: Impostazioni di EditorConfig relative allo stile del codice per .NET](editorconfig-code-style-settings-reference.md)

Visual Studio consente la configurazione di convenzioni di scrittura del codice, rilevando le violazioni di stile, e presenta correzioni rapide per risolvere i problemi di stile con i tasti di scelta rapida **CTRL**+**.** . Per configurare e imporre le convenzioni di formattazione, denominazione e stile del codice in un repository, consentendo eccezioni a livello di progetto e di file, è possibile usare *EditorConfig*.

![Configurare e imporre convenzioni di scrittura del codice con EditorConfig](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

### <a name="debugging"></a>Debug

[Documentazione: Debug in Visual Studio](../debugger/index.md)

Visual Studio include un debugger all'avanguardia che consente di eseguire il debug delle applicazioni .NET destinate a .NET Framework, .NET Standard e .NET Core. Il debugger consente di attivare, disattivare e impostare punti di interruzione condizionali (**F9**), eseguire istruzioni di chiamate di metodi, valutare espressioni LINQ e lambda, impostare espressioni di controllo per le variabili, ricollegarsi ai processi, esaminare lo stack di chiamate e persino di apportare modifiche in tempo reale al codice durante il debug con *Modifica e continuazione*.

Se il servizio è in esecuzione in Azure, con Visual Studio 2017 Enterprise è possibile usare *Debug snapshot* per diagnosticare eventuali problemi nelle applicazioni cloud distribuite live.

![Debug in Visual Studio](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

### <a name="version-control"></a>Controllo della versione

[Documentazione: Controllo della versione in Visual Studio](/vsts/index)

Usare Git o il controllo della versione di Team Foundation per archiviare e aggiornare il codice in Visual Studio. All'interno dell'editor, è possibile organizzare le modifiche locali con Team Explorer e usare la barra di stato per tenere traccia di commit e modifiche in sospeso. È anche possibile configurare l'integrazione e il recapito continui all'interno di Visual Studio con l'estensione [Strumenti di recapito continuo per Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) per adottare il flusso di lavoro di sviluppo agile.

![Controllo del codice sorgente in Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

### <a name="extensibility"></a>Estendibilità

[Documentazione: Estensione di Visual Studio](../extensibility/index.md)

Visual Studio offre un ampio ecosistema di estensioni che è possibile installare o creare quando necessario. Installare le estensioni dalla *raccolta estensioni* o da *Visual Studio Marketplace*, compilare un plug-in personalizzato dell'editor con *VS SDK* o creare un analizzatore di codice o un refactoring in tempo reale personalizzato tramite *.NET Compiler Platform SDK*. È possibile trovare suggerimenti e correzioni di codice aggiuntivi scaricando l'estensione [Analisi codice Microsoft](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

![Raccolta estensioni di Visual Studio](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")
