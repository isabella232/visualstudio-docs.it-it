---
title: EditorConfig rispetto agli analizzatori
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26e48664c40db018df60f2b6d600fab0767a7b72
ms.sourcegitcommit: 2db01751deeee7b2bdb1db25419ea6706e6fcdf8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71062173"
---
# <a name="code-analysis-faq"></a>Domande frequenti sull'analisi del codice

Questa pagina contiene le risposte ad alcune domande frequenti sull'analisi del codice basata su .NET Compiler Platform in Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analisi codice rispetto a EditorConfig

**D**: È consigliabile usare l'analisi del codice o EditorConfig per controllare lo stile del codice?

**R**: L'analisi del codice e i file EditorConfig funzionano in mano. Quando si definiscono gli stili [di codice in un file EditorConfig](../ide/editorconfig-code-style-settings-reference.md) o nella pagina [Opzioni editor di testo](../ide/code-styles-and-code-cleanup.md) , si configurano effettivamente gli analizzatori di codice incorporati in Visual Studio. I file EditorConfig possono essere usati anche per configurare alcuni pacchetti di NuGet Analyzer, ad esempio gli [analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig rispetto ai set di regole

**D**: È necessario configurare gli analizzatori utilizzando un set di regole o un file EditorConfig?

**R**: I set di regole e i file EditorConfig possono coesistere e possono essere usati entrambi per configurare gli analizzatori. I [set](analyzer-rule-sets.md) di regole consentono di abilitare e disabilitare le regole e di impostarne la gravità. I file EditorConfig offrono altri modi per configurare le regole. Per gli analizzatori FxCop, i file EditorConfig consentono [di definire i tipi di codice da analizzare](fxcop-analyzer-options.md). Per gli analizzatori di tipo codice incorporati in Visual Studio, i file EditorConfig consentono di [definire gli stili di codice preferiti](../ide/editorconfig-code-style-settings-reference.md) per una codebase.

Oltre ai set di regole e ai file EditorConfig, alcuni analizzatori sono configurati tramite l'uso di file di testo contrassegnati come C# [file aggiuntivi](../ide/build-actions.md#build-action-values) per i compilatori e VB.

> [!NOTE]
> Non è possibile usare i file EditorConfig per configurare l'analisi legacy, mentre i set di regole possono.

## <a name="code-analysis-in-ci-builds"></a>Analisi del codice nelle compilazioni CI

**D**: L'analisi del codice basata su .NET Compiler Platform funziona in compilazioni di integrazione continua (CI)?

**R**: Sì. Per gli analizzatori installati da un pacchetto NuGet, tali regole vengono [applicate in fase di compilazione](roslyn-analyzers-overview.md#build-errors), incluso durante una compilazione ci. Gli analizzatori usati nelle compilazioni CI rispettano la configurazione della regola da entrambi i [set di regole](analyzer-rule-sets.md) e [file EditorConfig](configure-fxcop-analyzers.md). Attualmente, gli analizzatori di codice incorporati in Visual Studio non sono disponibili come pacchetto NuGet, quindi queste regole non sono applicabili in una compilazione CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analizzatori IDE rispetto a StyleCop

**D**: Qual è la differenza tra gli analizzatori di codice IDE di Visual Studio e gli analizzatori StyleCop?

**R**: L'IDE di Visual Studio include analizzatori incorporati che cercano sia lo stile del codice che i problemi di qualità. Queste regole consentono di usare le nuove funzionalità del linguaggio Man mano che sono state introdotte e di migliorare la gestibilità del codice. Gli analizzatori IDE vengono continuamente aggiornati con ogni versione di Visual Studio.

Gli [analizzatori StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) sono analizzatori di terze parti installati come pacchetto NuGet che verificano la coerenza dello stile nel codice. In generale, le regole StyleCop consentono di impostare le preferenze personali per una codebase senza suggerire uno stile rispetto a un altro.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizzatori del codice rispetto all'analisi legacy

**D**: Qual è la differenza tra analisi legacy e analisi del codice basata su .NET Compiler Platform?

**R: l'** analisi del codice basata su .NET Compiler Platform analizza il codice sorgente in tempo reale e durante la compilazione, mentre analisi legacy analizza i file binari al termine della compilazione. Per altre informazioni, vedere Domande frequenti [su analisi basata su .NET Compiler Platform e analisi legacy](roslyn-analyzers-overview.md#net-compiler-platform-based-analysis-versus-legacy-analysis) e [analizzatori FxCop](fxcop-analyzers-faq.md).

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori](roslyn-analyzers-overview.md)
- [Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
