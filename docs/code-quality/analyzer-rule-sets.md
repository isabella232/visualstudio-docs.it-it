---
title: Set di regole dell'analizzatore FxCop
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 313b578743fd734da3354989a8cee16022779242
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974702"
---
# <a name="rule-sets-for-analyzer-packages"></a>Set di regole per pacchetti dell'analizzatore

I set di regole predefiniti sono inclusi con alcuni pacchetti dell'analizzatore NuGet. Ad esempio, i set di regole inclusi nel pacchetto [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet Analyzer (a partire dalla versione 2.6.2) abilitano o disabilitano le regole in base alla categoria, ad esempio sicurezza, denominazione o prestazioni. L'uso di set di regole consente di visualizzare rapidamente solo le violazioni delle regole relative a una particolare categoria di regole.

Un set di regole è un raggruppamento di regole di analisi del codice che identificano i problemi di destinazione e le condizioni specifiche. I set di regole consentono di abilitare o disabilitare le regole e impostare la gravità per le singole violazioni delle regole. Il pacchetto NuGet dell'analizzatore FxCop include set di regole predefiniti per le categorie di regole seguenti:

- progettazione
- documentazione
- manutenibilità
- denominazione
- prestazioni
- affidabilità
- sicurity
- utilizzo

Se si esegue la migrazione da un'analisi "FxCop" legacy a un'analisi del codice basata su .NET Compiler Platform, questi set di regole consentono di continuare a usare configurazioni di regole simili a [quelle usate in precedenza](rule-set-reference.md).

## <a name="use-analyzer-package-rule-sets"></a>Usare set di regole del pacchetto dell'analizzatore

Dopo aver [installato un pacchetto di analizzatore NuGet](install-roslyn-analyzers.md), individuare il set di regole predefinito nella relativa directory *RuleSets* . Se, ad esempio, si fa riferimento al pacchetto di `Microsoft.CodeAnalysis.FxCopAnalyzers` Analyzer, è possibile trovare la directory *RuleSets* in *% USERPROFILE% \\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers @ no__t-4 @ no__t-5version @ no__t-6\rulesets*. Da qui, copiare uno o più RuleSet e incollarli nella directory che contiene il progetto di Visual Studio o direttamente in **Esplora soluzioni**.

È anche possibile [personalizzare un set di regole predefinito](how-to-create-a-custom-rule-set.md) per le proprie preferenze. Ad esempio, è possibile modificare la gravità di una o più regole in modo che le violazioni vengano visualizzate come errori o avvisi nell' **Elenco errori**.

## <a name="set-the-active-rule-set"></a>Imposta il set di regole attive

Il processo di impostazione del set di regole attivo è leggermente diverso a seconda che si disponga di un progetto .NET Core/.NET standard o di un progetto .NET Framework.

### <a name="net-core"></a>.NET Core

Per impostare una regola come set di regole attivo per l'analisi nei progetti .NET Core o .NET Standard, aggiungere manualmente la proprietà **CodeAnalysisRuleSet** al file di progetto. Il frammento di codice seguente, ad esempio, imposta `HelloWorld.ruleset` come set di regole attive.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Per impostare una regola come set di regole attivo per l'analisi nei progetti .NET Framework:

- Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Proprietà**.

- Nelle pagine delle proprietà del progetto selezionare la scheda **analisi codice** .

::: moniker range="vs-2017"

- In **Esegui questo set di regole**selezionare **Sfoglia**, quindi selezionare il set di regole desiderato copiato nella directory del progetto.

::: moniker-end

::: moniker range=">=vs-2019"

- In **regole attive**selezionare **Sfoglia**, quindi selezionare il set di regole desiderato copiato nella directory del progetto.

::: moniker-end

   A questo punto, vengono visualizzate solo le violazioni delle regole per le regole abilitate nel set di regole selezionato.

## <a name="available-rule-sets"></a>Set di regole disponibili

I set di regole dell'analizzatore predefiniti includono tre RuleSet che interessano tutte le regole del pacchetto @ no__t-0one che le abilitano tutti, una che li Disabilita tutti e uno che rispetta le impostazioni di gravità e abilitazione predefinite di ogni regola:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Sono inoltre disponibili due set di regole per ogni categoria di regole nel pacchetto, ad esempio prestazioni o sicurezza. Un set di regole Abilita tutte le regole per la categoria e un set di regole rispetta la gravità predefinita e le impostazioni di abilitazione per ogni regola nella categoria.

Il pacchetto [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet Analyzer include set di regole per le categorie seguenti:

- progettazione
- documentazione
- manutenibilità
- denominazione
- prestazioni
- affidabilità
- sicurity
- utilizzo

## <a name="see-also"></a>Vedere anche

- [Domande frequenti sugli analizzatori](analyzers-faq.md)
- [Panoramica degli analizzatori .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Installare gli analizzatori](install-roslyn-analyzers.md)
- [Configurare gli analizzatori](use-roslyn-analyzers.md)
- [Usare set di regole per raggruppare le regole di analisi del codice](using-rule-sets-to-group-code-analysis-rules.md)
