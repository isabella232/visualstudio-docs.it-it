---
title: 'Documenti di Visual Studio: cronologia delle novità '
titleSuffix: ''
description: Cronologia delle novità di Visual Studio docs
ms.date: 09/01/2020
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
ms.openlocfilehash: 9f5fc25f6bb25c9471b1de1d464fa6afc4c80b3b
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "89410507"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Cronologia delle novità di Visual Studio docs

Benvenuti alla cronologia delle novità di Visual Studio docs. Questo argomento contiene le principali modifiche apportate ai documenti prima del 2020 agosto (a partire da luglio 2020). Per le ultime novità, vedere la [documentazione di Visual Studio:](whats-new-visual-studio-docs.md)novità della documentazione.

## <a name="july-2020"></a>Luglio 2020
### <a name="code-quality"></a>Qualità del codice

**Nuovi articoli**

- [Ca1417: non usare `OutAttribute` nei parametri di stringa per P/Invoke](/visualstudio/code-quality/ca1417) -aggiungere la documentazione per ca1417
- [CA1805: non inizializzare inutilmente.](/visualstudio/code-quality/ca1805) -Aggiungere documenti per CA1805
- Ca1836: preferire il numero di operazioni di i [/o al conteggio quando disponibili](/visualstudio/code-quality/ca1836) -aggiungere la documentazione per ca1836 (preferire il numero di spazio su Count)
- [Ca2016: inviare il parametro CancellationToken ai metodi che accettano un solo](/visualstudio/code-quality/ca2016) documento ca2016-inviare il parametro CancellationToken ai metodi che ne accettano uno
- [CA2350: assicurarsi che l'input di DataTable. ReadXml () sia attendibile](/visualstudio/code-quality/ca2350) -Initial DataSet/DataTable deserializzation Rules docs
- [CA2351: assicurarsi che l'input di DataSet. ReadXml () sia attendibile](/visualstudio/code-quality/ca2351) -Initial DataSet/DataTable deserializzation Rules docs
- [CA2352: il set di dati o l'oggetto DataTable unsafe in un tipo serializzabile può essere vulnerabile agli attacchi di esecuzione di codice in modalità remota](/visualstudio/code-quality/ca2352) . documenti iniziali di deserializzazione DataSet/DataTable
- [CA2353: set di dati o DataTable non sicuro in un tipo serializzabile](/visualstudio/code-quality/ca2353) -tabella iniziale DataSet/DataTable deserializzazione docs
- [CA2354: il set di dati o la DataTable unsafe in un oggetto grafico deserializzato può essere vulnerabile a un attacco di esecuzione di codice in modalità remota](/visualstudio/code-quality/ca2354) . documentazione iniziale di DataSet/DataTable deserializzazione
- [CA2355: set di dati o DataTable non sicuro in un oggetto grafico deserializzato](/visualstudio/code-quality/ca2355) -documenti iniziali DataSet/DataTable deserializzation Rules
- [CA2356: tipo di dati o DataTable non sicuro in un oggetto grafico deserializzato Web](/visualstudio/code-quality/ca2356) -documentazione iniziale relativa alla deserializzazione di DataSet/DataTable

### <a name="containers"></a>Contenitori

**Nuovi articoli**

- [Configurare il processo locale con Kubernetes](/visualstudio/containers/configure-local-process-with-kubernetes) -processo locale con Kubernetes: configurazione YAML
- [Usare il processo locale con Kubernetes (anteprima)](/visualstudio/containers/local-process-kubernetes) -migrazione di spazi di sviluppo
- [Come funziona Processo locale con Kubernetes](/visualstudio/containers/overview-local-process-kubernetes)
  - Processo locale per Kubernetes: sezione Aggiungi routing
  - Migrazione di spazi di sviluppo

### <a name="cross-platform"></a>Multipiattaforma

**Articoli aggiornati**

- [Log delle modifiche (Visual Studio Tools per Unity, Windows)-modifica](/visualstudio/cross-platform/change-log-visual-studio-tools-for-unity) del changelog VSTU in 4.7.1.0
- [Log delle modifiche (Visual Studio Tools per Unity, Mac)-modifica](/visualstudio/cross-platform/change-log-visual-studio-tools-for-unity-mac) del changelog VSTUM in 2.7.1.0

### <a name="get-started"></a>Introduzione

**Nuovi articoli**

- [Esercitazione: estendere una semplice app console C#](/visualstudio/get-started/csharp/tutorial-console-part-2) -versione Estendi marciapiede esercitazione prima versione

### <a name="ide"></a>IDE

**Nuovi articoli**

- [Linee guida della community per sviluppatori](/visualstudio/ide/developer-community-guidelines) -aggiunta di linee guida DevCom
- [Completamento IntelliSense per i tipi non importati e i metodi di estensione](/visualstudio/ide/reference/intellisense-completion-unimported-types-extension-methods)

### <a name="install"></a>Installazione

**Nuovi articoli**

- [Aggiornare Visual Studio usando un layout minimo offline](/visualstudio/install/update-minimal-layout) -documento funzionalità di layout minimo
- [Guida a Visual Studio Enterprise](/visualstudio/install/visual-studio-enterprise-guide) -Guida aziendale

### <a name="javascript"></a>JavaScript

**Nuovi articoli**

- [Compila codice typescript (Node.js)](/visualstudio/javascript/compile-typescript-code-npm) -compilazione e compilazione typescript
- [Compila codice typescript (ASP.NET Core)](/visualstudio/javascript/compile-typescript-code-nuget) -compilazione e compilazione typescript

### <a name="msbuild"></a>MSBuild

**Nuovi articoli**

- [Metadati dell'elemento MSBuild comuni](/visualstudio/msbuild/common-msbuild-item-metadata) -MSBuild: aggiungere una tabella per i metadati facoltativi con collegamento e collegamento
- [Filtri della soluzione in MSBuild](/visualstudio/msbuild/solution-filters) -filtri della soluzione MSBuild

### <a name="test"></a>Test

**Nuovi articoli**

- [Eseguire il debug e analizzare unit test con Esplora test](/visualstudio/test/debug-unit-tests-with-test-explorer) -lavoro prestazioni Esplora test

**Articoli aggiornati**

- [Configurare gli unit test usando un file con *estensione runsettings*](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - Aggiornamenti per la configurazione di unit test mediante un file runsettings
  - La descrizione dell'opzione Blame è stata modificata ed è stato aggiunto un esempio.