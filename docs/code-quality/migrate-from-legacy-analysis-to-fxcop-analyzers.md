---
title: Eseguire la migrazione dall'analisi legacy (FxCop) all'analisi dell'origine (analizzatori FxCop)
description: Informazioni su come analizzare il codice per la prima volta o su come eseguire la migrazione dall'analisi binaria (FxCop) al nuovo metodo di analisi del codice gestito tramite l'analisi dell'origine (analizzatori FxCop).
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
ms.openlocfilehash: 9157d47278f835232308dc497965afebb294f8fd
ms.sourcegitcommit: 514f0f7d1a61d292c7dbc80ec73a36bda960d6ce
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937581"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>Eseguire la migrazione dall'analisi legacy (FxCop) all'analisi dell'origine (analizzatori FxCop)

L'analisi dell'origine per .NET Compiler Platform ("Roslyn") analizzatori sostituisce l' [analisi legacy](../code-quality/code-analysis-for-managed-code-overview.md) per il codice gestito. Per i modelli di progetto più recenti, ad esempio i progetti .NET Core e .NET Standard, l'analisi legacy non è disponibile.

Molte delle regole di analisi legacy (FxCop) sono già state riscritte per gli analizzatori FxCop, un set di analizzatori di codice Roslyn. Gli [analizzatori FxCop vengono installati come pacchetto NuGet](install-fxcop-analyzers.md#nuget-package) a cui fa riferimento il progetto o la soluzione. Gli analizzatori FxCop eseguono un'analisi basata sul codice sorgente durante l'esecuzione del compilatore. I risultati degli analizzatori vengono indicati insieme ai risultati del compilatore.

Per ulteriori informazioni sulle differenze tra l'analisi legacy e l'analisi dell'origine, vedere gli argomenti seguenti:

- [Analisi del codice sorgente rispetto all'analisi legacy](../code-quality/roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis)

- [Domande frequenti sugli analizzatori FxCop](../code-quality/fxcop-analyzers-faq.md)

Per eseguire la migrazione all'analisi [dell'origine, installare gli analizzatori FxCop](../code-quality/install-fxcop-analyzers.md). Analogamente alle violazioni delle regole di analisi legacy, le violazioni dell'analisi del codice sorgente vengono visualizzate nella finestra di Elenco errori in Visual Studio. Inoltre, le violazioni dell'analisi del codice sorgente vengono visualizzate nell'editor di codice come *controllo ortografia durante* sotto il codice che causa il danneggiamento. Il colore della linea ondulata dipende dall'[impostazione di gravità](../code-quality/use-roslyn-analyzers.md#rule-severity) della regola. Per visualizzare lo stato delle regole trasferite ai nuovi analizzatori FxCop, vedere [porte e regole non portate](../code-quality/fxcop-rule-port-status.md).

Per ulteriori informazioni sulla configurazione degli analizzatori FxCop:

- Per configurare gli analizzatori FxCop, vedere [configurare gli analizzatori FxCop](../code-quality/configure-fxcop-analyzers.md).

- Per informazioni sulla configurazione degli analizzatori con regole predefinite con EditorConfig o un file del set di regole, vedere [abilitare una categoria di regole](../code-quality/analyzer-rule-sets.md).