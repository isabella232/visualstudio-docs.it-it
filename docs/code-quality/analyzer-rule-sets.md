---
title: Set di regole dell'analizzatore
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c0be66559802188503c3b8f8c1c2cf2955dbd8a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547946"
---
# <a name="rule-sets-for-analyzer-packages"></a>Set di regole per pacchetti dell'analizzatore

I set di regole predefiniti sono inclusi con alcuni pacchetti dell'analizzatore NuGet. Ad esempio, i set di regole inclusi nel pacchetto [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet Analyzer (a partire dalla versione 2.6.2) abilitano o disabilitano le regole in base alla categoria, ad esempio sicurezza, denominazione o prestazioni. L'uso di set di regole consente di visualizzare rapidamente solo le violazioni delle regole relative a una particolare categoria di regole.

Se si esegue la migrazione da un'analisi "FxCop" legacy a un'analisi del codice basata su .NET Compiler Platform, questi set di regole consentono di continuare a usare le stesse configurazioni delle regole usate in precedenza.

## <a name="use-analyzer-package-rule-sets"></a>Usare set di regole del pacchetto dell'analizzatore

Dopo aver [installato un pacchetto di analizzatore NuGet](install-roslyn-analyzers.md), individuare il set di regole predefinito nella relativa directory RuleSets. Ad esempio, se si fa riferimento al `Microsoft.CodeAnalysis.FxCopAnalyzers` pacchetto dell'analizzatore, è possibile trovare la directory *RuleSets* in *% USERPROFILE\\%.\\\<nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers Version \rulesets\>* . Da qui, copiare uno o più RuleSet e incollarli nella directory che contiene il progetto di Visual Studio o direttamente in **Esplora soluzioni**.

È anche possibile [personalizzare un set di regole predefinito](how-to-create-a-custom-rule-set.md) per le proprie preferenze. Ad esempio, è possibile modificare la gravità di una o più regole in modo che le violazioni vengano visualizzate come errori o avvisi nell' **Elenco errori**.

## <a name="set-the-active-rule-set"></a>Imposta il set di regole attive

Il processo di impostazione del set di regole attivo è leggermente diverso a seconda che si disponga di un progetto .NET Core/.NET standard o di un progetto .NET Framework.

### <a name="net-core"></a>.NET Core

Per impostare una regola come set di regole attivo per l'analisi nei progetti .NET Core o .NET Standard, aggiungere manualmente la proprietà **CodeAnalysisRuleSet** al file di progetto. Il frammento di codice seguente, ad `HelloWorld.ruleset` esempio, imposta come set di regole attive.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Per impostare una regola per impostare il set di regole attive per l'analisi nei progetti .NET Framework, fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Proprietà**. Nelle pagine delle proprietà del progetto selezionare la scheda **analisi codice** . In **Esegui questo set di regole**selezionare **Sfoglia**, quindi selezionare il set di regole desiderato copiato nella directory del progetto. A questo punto, vengono visualizzate solo le violazioni delle regole per le regole abilitate nel set di regole selezionato.

## <a name="available-rule-sets"></a>Set di regole disponibili

I set di regole dell'analizzatore predefiniti includono tre set di regole che interessano tutte&mdash;le regole del pacchetto che li abilitano tutti, uno che li Disabilita e uno che rispetta le impostazioni di gravità e abilitazione predefinite di ogni regola:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Sono inoltre disponibili due set di regole per ogni categoria di regole nel pacchetto, ad esempio prestazioni o sicurezza. Un set di regole Abilita tutte le regole per la categoria e un set di regole rispetta la gravità predefinita e le impostazioni di abilitazione per ogni regola nella categoria.

Il pacchetto [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet Analyzer include set di regole per le categorie seguenti, che corrispondono ai set di regole disponibili per l'analisi legacy:

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
- [Usare gli analizzatori](use-roslyn-analyzers.md)
- [Usare set di regole per raggruppare le regole di analisi del codice](using-rule-sets-to-group-code-analysis-rules.md)
