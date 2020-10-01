---
title: 'Documenti di Visual Studio: cronologia delle novità '
titleSuffix: ''
description: Cronologia delle novità nella documentazione di Visual Studio
ms.date: 09/30/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 6d0b60c548e4e5d42a10e82754d045073f016f8b
ms.sourcegitcommit: ea3c985a23851b424127f2205f617446b6536578
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2020
ms.locfileid: "91621750"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Cronologia delle novità nella documentazione di Visual Studio

Benvenuti alla cronologia delle novità di Visual Studio docs. Questo argomento contiene le principali modifiche apportate ai documenti prima del 2020 settembre (a partire dal luglio 2020). Per le ultime novità, vedere la [documentazione di Visual Studio:](whats-new-visual-studio-docs.md)novità della documentazione.

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

- [Ca1310: specificare StringComparison per la correttezza](../code-quality/ca1310.md) -aggiungere la documentazione per ca1310 e aggiornare la documentazione per CA1307
- [Ca1837: usare Environment. ProcessId anziché Process. GetCurrentProcess (). ID](../code-quality/ca1837.md) -docs per ca1837
- [Ca1838: evitare `StringBuilder` i parametri per P/Invoke](../code-quality/ca1838.md) -aggiungere la documentazione per ca1838
- [Ca2008: non creare attività senza passare un TaskScheduler](../code-quality/ca2008.md) -aggiungere la documentazione per ca2008
- [CA2249: provare a usare String. Contains anziché String. IndexOf](../code-quality/ca2249.md) -docs per CA2249
- [CA2361: assicurarsi che la classe generata automaticamente contenente DataSet. ReadXml () non venga usata con dati non attendibili](../code-quality/ca2361.md) -altre regole DataSet/DataTable
- [CA2362: il set di dati o la DataTable unsafe nel tipo serializzabile generato automaticamente può essere vulnerabile agli attacchi di esecuzione di codice in modalità remota](../code-quality/ca2362.md) . altre regole DataSet/DataTable
- [IL3000: evitare di usare l'accesso al percorso del file di assembly quando si pubblica come](../code-quality/il3000.md) documentazione di aggiunta di un singolo file per IL3000
- [IL3001: evitare di accedere al percorso del file di assembly durante la pubblicazione come singolo file](../code-quality/il3001.md) : aggiungere documenti per IL3001

**Aggiornato**

- [CA1002: non esporre elenchi generici](../code-quality/ca1002.md) -sezione aggiunta di configurabilità-superficie API
- [CA1046: non eseguire l'overload dell'operatore uguale ai tipi di riferimento](../code-quality/ca1046.md) -sezione aggiunta di configurabilità-superficie API
- [CA1307: specificare StringComparison per maggiore chiarezza](../code-quality/ca1307.md) -aggiungere la documentazione per ca1310 e aggiornare la documentazione per CA1307
- [CA1700: non denominare i valori enum &#39;sezione&#39;riservata ](../code-quality/ca1700.md) -Aggiungi configurabilità-superficie API
- [CA1707: gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707.md) -sezione aggiunta di configurabilità-superficie API
- [CA1822: contrassegna i membri come statici](../code-quality/ca1822.md) -aggiunta di configurabilità-sezione di superficie dell'API
- [CA2351: assicurarsi che l'input di DataSet. ReadXml () sia attendibile](../code-quality/ca2351.md) -altre regole DataSet/DataTable
- [Installare gli analizzatori di terze parti](../code-quality/install-roslyn-analyzers.md) : struttura modificata e titoli per la documentazione di analisi del codice

### <a name="containers"></a>Contenitori

**Articoli aggiornati**

- [Distribuire un contenitore ASP.NET in un registro contenitori con Visual Studio](../containers/hosting-web-apps-in-docker.md) -aggiornamenti degli strumenti contenitore per l'interfaccia utente di pubblicazione di visual Studio 16,7
- [Introduzione agli strumenti di Visual Studio Kubernetes](../containers/tutorial-kubernetes-tools.md) -esercitazione su Kubernetes: aggiungere i passaggi per la rimozione

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

- [Personalizzare il layout delle finestre in Visual Studio](./customizing-window-layouts-in-visual-studio.md) -aggiungere informazioni sulle schede del documento verticale con moniker per personalizzare il layout delle finestre
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

- [Ca1417: non usare `OutAttribute` nei parametri di stringa per P/Invoke](../code-quality/ca1417.md) -aggiungere la documentazione per ca1417
- [CA1805: non inizializzare inutilmente.](../code-quality/ca1805.md) -Aggiungere documenti per CA1805
- Ca1836: preferire il numero di operazioni di i [/o al conteggio quando disponibili](../code-quality/ca1836.md) -aggiungere la documentazione per ca1836 (preferire il numero di spazio su Count)
- [Ca2016: inviare il parametro CancellationToken ai metodi che accettano un solo](../code-quality/ca2016.md) documento ca2016-inviare il parametro CancellationToken ai metodi che ne accettano uno
- [CA2350: assicurarsi che l'input di DataTable. ReadXml () sia attendibile](../code-quality/ca2350.md) -Initial DataSet/DataTable deserializzation Rules docs
- [CA2351: assicurarsi che l'input di DataSet. ReadXml () sia attendibile](../code-quality/ca2351.md) -Initial DataSet/DataTable deserializzation Rules docs
- [CA2352: il set di dati o l'oggetto DataTable unsafe in un tipo serializzabile può essere vulnerabile agli attacchi di esecuzione di codice in modalità remota](../code-quality/ca2352.md) . documenti iniziali di deserializzazione DataSet/DataTable
- [CA2353: set di dati o DataTable non sicuro in un tipo serializzabile](../code-quality/ca2353.md) -tabella iniziale DataSet/DataTable deserializzazione docs
- [CA2354: il set di dati o la DataTable unsafe in un oggetto grafico deserializzato può essere vulnerabile a un attacco di esecuzione di codice in modalità remota](../code-quality/ca2354.md) . documentazione iniziale di DataSet/DataTable deserializzazione
- [CA2355: set di dati o DataTable non sicuro in un oggetto grafico deserializzato](../code-quality/ca2355.md) -documenti iniziali DataSet/DataTable deserializzation Rules
- [CA2356: tipo di dati o DataTable non sicuro in un oggetto grafico deserializzato Web](../code-quality/ca2356.md) -documentazione iniziale relativa alla deserializzazione di DataSet/DataTable

### <a name="containers"></a>Contenitori

**Nuovi articoli**

- [Configurare il processo locale con Kubernetes](../containers/configure-local-process-with-kubernetes.md) -processo locale con Kubernetes: configurazione YAML
- [Usare il processo locale con Kubernetes (anteprima)](../containers/local-process-kubernetes.md) -migrazione di spazi di sviluppo
- [Come funziona Processo locale con Kubernetes](../containers/overview-local-process-kubernetes.md)
  - Processo locale per Kubernetes: sezione Aggiungi routing
  - Migrazione di spazi di sviluppo

### <a name="cross-platform"></a>Multipiattaforma

**Articoli aggiornati**

- [Log delle modifiche (Visual Studio Tools per Unity, Windows)-modifica](../cross-platform/change-log-visual-studio-tools-for-unity.md) del changelog VSTU in 4.7.1.0
- [Log delle modifiche (Visual Studio Tools per Unity, Mac)-modifica](../cross-platform/change-log-visual-studio-tools-for-unity-mac.md) del changelog VSTUM in 2.7.1.0

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