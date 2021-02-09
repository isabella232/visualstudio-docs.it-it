---
title: Eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET
ms.custom: SEO-VS-2020
description: Informazioni su come eseguire la migrazione da analizzatori FxCop ad analizzatori .NET
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
ms.openlocfilehash: e435502587e65bd694567f4100516a91fa97cc0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867867"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET

L'analisi dell'origine per .NET Compiler Platform ("Roslyn") analizzatori sostituisce l' [analisi legacy](code-analysis-for-managed-code-overview.md) per il codice gestito. Molte delle regole di analisi legacy (FxCop) sono già state riscritte come analizzatori di origine.

Prima di Visual Studio 2019 16,8 e .NET 5,0, questi analizzatori venivano forniti come `Microsoft.CodeAnalysis.FxCopAnalyzers` [pacchetto NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

A partire da Visual Studio 2019 16,8 e .NET 5,0, questi analizzatori sono [inclusi in .NET SDK](/dotnet/fundamentals/code-analysis/overview). Se non si vuole passare a .NET 5 + SDK o se si preferisce un modello basato su pacchetti NuGet, gli analizzatori sono anche disponibili nel `Microsoft.CodeAnalysis.NetAnalyzers` [pacchetto NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Per gli aggiornamenti delle versioni su richiesta potrebbe essere preferibile un modello basato su pacchetti.

> [!NOTE]
> Gli analizzatori .NET della prima entità sono indipendenti dalla piattaforma di destinazione. Ovvero non è necessario che il progetto sia destinato a una piattaforma .NET specifica. Gli analizzatori funzionano per i progetti destinati a e per le `net5.0` versioni precedenti di .NET, ad esempio `netcoreapp` , `netstandard` e `net472` .

## <a name="migration-steps"></a>Passaggi della migrazione

A partire dalla versione `3.3.2` , il `Microsoft.CodeAnalysis.FxCopAnalyzers` pacchetto NuGet è stato deprecato. Per eseguire la migrazione del progetto o della soluzione da `Microsoft.CodeAnalysis.FxCopAnalyzers` agli analizzatori .NET, attenersi alla procedura seguente:

1. Disinstalla `Microsoft.CodeAnalysis.FxCopAnalyzers` pacchetto NuGet

2. [Abilitare o installare gli analizzatori .NET](install-net-analyzers.md). Si noti che non è necessario modificare la piattaforma di destinazione del progetto.

3. Enable additional Rules: `Microsoft.CodeAnalysis.NetAnalyzers` è molto più prudente rispetto a `Microsoft.CodeAnalysis.FxCopAnalyzers` . A differenza del pacchetto FxCopAnalyzers, dispone solo di alcune regole di correttezza [abilitate per impostazione predefinita come avvisi di compilazione](/dotnet/fundamentals/code-analysis/overview#enabled-rules). È possibile [abilitare regole aggiuntive](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) personalizzando la proprietà [AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) di MSBuild. Se ad esempio si imposta la proprietà su, per `AllEnabledByDefault` impostazione predefinita tutte le regole CA applicabili vengono abilitate come avvisi di compilazione.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Vedi anche

- [Analisi del codice sorgente rispetto all'analisi legacy](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [Eseguire la migrazione dall'analisi legacy agli analizzatori .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Abilitare o installare gli analizzatori .NET](install-net-analyzers.md)
- [Domande frequenti sugli analizzatori .NET](net-analyzers-faq.md)
- [Configurare gli analizzatori .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
