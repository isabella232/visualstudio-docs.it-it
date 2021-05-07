---
title: Eseguire la migrazione da FxCop all'analisi di origine (analizzatori .NET)
ms.custom: SEO-VS-2020
description: Informazioni su come analizzare il codice per la prima volta o come eseguire la migrazione dall'analisi binaria (FxCop) al nuovo modo di analizzare il codice gestito usando l'analisi del codice sorgente (analizzatori .NET).
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
ms.openlocfilehash: 9a673e7467816e71b8240de9e5f68840c9188dcd
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798232"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Eseguire la migrazione dall'analisi legacy (FxCop) all'analisi di origine (analizzatori .NET)

L'analisi del codice .NET Compiler Platform analizzatori ("Roslyn") sostituisce [l'analisi legacy](../code-quality/code-analysis-for-managed-code-overview.md) per il codice gestito. Per i modelli di progetto più nuovi, ad esempio .NET Core e .NET Standard, l'analisi legacy non è disponibile.

Molte delle regole di analisi legacy (FxCop) sono già state riscritte per gli analizzatori .NET, un set di analizzatori di codice Roslyn. Gli analizzatori Roslyn eseguono l'analisi basata sul codice sorgente durante l'esecuzione del compilatore. I risultati degli analizzatori vengono indicati insieme ai risultati del compilatore.

Per altre informazioni sulle differenze tra l'analisi legacy e l'analisi di origine, vedere quanto segue:

- [Analisi del codice sorgente e analisi legacy](../code-quality/net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)

- [Domande frequenti sugli analizzatori .NET](../code-quality/net-analyzers-faq.yml)

## <a name="migration"></a>Migrazione

Per eseguire la migrazione all'analisi [di origine, abilitare o installare gli analizzatori .NET.](install-net-analyzers.md) Analogamente alle violazioni delle regole di analisi legacy, le violazioni dell'analisi del codice sorgente vengono visualizzate nella finestra Elenco errori in Visual Studio. Inoltre, le violazioni dell'analisi del codice sorgente vengono anche mostrate nell'editor di codice come a *comparsa* sotto il codice in errore. Il colore della linea ondulata dipende dall'[impostazione di gravità](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) della regola. Per visualizzare lo stato delle regole portate ai nuovi analizzatori .NET, vedere Regole portate e [non esportate.](../code-quality/fxcop-rule-port-status.md)

> [!NOTE]
> Prima di Visual Studio 2019 16.8 e .NET 5.0, questi analizzatori sono stati forniti come `Microsoft.CodeAnalysis.FxCopAnalyzers` [pacchetto NuGet.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) A partire Visual Studio 2019 16.8 e .NET 5.0, questi analizzatori sono [inclusi in .NET SDK.](/dotnet/fundamentals/code-analysis/overview) Sono disponibili anche come `Microsoft.CodeAnalysis.NetAnalyzers` [pacchetto NuGet.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) Per altre informazioni, vedere [Eseguire la migrazione da analizzatori FxCop a analizzatori .NET.](migrate-from-fxcop-analyzers-to-net-analyzers.md)

## <a name="configuration"></a>Configurazione

Per altre informazioni su come configurare gli analizzatori .NET:

- Per configurare gli analizzatori .NET, vedere [Configurare gli analizzatori .NET.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)

- Per informazioni sulla configurazione degli analizzatori usando regole predefinite con EditorConfig o un file del set di regole, vedere [Abilitare una categoria di regole.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)

## <a name="see-also"></a>Vedi anche

- [Eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
