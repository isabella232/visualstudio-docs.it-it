---
title: EditorConfig e analizzatori
ms.date: 03/11/2019
description: Informazioni sull.NET Compiler Platform a analisi del codice basata su Visual Studio. Vedere le risposte alle domande su file EditorConfig, set di regole e altri argomenti.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6d67471027f36d0e22c055f4306ce2137d972463
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800510"
---
# <a name="code-analysis-faq"></a>Domande frequenti sull'analisi del codice

Questa pagina contiene le risposte ad alcune domande frequenti sull.NET Compiler Platform di codice basata su Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analisi del codice e EditorConfig

**D:** È consigliabile usare l'analisi del codice o EditorConfig per controllare lo stile del codice?

**A**: l'analisi del codice e i file EditorConfig funzionano in modo manuale. Quando si definiscono gli stili di codice in un [file EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options) o nella pagina Opzioni dell'editor di testo, si configurano effettivamente gli analizzatori di codice incorporati in Visual Studio. [](../ide/code-styles-and-code-cleanup.md) I file EditorConfig possono essere usati per abilitare o disabilitare le regole dell'analizzatore e anche per configurare i pacchetti dell'analizzatore NuGet.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig e set di regole

**D:** È consigliabile configurare gli analizzatori usando un set di regole o un file EditorConfig?

**A:** i set di regole e i file EditorConfig possono coesistere ed entrambi possono essere usati per configurare gli analizzatori. Sia i file EditorConfig che i set di regole consentono di abilitare e disabilitare le regole e di impostarne la gravità.

Tuttavia, i file EditorConfig offrono anche altri modi per configurare le regole:

- Per gli analizzatori di qualità del codice .NET, i file EditorConfig consentono di [definire i tipi di codice da analizzare.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
- Per gli analizzatori di tipo codice .NET incorporati in Visual Studio, i file EditorConfig consentono di definire gli stili di codice preferiti [per](/dotnet/fundamentals/code-analysis/code-style-rule-options) una codebase.

Oltre ai set di regole e ai file EditorConfig, alcuni analizzatori vengono configurati tramite l'uso di file di testo contrassegnati come [file aggiuntivi](../ide/build-actions.md#build-action-values) per i compilatori C# e VB.

> [!NOTE]
> - I file EditorConfig possono essere usati solo per abilitare le regole e impostarne la gravità in Visual Studio 2019 versione 16.3 e successive.
> - I file EditorConfig non possono essere usati per configurare l'analisi legacy, mentre i set di regole possono.

## <a name="code-analysis-in-ci-builds"></a>Analisi del codice nelle compilazioni CI

**D:** L.NET Compiler Platform'analisi del codice basata su funzioni nelle compilazioni di integrazione continua?

**R**: Sì. Per gli analizzatori installati da un pacchetto NuGet, queste regole vengono applicate in fase di [compilazione,](roslyn-analyzers-overview.md#build-errors)anche durante una compilazione ci. Gli analizzatori usati nelle compilazioni CI rispettano la configurazione delle regole dai set di regole e dai file EditorConfig. Attualmente, gli analizzatori di codice incorporati in Visual Studio non sono disponibili come pacchetto NuGet e pertanto queste regole non sono imponibili in una compilazione ci.

## <a name="ide-analyzers-versus-stylecop"></a>Analizzatori IDE e StyleCop

**D:** Qual è la differenza tra gli analizzatori Visual Studio codice IDE e gli analizzatori StyleCop?

**Oggetto**: l Visual Studio IDE include analizzatori predefiniti che ricercano sia problemi di stile del codice che di qualità. Queste regole consentono di usare nuove funzionalità del linguaggio quando vengono introdotte e migliorano la manutenibilità del codice. Gli analizzatori IDE vengono aggiornati continuamente con ogni Visual Studio versione.

[Gli analizzatori StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) sono analizzatori di terze parti installati come pacchetto NuGet che verificano la coerenza dello stile nel codice. In generale, le regole StyleCop consentono di impostare preferenze personali per una codebase senza consigliare uno stile rispetto a un altro.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizzatori del codice e analisi legacy

**D:** Qual è la differenza tra l'analisi legacy e l'.NET Compiler Platform di codice basata sull'analisi?

**:** l.NET Compiler Platform-based code analysis analizza il codice sorgente in tempo reale e durante la compilazione, mentre l'analisi legacy analizza i file binari al termine della compilazione. Per altre informazioni, vedere Analisi basata .NET Compiler Platform e [analisi legacy.](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)

## <a name="fxcop-analyzers-versus-net-analyzers"></a>Analizzatori FxCop e analizzatori .NET

**D:** Qual è la differenza tra gli analizzatori FxCop e gli analizzatori .NET?

**A:** sia gli analizzatori FxCop che gli analizzatori .NET fanno riferimento alle implementazioni dell'analizzatore .NET Compiler Platform ("Roslyn") delle regole della CA FxCop. Prima di Visual Studio 2019 16.8 e .NET 5.0, questi analizzatori sono stati forniti come `Microsoft.CodeAnalysis.FxCopAnalyzers` [pacchetto NuGet.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) A partire Visual Studio 2019 16.8 e .NET 5.0, questi analizzatori sono [inclusi in .NET SDK.](/dotnet/fundamentals/code-analysis/overview) Sono disponibili anche come `Microsoft.CodeAnalysis.NetAnalyzers` [pacchetto NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Prendere in [considerazione la migrazione dagli analizzatori FxCop agli analizzatori .NET.](migrate-from-fxcop-analyzers-to-net-analyzers.md)

## <a name="treat-warnings-as-errors"></a>Considera gli avvisi come errori

**D:** Il progetto usa l'opzione di compilazione per considerare gli avvisi come errori. Dopo la migrazione dall'analisi legacy all'analisi del codice sorgente, tutti gli avvisi di analisi del codice vengono ora visualizzati come errori. Come è possibile evitarlo?

**A:** Per evitare che gli avvisi di analisi del codice vengano considerati come errori, seguire questa procedura:

  1. Creare un file props con il contenuto seguente:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Aggiungere una riga al file di progetto con estensione csproj o vbproj per importare il file props creato nel passaggio precedente. Questa riga deve essere posizionata prima delle righe che importano i file props dell'analizzatore. Ad esempio, se il file con estensione props è denominato codeanalysis.props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Pagina delle proprietà della soluzione analisi codice

**D:** Dove si trova la Code Analysis delle proprietà per la soluzione?

**A**: la Code Analysis proprietà a livello di soluzione è stata rimossa a favore del gruppo di proprietà condiviso più affidabile. Per la Code Analysis a livello di progetto, la pagina Code Analysis proprietà è ancora disponibile. Per i progetti gestiti, è anche consigliabile eseguire la migrazione dai set di regole a EditorConfig per la configurazione delle regole.  Per condividere set di regole tra più/tutti i progetti in una soluzione o in un repo, è consigliabile definire un gruppo di proprietà con la proprietà [CodeAnalysisRuleSet](../code-quality/using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) in un file props/targets condiviso o in un file *Directory.props/Directory.targets.* Se non sono presenti proprietà o destinazioni comuni importate da tutti i progetti, è consigliabile aggiungere tale gruppo di proprietà a [un file Directory.props o Directory.targets](../msbuild/customize-your-build.md) in una directory della soluzione di primo livello, che viene importata automaticamente in tutti i file di progetto definiti nella directory o nelle relative sottodirectory.

## <a name="see-also"></a>Vedi anche

- [Panoramica degli analizzatori](roslyn-analyzers-overview.md)
- [Impostazioni delle convenzioni di codifica .NET per EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)