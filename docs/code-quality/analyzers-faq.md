---
title: EditorConfig rispetto agli analizzatori
ms.date: 03/11/2019
description: Informazioni sull'analisi del codice basata su .NET Compiler Platform in Visual Studio. Vedere le risposte alle domande su file EditorConfig, set di regole e altri argomenti.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20d566937286743a684ecce2ff54ff2cafe4b3a4
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348393"
---
# <a name="code-analysis-faq"></a>Domande frequenti sull'analisi del codice

Questa pagina contiene le risposte ad alcune domande frequenti sull'analisi del codice basata su .NET Compiler Platform in Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analisi codice rispetto a EditorConfig

**D** : è consigliabile usare l'analisi del codice o EditorConfig per controllare lo stile del codice?

**R: l'** analisi del codice e i file EditorConfig funzionano manualmente. Quando si definiscono gli stili [di codice in un file EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options) o nella pagina [Opzioni editor di testo](../ide/code-styles-and-code-cleanup.md) , si configurano effettivamente gli analizzatori di codice incorporati in Visual Studio. I file EditorConfig possono essere usati per abilitare o disabilitare le regole dell'analizzatore e anche per configurare i pacchetti di NuGet Analyzer.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig rispetto ai set di regole

**D** : è necessario configurare gli analizzatori utilizzando un set di regole o un file EditorConfig?

**R** : i set di regole e i file EditorConfig possono coesistere e possono essere usati entrambi per configurare gli analizzatori. Sia i file EditorConfig che i set di regole consentono di abilitare e disabilitare le regole e di impostarne la gravità.

Tuttavia, i file EditorConfig offrono modi aggiuntivi per configurare le regole:

- Per gli analizzatori di qualità del codice .NET, i file EditorConfig consentono [di definire i tipi di codice da analizzare](/dotnet/fundamentals/code-analysis/code-quality-rule-options).
- Per gli analizzatori di tipo codice .NET incorporati in Visual Studio, i file EditorConfig consentono di [definire gli stili di codice preferiti](/dotnet/fundamentals/code-analysis/code-style-rule-options) per una codebase.

Oltre ai set di regole e ai file EditorConfig, alcuni analizzatori sono configurati tramite l'uso di file di testo contrassegnati come [file aggiuntivi](../ide/build-actions.md#build-action-values) per i compilatori C# e VB.

> [!NOTE]
> - I file EditorConfig possono essere usati solo per abilitare le regole e per impostarne la gravità in Visual Studio 2019 versione 16,3 e successive.
> - Non è possibile usare i file EditorConfig per configurare l'analisi legacy, mentre i set di regole possono.

## <a name="code-analysis-in-ci-builds"></a>Analisi del codice nelle compilazioni CI

**D** : l'analisi del codice basata su .NET Compiler Platform funziona in compilazioni di integrazione continua (ci)?

**R** : Sì. Per gli analizzatori installati da un pacchetto NuGet, tali regole vengono [applicate in fase di compilazione](roslyn-analyzers-overview.md#build-errors), incluso durante una compilazione ci. Gli analizzatori usati nelle compilazioni CI rispettano la configurazione della regola da entrambi i set di regole e file EditorConfig. Attualmente, gli analizzatori di codice incorporati in Visual Studio non sono disponibili come pacchetto NuGet, quindi queste regole non sono applicabili in una compilazione CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analizzatori IDE rispetto a StyleCop

**D** : qual è la differenza tra gli analizzatori di codice IDE di Visual Studio e gli analizzatori StyleCop?

**R** : l'IDE di Visual Studio include analizzatori incorporati che cercano sia lo stile del codice che i problemi di qualità. Queste regole consentono di usare le nuove funzionalità del linguaggio Man mano che sono state introdotte e di migliorare la gestibilità del codice. Gli analizzatori IDE vengono continuamente aggiornati con ogni versione di Visual Studio.

Gli [analizzatori StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) sono analizzatori di terze parti installati come pacchetto NuGet che verificano la coerenza dello stile nel codice. In generale, le regole StyleCop consentono di impostare le preferenze personali per una codebase senza suggerire uno stile rispetto a un altro.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizzatori del codice rispetto all'analisi legacy

**D** : qual è la differenza tra analisi legacy e analisi del codice basata su .NET Compiler Platform?

**R: l'** analisi del codice basata su .NET Compiler Platform analizza il codice sorgente in tempo reale e durante la compilazione, mentre analisi legacy analizza i file binari al termine della compilazione. Per altre informazioni, vedere [analisi basata su .NET Compiler Platform e analisi legacy](../code-quality/fxcop-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers).

## <a name="treat-warnings-as-errors"></a>Considera gli avvisi come errori

**D** : il progetto usa l'opzione di compilazione per considerare gli avvisi come errori. Dopo la migrazione dall'analisi legacy all'analisi del codice sorgente, tutti gli avvisi di analisi del codice sono ora visualizzati come errori. Come è possibile evitare questo?

**R** : per impedire che gli avvisi di analisi del codice vengano considerati come errori, attenersi alla seguente procedura:

  1. Creare un file con estensione Props con il contenuto seguente:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Aggiungere una riga al file di progetto con estensione csproj o vbproj per importare il file con estensione Props creato nel passaggio precedente. Questa riga deve essere posizionata prima di tutte le righe che importano i file di FxCop Analyzer. props. Ad esempio, se il file. props è denominato CodeAnalysis. props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Pagina delle proprietà della soluzione analisi codice

**D** : dove è la pagina delle proprietà di analisi del codice per la soluzione?

**R** : la pagina delle proprietà dell'analisi del codice a livello di soluzione è stata rimossa a favore del gruppo di proprietà condiviso più affidabile. Per la gestione dell'analisi del codice a livello di progetto, la pagina delle proprietà analisi codice è ancora disponibile. Per i progetti gestiti, è anche consigliabile eseguire la migrazione da RuleSets a EditorConfig per la configurazione delle regole.  Per la condivisione di RuleSet tra più progetti in una soluzione o in un repository, è consigliabile definire un gruppo di proprietà con la proprietà CodeAnalysisRuleSet in un file props/targets condiviso o in un file directory. props/directory. targets. Se non si dispone di tali oggetti o destinazioni comuni che tutti i progetti importano, è consigliabile [aggiungere tale gruppo di proprietà a una directory. props o a una directory. targets in una directory della soluzione di primo livello, che viene importata automaticamente in tutti i file di progetto definiti nella directory o nelle relative sottodirectory](../msbuild/customize-your-build.md).

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori](roslyn-analyzers-overview.md)
- [Impostazioni della convenzione di codifica .NET per EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)