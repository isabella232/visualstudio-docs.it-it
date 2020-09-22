---
title: 'Documenti di Visual Studio: cronologia delle novità '
titleSuffix: ''
description: Cronologia delle novità nella documentazione di Visual Studio
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
ms.openlocfilehash: 8505f98163c57fe276bcf4c76195fe843300394f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809466"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Cronologia delle novità nella documentazione di Visual Studio

Benvenuti alla cronologia delle novità di Visual Studio docs. Questo argomento contiene le principali modifiche apportate ai documenti prima del 2020 agosto (a partire da luglio 2020). Per le ultime novità, vedere la [documentazione di Visual Studio:](whats-new-visual-studio-docs.md)novità della documentazione.

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

### <a name="get-started"></a>Operazioni preliminari

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