---
title: Eseguire la migrazione da FxCop a Analysis Source (analizzatori .NET)
ms.custom: SEO-VS-2020
description: Informazioni su come analizzare il codice per la prima volta o su come eseguire la migrazione dall'analisi binaria (FxCop) al nuovo metodo di analisi del codice gestito tramite l'analisi dell'origine (analizzatori .NET).
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
manager: jillfra
ms.openlocfilehash: 84acec58ed78884f0b037950fa25ce40f6adcbfc
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112234"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Migrare da analisi legacy (FxCop) a analisi origine (analizzatori .NET)

L'analisi dell'origine per .NET Compiler Platform ("Roslyn") analizzatori sostituisce l' [analisi legacy](../code-quality/code-analysis-for-managed-code-overview.md) per il codice gestito. Per i modelli di progetto più recenti, ad esempio i progetti .NET Core e .NET Standard, l'analisi legacy non è disponibile.

Molte delle regole di analisi legacy (FxCop) sono già state riscritte per gli analizzatori .NET, un set di analizzatori di codice Roslyn. Gli analizzatori Roslyn eseguono l'analisi basata sul codice sorgente durante l'esecuzione del compilatore. I risultati degli analizzatori vengono indicati insieme ai risultati del compilatore.

Per ulteriori informazioni sulle differenze tra l'analisi legacy e l'analisi dell'origine, vedere gli argomenti seguenti:

- [Analisi del codice sorgente rispetto all'analisi legacy](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)

- [Domande frequenti sugli analizzatori .NET](../code-quality/net-analyzers-faq.md)

## <a name="migration"></a>Migrazione

Per eseguire la migrazione all'analisi [dell'origine, abilitare o installare gli analizzatori .NET](install-net-analyzers.md). Analogamente alle violazioni delle regole di analisi legacy, le violazioni dell'analisi del codice sorgente vengono visualizzate nella finestra di Elenco errori in Visual Studio. Inoltre, le violazioni dell'analisi del codice sorgente vengono visualizzate nell'editor di codice come *controllo ortografia durante* sotto il codice che causa il danneggiamento. Il colore della linea ondulata dipende dall'[impostazione di gravità](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) della regola. Per visualizzare lo stato delle regole trasferite ai nuovi analizzatori .NET, vedere [porte e regole non portate](../code-quality/fxcop-rule-port-status.md).

> [!NOTE]
> Prima di Visual Studio 2019 16,8 e .NET 5,0, questi analizzatori venivano forniti come `Microsoft.CodeAnalysis.FxCopAnalyzers` [pacchetto NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). A partire da Visual Studio 2019 16,8 e .NET 5,0, questi analizzatori sono [inclusi in .NET SDK](/dotnet/fundamentals/code-analysis/overview). Sono disponibili anche come `Microsoft.CodeAnalysis.NetAnalyzers` [pacchetto NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Per altre informazioni, vedere [eseguire la migrazione da analizzatori FxCop ad analizzatori .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="configuration"></a>Configurazione

Per ulteriori informazioni sulla configurazione degli analizzatori .NET:

- Per configurare gli analizzatori .NET, vedere [configurare gli analizzatori .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- Per informazioni sulla configurazione degli analizzatori con regole predefinite con EditorConfig o un file del set di regole, vedere [abilitare una categoria di regole](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

## <a name="see-also"></a>Vedere anche

- [Eseguire la migrazione da analizzatori FxCop ad analizzatori .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
