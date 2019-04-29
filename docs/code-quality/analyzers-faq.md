---
title: EditorConfig confronto degli analizzatori
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bec9296f15c48cf3b327c78cd0ce7d57adafa002
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62571472"
---
# <a name="analyzers-faq"></a>Domande frequenti sugli analizzatori

Questa pagina contiene le risposte ad alcune domande frequenti sugli analizzatori di Roslyn in Visual Studio.

## <a name="roslyn-analyzers-versus-editorconfig"></a>Analizzatori di Roslyn e con estensione editorconfig

**Q**: È consigliabile usare gli analizzatori di Roslyn o con estensione editorconfig per lo stile codice?

**R**: Gli analizzatori di Roslyn e i file con estensione editorconfig funzionano in stretta associazione. Quando si definiscono gli stili di codice [in un file con estensione editorconfig](../ide/editorconfig-code-style-settings-reference.md) o scegliere il [editor di testo opzioni](../ide/code-styles-and-quick-actions.md) pagina, in realtà si sta configurando gli analizzatori di Roslyn integrate in Visual Studio. I file EditorConfig sono anche utilizzabile per configurare alcuni pacchetti di terze parti analyzer, ad esempio [analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig rispetto a set di regole

**Q**: È necessario configurare my gli analizzatori che usano un set di regole o un file con estensione editorconfig?

**R**: Set di regole e i file con estensione editorconfig si escludono a vicenda modi per configurare gli analizzatori. Essi possono coesistere. [Set di regole](analyzer-rule-sets.md) consentono di abilitare e disabilitare le regole e impostare il livello di gravità. I file EditorConfig offrono altri modi per configurare le regole. Per gli analizzatori FxCop, file con estensione editorconfig consentono [definire i tipi di codice per analizzare](fxcop-analyzer-options.md). Per gli analizzatori integrate in Visual Studio, i file con estensione editorconfig consentono [definire gli stili di codice preferito](../ide/editorconfig-code-style-settings-reference.md) per una codebase.

Oltre ai set di regole e i file con estensione editorconfig, alcuni analizzatori di terze parti sono configurati tramite l'uso di file di testo contrassegnati come [file aggiuntivi](../ide/build-actions.md#build-action-values) per il C# e i compilatori di Visual Basic.

> [!NOTE]
> I file EditorConfig non sono utilizzabile per configurare le regole di analisi statica del codice, mentre per i set di regole.

## <a name="analyzers-in-ci-builds"></a>Analizzatori nelle compilazioni di integrazione continua

**Q**: Gli analizzatori funzionano nelle compilazioni di integrazione continua (CI)?

**R**: Sì. Per gli analizzatori che vengono installati da un pacchetto NuGet, tali regole sono [applicati in fase di compilazione](roslyn-analyzers-overview.md#build-errors), tra cui durante una compilazione CI. Gli analizzatori utilizzati nella configurazione di regola riguardo le compilazioni CI sia da [set di regole](analyzer-rule-sets.md) e [file con estensione editorconfig](configure-fxcop-analyzers.md). Attualmente, gli analizzatori di codice che sono integrati in Visual Studio non sono disponibili come pacchetto NuGet, e quindi queste regole non sono applicabili in una compilazione CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analizzatori IDE e StyleCop

**Q**: Che cos'è la differenza tra gli analizzatori di codice IDE di Visual Studio e gli analizzatori StyleCop?

**R**: IDE di Visual Studio include analizzatori predefiniti che per individuare i problemi di stile e la qualità sia codice. Queste regole consentono di usare nuove funzionalità del linguaggio che è stato introdotto e migliorare la gestibilità del codice. Gli analizzatori IDE vengono aggiornati continuamente con ogni versione di Visual Studio.

[Gli analizzatori StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) sono gli analizzatori di terze parti installati come pacchetto NuGet che verifica la coerenza di stile nel codice. In generale, le regole StyleCop consentono di impostare le preferenze personali per un codice di base senza consigliare uno stile rispetto a un altro.

## <a name="analyzers-versus-static-code-analysis"></a>Analizzatori e analisi statica del codice

**Q**: Che cos'è la differenza tra gli analizzatori e analisi statica del codice?

**R**: Gli analizzatori di analizzano il codice sorgente in tempo reale e durante la compilazione, mentre l'analisi statica del codice consente di analizzare i file binari dopo la compilazione è stata completata. Per altre informazioni, vedere [analizzatori di Roslyn e analisi statica del codice](roslyn-analyzers-overview.md#roslyn-analyzers-vs-static-code-analysis) e [analizzatori FxCop domande frequenti su](fxcop-analyzers-faq.md).

## <a name="see-also"></a>Vedere anche

- [Panoramica di analizzatori](roslyn-analyzers-overview.md)
- [Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig](../ide/editorconfig-code-style-settings-reference.md)