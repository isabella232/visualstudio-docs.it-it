---
title: 'Documenti di Visual Studio: cronologia delle novità '
titleSuffix: ''
description: Cronologia delle novità nella documentazione di Visual Studio
ms.date: 03/08/2021
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: bbad51f6d06c221118ffda01e1c7e93374eea2ff
ms.sourcegitcommit: 3a855d3513407ea78336386dc3be0b75142614b0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2021
ms.locfileid: "103622569"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Cronologia delle novità nella documentazione di Visual Studio

Benvenuti alla cronologia delle novità di Visual Studio docs. Questo articolo contiene le principali modifiche apportate ai documenti prima del 2021 febbraio (a partire dal luglio 2020). Per le ultime novità, vedere la [documentazione di Visual Studio:](whats-new-visual-studio-docs.md)novità della documentazione.

## <a name="january-2021"></a>Gennaio 2021
### <a name="azure"></a>Azure

**Nuovi articoli**

- [Creazione e distribuzione nei servizi cloud (supporto esteso) in Visual Studio (anteprima)](../azure/cloud-services-extended-support.md) -supporto esteso di servizi cloud-nessun modello

### <a name="code-quality"></a>Qualità del codice

**Nuovi articoli**

- [Metriche del codice-associazione di classi](../code-quality/code-metrics-class-coupling.md) -aggiornamento della metrica del codice
- [Metriche del codice-intervallo di indici di gestibilità e](../code-quality/code-metrics-maintainability-index-range-and-meaning.md) aggiornamento della metrica del codice

### <a name="debugger"></a>Debugger

**Nuovi articoli**

- [Eseguire il debug di app .NET Core in WSL 2 con Visual Studio](../debugger/debug-dotnet-core-in-wsl-2.md) -debug WSL2 di .NET Core

**Articoli aggiornati**

- [Creare visualizzazioni personalizzate di oggetti C++ nel debugger usando natvis Framework](../debugger/create-custom-views-of-native-objects.md) -chiarimento per la formattazione XML di caratteri speciali in natvis
- [Avviso di sicurezza: la connessione a un processo di proprietà di un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non sono sicure, non connettersi a questo processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md) : aggiornamenti all'avviso di sicurezza quando ci si connette a un processo non attendibile

### <a name="deployment"></a>Distribuzione

**Articoli aggiornati**

- [ &lt; &gt; Elemento InstallChecks (programma di avvio automatico)](../deployment/installchecks-element-bootstrapper.md) -aggiornare la documentazione del pacchetto del programma di avvio automatico per includere il nuovo elemento BeforeInstallChecks

### <a name="extensibility"></a>Estendibilità

**Articoli aggiornati**

- [Procedura dettagliata: pubblicare un'estensione di Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md) -[PUBLIC_MOVE] commit da PR pubblico 6214

### <a name="get-started"></a>Introduzione

**Nuovi articoli**

- [Esercitazione: aprire un progetto da un repository in Visual Studio 2017](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md) -esercitazione aprire un progetto da un repository

**Articoli aggiornati**

- [Esercitazione: aprire un progetto da un repository](../get-started/tutorial-open-project-from-repo.md) -esercitazione aprire un progetto da un repository

### <a name="ide"></a>IDE

**Nuovi articoli**

- [Guida sensibile al contesto di JavaScript per Visual Studio](./not-in-toc/default-f1-javascript.md) -aggiunta di pagine F1 predefinite js e TS
- [Guida sensibile al contesto di typescript per Visual Studio](./not-in-toc/default-f1-typescript.md) -aggiunta di pagine F1 predefinite js e TS

**Articoli aggiornati**

- [Soluzioni e progetti in Visual Studio](./solutions-and-projects-in-visual-studio.md) : aggiungere un collegamento alla libreria di immagini di Visual Studio

### <a name="install"></a>Installazione

**Articoli aggiornati**

- [Numeri di build e date di rilascio di Visual Studio](../install/visual-studio-build-numbers-and-release-dates.md) -aggiornamenti Patch Tuesday

### <a name="msbuild"></a>MSBuild

**Articoli aggiornati**

- [Glossario di MSBuild](../msbuild/msbuild-glossary.md) -innalzamento di livello delle chiavi del glossario a H2

### <a name="profiling"></a>Profilatura

**Nuovi articoli**

- [Visualizzare i contatori DotNet dal profiler di Visual Studio](../profiling/dotnet-counters-tool.md) -aggiunta del documento dello strumento contatori .NET

### <a name="test"></a>Test

**Articoli aggiornati**

- [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md) -aggiungere un file di test audio cue doc

## <a name="december-2020"></a>Dicembre 2020
### <a name="azure"></a>Azure

**Nuovi articoli**

- [Aggiunta di app Azure configurazione con Visual Studio servizi connessi](../azure/vs-azure-tools-connected-services-app-configuration.md) -App config servizi connessi esercitazione

### <a name="code-quality"></a>Qualità del codice

**Articoli aggiornati**

- [Panoramica](../code-quality/use-roslyn-analyzers.md) -compilazione dalla riga di comando con EditorConfig
- [Abilitare o installare gli analizzatori .NET di terze parti](../code-quality/install-net-analyzers.md)
  - Aggiungere maggiore chiarezza ai documenti di migrazione per FxCopAnalyzers in NetAnalyzers
  - Ridisporre il sommario per gli analizzatori .NET
- [Eseguire la migrazione da analizzatori FxCop ad analizzatori .NET](../code-quality/migrate-from-fxcop-analyzers-to-net-analyzers.md) -aggiungere maggiore chiarezza alla documentazione per la migrazione di FxCopAnalyzers in NetAnalyzers

### <a name="containers"></a>Contenitori

**Articoli aggiornati**

- [Risolvere i problemi relativi allo sviluppo di Visual Studio con Docker](../containers/troubleshooting-docker-errors.md) -aggiornamento di Docker per Visual Studio Guida alla risoluzione dei problemi

### <a name="debugger"></a>Debugger

**Articoli aggiornati**

- [Domande frequenti: trovare la funzionalità di debug necessaria in Visual Studio](../debugger/find-your-debugging-task.md) -attività di individuazione per trovare l'attività di debug e gli argomenti introduttivi

### <a name="get-started"></a>Introduzione

**Articoli aggiornati**

- [Esercitazione: creare una semplice app console c# in Visual Studio](../get-started/csharp/tutorial-console.md) -esercitazione sulla console c#: la parte 2 si applica solo a vs 2019

### <a name="ide"></a>IDE

**Articoli aggiornati**

- [Soluzioni e progetti in Visual Studio](./solutions-and-projects-in-visual-studio.md) -argomenti relativi agli aggiornamenti per progetti & soluzioni
- [Creare un nuovo progetto in Visual Studio](./create-new-project.md)
  - perfezionare il testo ALT per screenshot e diagrammi
  - altri aggiornamenti per le soluzioni & argomenti relativi ai progetti
- [Risorse per la risoluzione dei problemi relativi agli errori IDE](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md) -rivedere la sezione delle risorse del forum obsolete
- [Usare soluzioni e progetti](./creating-solutions-and-projects.md) -altri aggiornamenti alle soluzioni & argomenti sui progetti
- [Come segnalare un problema con Visual Studio o il programma di installazione di Visual Studio](./how-to-report-a-problem-with-visual-studio.md)
  - Schermata aggiornata
  - Modifiche della community degli sviluppatori
- [Suggerimenti per le prestazioni di Visual Studio](./visual-studio-performance-tips-and-tricks.md) : aggiornare la sezione Disable strumenti di diagnostica
- [Introduzione a progetti e soluzioni](../get-started/tutorial-projects-solutions.md)
  - argomenti relativi agli aggiornamenti a soluzioni & progetti
  - Aggiornare tutorial-projects-solutions.md
  - opzione di menu from mancante

### <a name="test"></a>Test

**Articoli aggiornati**

- [Introduzione a unit test](../test/getting-started-with-unit-testing.md) -lavoro di individuazione e altri miglioramenti per gli strumenti di test
- [Esaminare prima di tutto gli strumenti di test in Visual Studio](../test/improve-code-quality.md) : lavoro di individuazione e altri miglioramenti per gli strumenti di test
- [Strumenti di test in Visual Studio # obbligatorio; titolo della pagina visualizzato nei risultati della ricerca. Includere il marchio. < 60 caratteri.](../test/index.yml) -Lavoro di individuazione e altri miglioramenti per gli strumenti di test
- [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md) -aggiungere il codice XML della playlist dinamica per i Framework diff

## <a name="november-2020"></a>Novembre 2020
### <a name="code-quality"></a>Qualità del codice

**Nuovi articoli**

- [Abilitare o installare gli analizzatori .NET](../code-quality/install-net-analyzers.md) -aggiungere la documentazione per eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET
- [Eseguire la migrazione da analizzatori FxCop ad analizzatori .NET](../code-quality/migrate-from-fxcop-analyzers-to-net-analyzers.md) : aggiungere la documentazione per eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET
- [Eseguire la migrazione da analisi legacy (FxCop) a analisi origine (analizzatori .NET)](../code-quality/migrate-from-legacy-analysis-to-net-analyzers.md) : aggiungere la documentazione per eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET
- [Domande frequenti sugli analizzatori FxCop e .NET legacy](../code-quality/net-analyzers-faq.md) : aggiungere la documentazione per eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET

**Articoli aggiornati**

- [Domande frequenti sull'analisi del codice](../code-quality/analyzers-faq.md) : aggiunta della documentazione per la migrazione dagli analizzatori FxCop agli analizzatori .NET
- [Stato della porta della regola FxCop](../code-quality/fxcop-rule-port-status.md) -aggiunta della documentazione per la migrazione dagli analizzatori FxCop agli analizzatori .NET
- [Regole deprecate](../code-quality/fxcop-unported-deprecated-rules.md) : è stata aggiunta la documentazione per la migrazione dagli analizzatori FxCop agli analizzatori .NET
- [Regole non portate che possono essere trasferite. la](../code-quality/fxcop-unported-rules-may-get-ported.md) documentazione è stata aggiunta per eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET
- [Regole non portate](../code-quality/fxcop-unported-rules.md) : è stata aggiunta la documentazione per la migrazione dagli analizzatori FxCop agli analizzatori .NET
- [Installare gli analizzatori di terze parti](../code-quality/install-roslyn-analyzers.md) : è stata aggiunta la documentazione per eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET
- [Panoramica](../code-quality/use-roslyn-analyzers.md) : è stata aggiunta la documentazione per la migrazione dagli analizzatori FxCop agli analizzatori .NET

### <a name="containers"></a>Contenitori

**Articoli aggiornati**

- Funzionamento del [Bridge per Kubernetes](../containers/overview-bridge-to-kubernetes.md) -sezione autorizzazioni di Kubernetes

### <a name="debugger"></a>Debugger

**Nuovi articoli**

- [Connettersi a un processo in esecuzione in un contenitore Docker](../debugger/attach-to-process-running-in-docker-container.md) -refactoring Connetti a elaborare documenti per scenari Linux

**Articoli aggiornati**

- [Connettersi ai processi in esecuzione con il debugger di Visual Studio](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) : refactoring Connetti a elaborare documenti per scenari Linux
- [Eseguire il debug di .NET Core in Linux tramite SSH mediante la connessione a un processo](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md) -refactoring Connetti a elaborare documenti per scenari Linux

### <a name="deployment"></a>Distribuzione

**Nuovi articoli**

- [Distribuire un'applicazione desktop di Windows .NET tramite ClickOnce](../deployment/quickstart-deploy-using-clickonce-folder.md) -aggiungere l'avvio rapido di ClickOnce per i progetti Windows .NET

**Articoli aggiornati**

- [Presentazione della distribuzione in Visual Studio](../deployment/deploying-applications-services-and-components.md)
  - Modifica passaggio
  - Individuabilità e aggiornamenti dei collegamenti per .NET 5
- [Distribuzione in Visual Studio # richiesta; titolo della pagina visualizzato nei risultati della ricerca. Includere il marchio. < 60 caratteri.](../deployment/index.yml) -Individuabilità e aggiornamenti dei collegamenti per .NET 5
- [Compilare applicazioni ClickOnce dalla riga di comando](../deployment/building-clickonce-applications-from-the-command-line.md) -aggiungere l'avvio rapido di ClickOnce per i progetti Windows .NET
- [Distribuire l'app in una cartella, IIS, Azure o un'altra destinazione](../deployment/deploying-applications-services-and-components-resources.md) -aggiungere l'avvio rapido di ClickOnce per i progetti Windows .NET
- [Distribuire un'app in una cartella con Visual Studio](../deployment/quickstart-deploy-to-local-folder.md) -aggiungere l'avvio rapido di ClickOnce per i progetti Windows .NET

### <a name="designers"></a>Finestre di progettazione

**Articoli aggiornati**

- [Esercitazione: Introduzione a Progettazione Windows Form](../designers/walkthrough-windows-forms-designer.md) -typo con correzione

### <a name="get-started"></a>Introduzione

**Articoli aggiornati**

- Informazioni [su progetti e soluzioni](../get-started/tutorial-projects-solutions.md) -aggiornamento del testo alternativo & metadati, oltre a una nota sul modello di soluzione vuota
- [Esercitazione: aprire un progetto da una](../get-started/tutorial-open-project-from-repo.md) Nota aggiuntiva del repository e vedere anche il collegamento per la nuova esperienza git

### <a name="ide"></a>IDE

**Nuovi articoli**

- [Usare gli account di GitHub in Visual Studio](./work-with-github-accounts.md) : aggiunta della pagina relativa all'uso di GitHub e informazioni sull'accesso a GitHub ad altre pagine
- [Estrae](./reference/extract-base-class.md) le funzionalità di produttività DotNet aggiunte alla classe di base
- Funzionalità di produttività DotNet aggiunte al [metodo inline](./reference/inline-method.md)
- [Rendere](./reference/make-class-abstract.md) le funzionalità di produttività DotNet aggiunte dalla classe
- [Usa `new()` ](./reference/use-new.md) -Aggiunta delle funzionalità di produttività DotNet
- [Usare i criteri](./reference/use-pattern-matching.md) di ricerca-aggiunta di funzionalità di produttività DotNet

**Articoli aggiornati**

- [Esperienza git in Visual Studio](./git-with-visual-studio.md)
  - Aggiornamento dei metadati del testo alternativo &
  - Aggiornamenti al nuovo contenuto dell'esperienza git per 16,8 GA
- [Novità di Visual Studio 2019](./whats-new-visual-studio-2019.md)
  - Aggiornamento dei metadati del testo alternativo &
  - Aggiornamento della pagina Novità di Visual Studio 2019 per 16,8 GA
- [Connettersi ai progetti in Team Explorer](./connect-team-project.md) -aggiornamento della pagina Team Explorer con la nuova nota sull'esperienza git & collegamento
- [Usare più account utente](./work-with-multiple-user-accounts.md) : sono state aggiunte informazioni sull'accesso a GitHub ad altre pagine
- [Convenzioni di formattazione EditorConfig in C++](./cpp-editorconfig-properties.md)
  - Il prefisso è cpp_, non _cpp_ _ per le impostazioni C++. EditorConfig
  - Rimosso carattere errato in C++. esempio EditorConfig
- [Converti `typeof` in `nameof` funzionalità di](./reference/convert-typeof-to-nameof.md) produttività DotNet aggiunte

### <a name="install"></a>Installazione

**Articoli aggiornati**

- [Numeri di build e date di rilascio di Visual Studio](../install/visual-studio-build-numbers-and-release-dates.md)
  - Aggiunta dei dati di 16.8.2
  - Aggiunta di 16.8.1
  - Numeri di Build aggiornati per 16,8 GA e altro ancora
- [Immagini di Visual Studio in Azure](../install/using-visual-studio-vm.md) : data di pubblicazione modificata e versioni di revisione secondaria aggiornate
- [ID dei carichi di lavoro e dei componenti di Visual Studio](../install/workload-and-component-ids.md) -documenti aggiornati per i componenti per 16,8
- Documentazione relativa alla directory dei componenti di [Visual Studio Build Tools](../install/workload-component-id-vs-build-tools.md) aggiornata per 16,8
- [Directory dei componenti di Visual Studio Community](../install/workload-component-id-vs-community.md) -documentazione del componente aggiornata per 16,8
- Documentazione relativa alla directory dei componenti di [Visual Studio Enterprise](../install/workload-component-id-vs-enterprise.md) aggiornata per 16,8
- Documentazione di [Visual Studio Team Explorer Component](../install/workload-component-id-vs-team-explorer.md) -componente aggiornato per 16,8
- [Directory dei componenti dell'agente di test di Visual Studio](../install/workload-component-id-vs-test-agent.md) : documentazione del componente aggiornata per 16,8
- Documentazione di [Visual Studio test controller Component](../install/workload-component-id-vs-test-controller.md) -componente aggiornato per 16,8
- [Installare e usare Visual Studio e i servizi di Azure protetti da un firewall o un server proxy](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md) -aggiunto un dominio mancante

### <a name="msbuild"></a>MSBuild

**Nuovi articoli**

- [Change Waves](../msbuild/change-waves.md) -MSBuild: Change Waves New Topic

**Articoli aggiornati**

- [Funzioni di proprietà](../msbuild/property-functions.md) -versione 16,8
- [Elementi di progetto MSBuild comuni](../msbuild/common-msbuild-project-items.md) : Ripristina il contenuto per l'elemento InternalsVisibleTo

### <a name="profiling"></a>Profilatura

**Articoli aggiornati**

- [Misurare le prestazioni dell'applicazione dalla riga di comando](../profiling/profile-apps-from-command-line.md) aggiornamento della profilatura dalla riga di comando docs

### <a name="test"></a>Test

**Articoli aggiornati**

- [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md) -aggiunta di una breve sezione sul formato XML della playlist
- [Isolare il codice sottoposto a test con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) -documentazione aggiornata con il supporto per .NET Core
- [Usare gli shim per isolare l'app per unit test](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) : documentazione aggiornata con il supporto di .NET Core

### <a name="xaml-tools"></a>Strumenti XAML

**Articoli aggiornati**

- [Usare i dati della fase di progettazione con il finestra di progettazione XAML in Visual Studio](../xaml-tools/xaml-designtime-data.md)
  - Aggiornamento della sezione requisiti per 16,8 GA
  - La sezione requisiti è stata modificata
  - Aggiornamento 16,8 commento anteprima + collegamento a GA

## <a name="october-2020"></a>Ottobre 2020
### <a name="code-quality"></a>Qualità del codice

**Articoli aggiornati**
- [Analizzatori del codice](../code-quality/index.yml) -refactoring della CA per .NET 5

### <a name="containers"></a>Contenitori

**Articoli aggiornati**

- [Guida introduttiva: usare Docker con un'app a singola pagina React in Visual Studio](../containers/container-tools-react.md)
  - Strumenti contenitore: rimuovere i riferimenti a un repository di immagini obsolete
  - Esercitazione sull'aggiornamento dei contenitori React per .NET 3,1 e Visual Studio 16,7
- [Funzionamento del Bridge per Kubernetes](../containers/overview-bridge-to-kubernetes.md) -Bridge per Kubernetes: aggiungere limitazioni
- [Eseguire il debug di app in un contenitore Docker locale](../containers/edit-and-refresh.md) -casella degli strumenti Docker

### <a name="debugger"></a>Debugger

**Nuovi articoli**

- [Supporto di DirectX 12 in Visual Studio](../debugger/graphics/visual-studio-graphics-diagnostics-directx-12.md) -Vsdg DX12

**Articoli aggiornati**

- [Eseguire il debug di app ASP.NET o ASP.NET Core in Visual Studio](../debugger/how-to-enable-debugging-for-aspnet-applications.md) -correzioni del contenuto del debugger per i problemi di GitHub
- [Usare i punti di interruzione nel debugger di Visual Studio](../debugger/using-breakpoints.md) -correzioni del contenuto del debugger per i problemi di GitHub
- [Eseguire il debug dei servizi di Azure in Visual Studio](../debugger/debug-azure-apps.md) -SEO e collegamento degli aggiornamenti per snapshot debugger
- [Eseguire il debug di app ASP.NET di Azure in tempo reale usando gli aggiornamenti snapshot debugger](../debugger/debug-live-azure-applications.md) -SEO e link per snapshot debugger
- [Debug remoto](../debugger/remote-debugging.md) -SEO e collegamento degli aggiornamenti per snapshot debugger
- [Panoramica di Visual Studio diagnostica della grafica](../debugger/graphics/overview-of-visual-studio-graphics-diagnostics.md) -Vsdg DX12
- [Visual Studio diagnostica della grafica](../debugger/graphics/visual-studio-graphics-diagnostics.md) -Vsdg DX12

### <a name="get-started"></a>Introduzione

**Articoli aggiornati**

- [Esercitazione: estendere una semplice app console c#:](../get-started/csharp/tutorial-console-part-2.md) aggiunte di debug per l'esercitazione estesa su c#

### <a name="ide"></a>IDE

**Nuovi articoli**

- [Usare il documento ricerca di Visual Studio](./visual-studio-search.md) -vs

### <a name="install"></a>Installazione

**Articoli aggiornati**

- [Numeri di build e date di rilascio di Visual Studio](../install/visual-studio-build-numbers-and-release-dates.md)
  - aggiungere i dati 16.7.7 e 16,8 Preview 6
  - aggiungere le informazioni di 16,8 Preview 5

### <a name="msbuild"></a>MSBuild

**Articoli aggiornati**

- [Procedura dettagliata: usare MSBuild](../msbuild/walkthrough-using-msbuild.md) -procedura dettagliata di MSBuild: aggiungere passaggi di installazione autonomi

### <a name="profiling"></a>Profilatura

**Articoli aggiornati**

- [Analizzare l'utilizzo della memoria](../profiling/analyze-memory-usage.md)
  - Aggiornamenti dell'utilizzo della memoria per la profilatura: collegamenti e chiarimenti
  - Aggiornamenti dello strumento utilizzo memoria
- [Analizzare l'utilizzo della memoria senza debug nel profiler delle prestazioni](../profiling/memory-usage-without-debugging2.md)
  - Aggiornamenti dell'utilizzo della memoria per la profilatura: collegamenti e chiarimenti
  - Aggiornamenti dello strumento utilizzo memoria
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)
  - Aggiornamenti dell'utilizzo della memoria per la profilatura: collegamenti e chiarimenti
  - Aggiornamenti dello strumento utilizzo memoria
- [Eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
  - Aggiornamenti dell'utilizzo della memoria per la profilatura: collegamenti e chiarimenti
  - Aggiornamenti dello strumento utilizzo memoria
- [Analizzare l'utilizzo della CPU senza debug nel profiler delle prestazioni](../profiling/cpu-usage.md) -aggiornamenti dello strumento utilizzo memoria

### <a name="windows"></a>Windows

**Articoli aggiornati**

- [Documentazione di Visual Studio | Microsoft Docs](../windows/index.yml) -aggiornamenti dell'hub Windows

### <a name="xaml-tools"></a>Strumenti XAML

**Nuovi articoli**

- [Usare i dati della fase di progettazione con il finestra di progettazione XAML in Visual Studio](../xaml-tools/xaml-designtime-data.md)
  - Aggiunta della sezione Extensibility alla documentazione della fase di progettazione XAML
  - Nuovo articolo XAML della fase di progettazione

## <a name="september-2020"></a>Settembre 2020
### <a name="code-quality"></a>Qualità del codice

**Nuovi articoli**

- [CA1416: convalida compatibilità piattaforma](/dotnet/fundamentals/code-analysis/quality-rules/ca1416) -documentazione CA1416 Convalida piattaforma compatibilità
- [Ca1834: usare StringBuilder. Append (Char) per le stringhe a carattere singolo](/dotnet/fundamentals/code-analysis/quality-rules/ca1834) -docs per ca1834

**Aggiornato**

- [Panoramica dell'analisi del codice sorgente](../code-quality/roslyn-analyzers-overview.md) -aggiornamenti dell'analisi del codice per il refactoring .NET
- [Configurare l'analisi della qualità del codice](../code-quality/use-roslyn-analyzers.md) -aggiornamenti dell'analisi del codice per il refactoring .NET

### <a name="containers"></a>Contenitori

**Nuovi articoli**

- [Usare Bridge to Kubernetes](../containers/bridge-to-kubernetes.md) -processo locale con la nuova personalizzazione di Kubernetes per il Bridge a Kubernetes
- [Funzionamento del Bridge per Kubernetes](../containers/overview-bridge-to-kubernetes.md) -processo locale con Kubernetes per la ripersonalizzazione di Bridge per Kubernetes

### <a name="deployment"></a>Distribuzione

**Articoli aggiornati**

- [Distribuire l'app in una cartella, IIS, Azure o in un'altra destinazione](../deployment/deploying-applications-services-and-components-resources.md) -aggiornamenti della distribuzione
- [Distribuire un'app in una cartella con Visual Studio](../deployment/quickstart-deploy-to-local-folder.md) -aggiornamenti della distribuzione

### <a name="ide"></a>IDE

**Nuovi articoli**

- [Nuova esperienza git in Visual Studio (anteprima)](./git-with-visual-studio.md) -aggiungere nuovo contenuto dell'esperienza git (anteprima)
- [Convenzioni di formattazione C++ EditorConfig](./cpp-editorconfig-properties.md) -nuovo articolo
- [Che cosa sono gli spazi di dati di GitHub? (Anteprima)](./codespaces/codespaces-overview.md) -Aggiungi contenuto codespaces (anteprima)
- [Come personalizzare un codespace (anteprima)](./codespaces/customize-codespaces.md) -aggiungere il contenuto di codespaces (anteprima)
- [Funzionalità supportate di Visual Studio (anteprima)](./codespaces/supported-features-codespaces.md) -aggiungere contenuti di codespaces (anteprima)
- [Come usare Visual Studio con uno spazio dei nomi (anteprima)](./codespaces/use-visual-studio-with-codespaces.md) -aggiungere contenuti di codespaces (anteprima)

**Articoli aggiornati**

- [Impostazioni della convenzione di codifica .NET per EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options) -aggiornamento di EditorConfig
- [Convenzioni del linguaggio](/dotnet/fundamentals/code-analysis/style-rules/language-rules) -esempi mancanti

### <a name="install"></a>Installazione

**Nuovi articoli**

- [Visual Studio nei dispositivi](../install/visual-studio-on-arm-devices.md) basati su ARM-aggiunta di documenti per vs su ARM

**Articoli aggiornati**

- [Risolvere gli errori correlati alla rete quando si installa o si usa Visual Studio](../install/troubleshooting-network-related-errors-in-visual-studio.md) -Aggiungi soluzione alternativa per l'arresto anomalo del proxy di autenticazione feedback

### <a name="profiling"></a>Profilatura

**Articoli aggiornati**

- [Misurare l'utilizzo della memoria in Visual Studio](../profiling/memory-usage.md) : Panoramica degli aggiornamenti per la funzionalità di profilatura
- [PerfTips](../profiling/perftips.md) -aggiornamenti al tour delle funzionalità di profilatura
- [Esaminare prima di tutto gli strumenti di profilatura](../profiling/profiling-feature-tour.md) -aggiornamenti alla panoramica delle funzionalità di profilatura
- [Eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
  - Panoramica degli aggiornamenti per la funzionalità di profilatura
  - Miglioramenti delle prestazioni del contenuto

## <a name="august-2020"></a>Agosto 2020
### <a name="azure"></a>Azure

**Nuovi articoli**

- [Aggiungere applicazione Azure Insights usando i servizi connessi di Visual Studio servizi connessi](../azure/azure-app-insights-add-connected-service.md) per VS 2019 16,7
- [Aggiungere la cache di Azure per Redis usando](../azure/azure-cache-for-redis-add-connected-service.md) i servizi connessi a Visual Studio servizi connessi per VS 2019 16,7
- [Aggiungere Azure Cosmos DB all'app usando i servizi connessi di Visual Studio servizi connessi](../azure/azure-cosmosdb-add-connected-service.md) per VS 2019 16,7
- [Aggiungere Azure SignalR usando i servizi connessi di Visual Studio servizi connessi](../azure/azure-signalr-add-connected-service.md) per VS 2019 16,7
- [Aggiungere una connessione ai servizi connessi al database SQL di Azure](../azure/azure-sql-database-add-connected-service.md) per VS 2019 16,7

**Articoli aggiornati**

- [Aggiunta dell’archiviazione di Azure tramite Servizi connessi di Visual Studio](../azure/vs-azure-tools-connected-services-storage.md)
  - Servizi connessi per VS 2019 16,7
  - Articolo relativo ai servizi connessi di archiviazione di Azure: aggiornare i tipi di interfaccia utente e progetto supportati

### <a name="code-quality"></a>Qualità del codice

**Nuovi articoli**

- [Ca1310: specificare StringComparison per la correttezza](/dotnet/fundamentals/code-analysis/quality-rules/ca1310) -aggiungere la documentazione per ca1310 e aggiornare la documentazione per CA1307
- [Ca1837: usare Environment. ProcessId anziché Process. GetCurrentProcess (). ID](/dotnet/fundamentals/code-analysis/quality-rules/ca1837) -docs per ca1837
- [Ca1838: evitare `StringBuilder` i parametri per P/Invoke](/dotnet/fundamentals/code-analysis/quality-rules/ca1838) -aggiungere la documentazione per ca1838
- [Ca2008: non creare attività senza passare un TaskScheduler](/dotnet/fundamentals/code-analysis/quality-rules/ca2008) -aggiungere la documentazione per ca2008
- [CA2249: provare a usare String. Contains anziché String. IndexOf](/dotnet/fundamentals/code-analysis/quality-rules/ca2249) -docs per CA2249
- [CA2361: assicurarsi che la classe generata automaticamente contenente DataSet. ReadXml () non venga usata con dati non attendibili](/dotnet/fundamentals/code-analysis/quality-rules/ca2361) -altre regole DataSet/DataTable
- [CA2362: il set di dati o la DataTable unsafe nel tipo serializzabile generato automaticamente può essere vulnerabile agli attacchi di esecuzione di codice in modalità remota](/dotnet/fundamentals/code-analysis/quality-rules/ca2362) . altre regole DataSet/DataTable
- [IL3000: evitare di usare l'accesso al percorso del file di assembly quando si pubblica come](/dotnet/fundamentals/code-analysis/quality-rules/il3000) documentazione di aggiunta di un singolo file per IL3000
- [IL3001: evitare di accedere al percorso del file di assembly durante la pubblicazione come singolo file](/dotnet/fundamentals/code-analysis/quality-rules/il3001) : aggiungere documenti per IL3001

**Aggiornato**

- [CA1002: non esporre elenchi generici](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) -sezione aggiunta di configurabilità-superficie API
- [CA1046: non eseguire l'overload dell'operatore uguale ai tipi di riferimento](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) -sezione aggiunta di configurabilità-superficie API
- [CA1307: specificare StringComparison per maggiore chiarezza](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) -aggiungere la documentazione per ca1310 e aggiornare la documentazione per CA1307
- [CA1700: non denominare i valori enum &#39;sezione&#39;riservata ](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) -Aggiungi configurabilità-superficie API
- [CA1707: gli identificatori non devono contenere caratteri di sottolineatura](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) -sezione aggiunta di configurabilità-superficie API
- [CA1822: contrassegna i membri come statici](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) -aggiunta di configurabilità-sezione di superficie dell'API
- [CA2351: assicurarsi che l'input di DataSet. ReadXml () sia attendibile](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) -altre regole DataSet/DataTable
- [Installare gli analizzatori di terze parti](../code-quality/install-roslyn-analyzers.md) : struttura modificata e titoli per la documentazione di analisi del codice

### <a name="containers"></a>Contenitori

**Articoli aggiornati**

- [Distribuire un contenitore ASP.NET in un registro contenitori con Visual Studio](../containers/hosting-web-apps-in-docker.md) -aggiornamenti degli strumenti contenitore per l'interfaccia utente di pubblicazione di visual Studio 16,7
- [Introduzione agli strumenti di Visual Studio Kubernetes](../containers/bridge-to-kubernetes.md) -esercitazione su Kubernetes: aggiungere i passaggi per la rimozione

### <a name="deployment"></a>Distribuzione

**Nuovi articoli**

- [Estensione di progetti programma di installazione di Visual Studio e .net core 3,1](../deployment/installer-projects-net-core.md) -creazione di una nuova pagina della Guida per i progetti di installazione di .net core 3,1 funzionalità

**Articoli aggiornati**

- [Distribuire l'app in una cartella, IIS, Azure o in un'altra destinazione](../deployment/deploying-applications-services-and-components-resources.md) -aggiornamenti della distribuzione
- [Distribuzione in Visual Studio](../deployment/index.yml) -aggiornamenti della distribuzione

### <a name="extensibility"></a>Estendibilità

**Articoli aggiornati**
- [Sottotipi di progetto](../extensibility/internals/project-subtypes.md) -correzione rientri elementi elenco
- [Riferimento al valore del colore per Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) -AB # 1759333 correggere le intestazioni di colonna mancanti

### <a name="get-started"></a>Introduzione

**Articoli aggiornati**

- [Passaggio 5: distribuire l'app ASP.NET Core in Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) -aggiornamenti dell'esercitazione video per la nuova interfaccia utente di servizi connessi

### <a name="ide"></a>IDE

**Nuovi articoli**

- [Modificare il tasto Guida F1 in Visual Studio](./not-in-toc/change-f1-help-key.md) -pagina della Guida sensibile al contesto del refactoring
- [Guida sensibile al contesto per l'editor di testo](./not-in-toc/default-f1-text-editor.md) -pagina della Guida F1 predefinita
- [Convert `typeof` to `nameof` ](./reference/convert-typeof-to-nameof.md) -Convert typeof in refactoring NameOf
- [Semplificare l'espressione LINQ](./reference/simplify-linq-expression.md) -semplificare il refactoring dell'espressione LINQ

**Articoli aggiornati**

- [Personalizzare il layout delle finestre in Visual Studio](./customizing-window-layouts-in-visual-studio.md) : aggiungere informazioni sulle schede del documento verticale con moniker per personalizzare il layout delle finestre.
- [Come segnalare un problema con Visual Studio o il programma di installazione di Visual Studio](./how-to-report-a-problem-with-visual-studio.md)
  - Sono state aggiunte altre informazioni a NMI
  - Pagina di un problema di report completa
- [Guida sensibile](./not-in-toc/default.md) al contesto refactoring-pagina della Guida F1 predefinita
- [Salvataggio automatico, ambiente, finestra di dialogo Opzioni](./reference/autorecover-environment-options-dialog-box.md) -Aggiungi informazioni sui percorsi dei file di salvataggio automatico aggiornati
- [Opzioni, editor di testo, di base (Visual Basic),](./reference/options-text-editor-basic-visual-basic.md) documentazione di base aggiunta in anticipo per gli hint per i nomi dei parametri inline
- [Opzioni, editor di testo, C#,](./reference/options-text-editor-csharp-advanced.md) documentazione di base aggiunta in anticipo per gli hint per i nomi dei parametri inline
- [Suggerimenti per le prestazioni di Visual Studio](./visual-studio-performance-tips-and-tricks.md) : aggiungere le informazioni su "Disabilita modalità mappa" e "Disabilita a capo automatico"
- [Novità di Visual studio 2019](./whats-new-visual-studio-2019.md) -aggiornamento delle novità di visual studio 2019 con le informazioni sulla versione GA di 16,7

### <a name="rtvs"></a>RTVS

**Articoli aggiornati**

- [Usare le tabelle SQL Server e con correzione R](../rtvs/integrating-sql-server-with-r.md) per includere le intestazioni di colonna

## <a name="july-2020"></a>Luglio 2020
### <a name="code-quality"></a>Qualità del codice

**Nuovi articoli**

- [Ca1417: non usare `OutAttribute` nei parametri di stringa per P/Invoke](/dotnet/fundamentals/code-analysis/quality-rules/ca1417) -aggiungere la documentazione per ca1417
- [CA1805: non inizializzare inutilmente.](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) -Aggiungere documenti per CA1805
- Ca1836: preferire il numero di operazioni di i [/o al conteggio quando disponibili](/dotnet/fundamentals/code-analysis/quality-rules/ca1836) -aggiungere la documentazione per ca1836 (preferire il numero di spazio su Count)
- [Ca2016: inviare il parametro CancellationToken ai metodi che accettano un solo](/dotnet/fundamentals/code-analysis/quality-rules/ca2016) documento ca2016-inviare il parametro CancellationToken ai metodi che ne accettano uno
- [CA2350: assicurarsi che l'input di DataTable. ReadXml () sia attendibile](/dotnet/fundamentals/code-analysis/quality-rules/ca2350) -Initial DataSet/DataTable deserializzation Rules docs
- [CA2351: assicurarsi che l'input di DataSet. ReadXml () sia attendibile](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) -Initial DataSet/DataTable deserializzation Rules docs
- [CA2352: il set di dati o l'oggetto DataTable unsafe in un tipo serializzabile può essere vulnerabile agli attacchi di esecuzione di codice in modalità remota](/dotnet/fundamentals/code-analysis/quality-rules/ca2352) . documenti iniziali di deserializzazione DataSet/DataTable
- [CA2353: set di dati o DataTable non sicuro in un tipo serializzabile](/dotnet/fundamentals/code-analysis/quality-rules/ca2353) -tabella iniziale DataSet/DataTable deserializzazione docs
- [CA2354: il set di dati o la DataTable unsafe in un oggetto grafico deserializzato può essere vulnerabile a un attacco di esecuzione di codice in modalità remota](/dotnet/fundamentals/code-analysis/quality-rules/ca2354) . documentazione iniziale di DataSet/DataTable deserializzazione
- [CA2355: set di dati o DataTable non sicuro in un oggetto grafico deserializzato](/dotnet/fundamentals/code-analysis/quality-rules/ca2355) -documenti iniziali DataSet/DataTable deserializzation Rules
- [CA2356: tipo di dati o DataTable non sicuro in un oggetto grafico deserializzato Web](/dotnet/fundamentals/code-analysis/quality-rules/ca2356) -documentazione iniziale relativa alla deserializzazione di DataSet/DataTable

### <a name="containers"></a>Contenitori

**Nuovi articoli**

- [Configurare il processo locale con Kubernetes](../containers/configure-bridge-to-kubernetes.md) -processo locale con Kubernetes: configurazione YAML
- [Usare il processo locale con Kubernetes (anteprima)](../containers/bridge-to-kubernetes.md) -migrazione di spazi di sviluppo
- [Come funziona Processo locale con Kubernetes](../containers/overview-bridge-to-kubernetes.md)
  - Processo locale per Kubernetes: sezione Aggiungi routing
  - Migrazione di spazi di sviluppo

### <a name="cross-platform"></a>Multipiattaforma

**Articoli aggiornati**

- [Log delle modifiche (Visual Studio Tools per Unity, Windows)-modifica](/gamedev/unity/change-log-visual-studio-tools-for-unity.md) del changelog VSTU in 4.7.1.0
- [Log delle modifiche (Visual Studio Tools per Unity, Mac)-modifica](/gamedev/unity/change-log-visual-studio-tools-for-unity-mac.md) del changelog VSTUM in 2.7.1.0

### <a name="get-started"></a>Introduzione

**Nuovi articoli**

- [Esercitazione: estendere una semplice app console C#](../get-started/csharp/tutorial-console-part-2.md) -versione Estendi marciapiede esercitazione prima versione

### <a name="ide"></a>IDE

**Nuovi articoli**

- [Linee guida della community per sviluppatori](./developer-community-guidelines.md) -aggiunta di linee guida DevCom
- [Completamento IntelliSense per i tipi non importati e i metodi di estensione](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>Installazione

**Nuovi articoli**

- [Aggiornare Visual Studio usando un layout minimo offline](../install/update-minimal-layout.md) -documento funzionalità di layout minimo
- [Guida a Visual Studio Enterprise](../install/visual-studio-enterprise-guide.md) -Guida aziendale

### <a name="javascript"></a>JavaScript

**Nuovi articoli**

- [Compila codice typescript (Node.js)](../javascript/compile-typescript-code-npm.md) -compilazione e compilazione typescript
- [Compila codice typescript (ASP.NET Core)](../javascript/compile-typescript-code-nuget.md) -compilazione e compilazione typescript

### <a name="msbuild"></a>MSBuild

**Nuovi articoli**

- [Metadati dell'elemento MSBuild comuni](../msbuild/common-msbuild-item-metadata.md) -MSBuild: aggiungere una tabella per i metadati facoltativi con collegamento e collegamento
- [Filtri della soluzione in MSBuild](../msbuild/solution-filters.md) -filtri della soluzione MSBuild

### <a name="test"></a>Test

**Nuovi articoli**

- [Eseguire il debug e analizzare unit test con Esplora test](../test/debug-unit-tests-with-test-explorer.md) -lavoro prestazioni Esplora test

**Articoli aggiornati**

- [Configurare gli unit test usando un file con *estensione runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - Aggiornamenti per la configurazione di unit test mediante un file runsettings
  - La descrizione dell'opzione Blame è stata modificata ed è stato aggiunto un esempio.