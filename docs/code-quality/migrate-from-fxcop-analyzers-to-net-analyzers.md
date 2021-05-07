---
title: Eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET
ms.custom: SEO-VS-2020
description: Informazioni su come eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: d6f9c36b1b64abe648c3aa9014c633e4e4949b1a
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798258"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET

L'analisi del .NET Compiler Platform analizzatori ("Roslyn") sostituisce [l'analisi legacy](code-analysis-for-managed-code-overview.md) per il codice gestito. Molte delle regole di analisi legacy (FxCop) sono già state riscritte come analizzatori di origine.

Prima di Visual Studio 2019 16.8 e .NET 5.0, questi analizzatori sono stati forniti come `Microsoft.CodeAnalysis.FxCopAnalyzers` [pacchetto NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

A partire Visual Studio 2019 16.8 e .NET 5.0, questi analizzatori sono [inclusi in .NET SDK.](/dotnet/fundamentals/code-analysis/overview) Se non si vuole passare a .NET 5+ SDK o se si preferisce un modello basato su pacchetti NuGet, gli analizzatori sono disponibili anche nel `Microsoft.CodeAnalysis.NetAnalyzers` [pacchetto NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Si potrebbe preferire un modello basato su pacchetto per gli aggiornamenti di versione su richiesta.

> [!NOTE]
> Gli analizzatori .NET di prima parte sono indipendenti dalla piattaforma di destinazione. Ciò significa che il progetto non deve avere come destinazione una piattaforma .NET specifica. Gli analizzatori funzionano per i progetti che hanno come destinazione e versioni `net5.0` precedenti di .NET, ad esempio `netcoreapp` , e `netstandard` `net472` .

## <a name="migration-steps"></a>Passaggi della migrazione

A partire dalla `3.3.2` versione , il pacchetto `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet è stato deprecato. Seguire questa procedura per eseguire la migrazione del progetto o della soluzione `Microsoft.CodeAnalysis.FxCopAnalyzers` da agli analizzatori .NET:

1. Disinstallare `Microsoft.CodeAnalysis.FxCopAnalyzers` il pacchetto NuGet

2. [Abilitare o installare gli analizzatori .NET.](install-net-analyzers.md) Si noti che non è necessario modificare la piattaforma di destinazione del progetto.

3. Abilitare regole aggiuntive: `Microsoft.CodeAnalysis.NetAnalyzers` è molto più conservativo rispetto a `Microsoft.CodeAnalysis.FxCopAnalyzers` . A differenza del pacchetto FxCopAnalyzers, ha solo alcune regole di correttezza abilitate per impostazione predefinita [come avvisi di compilazione.](/dotnet/fundamentals/code-analysis/overview#enabled-rules) È possibile [abilitare regole aggiuntive](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) personalizzando la proprietà MSBuild [AnalysisMode.](/dotnet/core/project-sdk/msbuild-props#analysismode) Ad esempio, l'impostazione della proprietà su `AllEnabledByDefault` abiliterà tutte le regole della CA applicabili come avvisi di compilazione per impostazione predefinita.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Vedi anche

- [Analisi del codice sorgente e analisi legacy](net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)
- [Eseguire la migrazione dall'analisi legacy agli analizzatori .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Abilitare o installare analizzatori .NET](install-net-analyzers.md)
- [Domande frequenti sugli analizzatori .NET](net-analyzers-faq.yml)
- [Configurare gli analizzatori .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
