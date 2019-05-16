---
title: Set di regole dell'analizzatore
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 696e6bd46c17054494be2ea0e0f2a1af4fd703d7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675479"
---
# <a name="rule-sets-for-roslyn-analyzers"></a>Set di regole per gli analizzatori di Roslyn

Set di regole predefiniti sono inclusi alcuni pacchetti di Analizzatore NuGet. Ad esempio, i set di regole forniti con il [fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) pacchetto dell'analizzatore NuGet (a partire dalla versione 2.6.2) abilitare o disabilitare le regole in base alla relativa categoria, ad esempio la sicurezza, la denominazione, o Prestazione. Uso dei set di regole semplifica visualizzare rapidamente solo tali violazioni delle regole relative a una determinata categoria della regola.

Se si esegue la migrazione da legacy "FxCop" analisi statica del codice per gli analizzatori di Roslyn, questi set di regole consentono di continuare a usare le stesse configurazioni di regola usato in precedenza.

## <a name="use-analyzer-rule-sets"></a>Usare set di regole dell'analizzatore

Dopo aver [installa un pacchetto dell'analizzatore NuGet](install-roslyn-analyzers.md), individuare il set di regole predefinite relativi *ruleSet* directory. Ad esempio, se si fa riferimento il `Microsoft.CodeAnalysis.FxCopAnalyzers` pacchetto di analizzatori, sarà possibile trovare relativi *ruleSet* directory alla *% USERPROFILE %\\.nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\ \<versione\>\rulesets*. Da qui, copiare uno o più dei ruleSet e incollarli nella directory contenente il progetto di Visual Studio o direttamente in **Esplora soluzioni**.

È anche possibile [personalizzare un set di regole predefiniti](how-to-create-a-custom-rule-set.md) secondo le proprie preferenze. Ad esempio, è possibile modificare la gravità di una o più regole in modo che le violazioni di vengono visualizzati come errori o avvisi nel **elenco errori**.

## <a name="set-the-active-rule-set"></a>Impostare il set di regole attivo

Il processo per l'impostazione di set di regole attivo è leggermente diverso a seconda che si disponga di un progetto .NET Core/.NET Standard o un progetto .NET Framework.

### <a name="net-core"></a>.NET Core

Per creare una regola di impostare la regola attiva impostata per l'analisi nei progetti .NET Core o .NET Standard, aggiungere manualmente il **CodeAnalysisRuleSet** proprietà al file di progetto. Ad esempio, il codice seguente frammento di codice imposta `HelloWorld.ruleset` come la regola attiva impostata.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Per creare una regola di impostare la regola attiva impostata per l'analisi nei progetti .NET Framework, pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **proprietà**. Nelle pagine delle proprietà di progetto, selezionare la **analisi del codice** scheda. Sotto **eseguire questo set di regole**, selezionare **Sfoglia**e quindi selezionare il set di regole desiderato che è stato copiato nella directory del progetto. È ora possibile visualizzare solo le violazioni delle regole per tali regole sono attivate nel set di regole selezionato.

## <a name="available-rule-sets"></a>Set di regole disponibili

I set di regole analizzatore predefinito includono tre set di regole che influiscono su tutte le regole nel pacchetto&mdash;uno che consente a tutti, uno che disabilita tutte le e uno che rispetta le impostazioni di gravità e abilitazione predefinito ogni della regola:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Esistono inoltre due set di regole per ogni categoria delle regole nel pacchetto, ad esempio le prestazioni o sicurezza. Un set di regole abilita tutte le regole per la categoria e un set di regole rispetta le impostazioni predefinite di gravità e abilitazione di ogni regola nella categoria.

Il [fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) pacchetto dell'analizzatore NuGet include set di regole per le categorie seguenti, che corrispondono ai set di regole disponibili per l'analisi statica del codice legacy "FxCop":

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
- [Usare set di regole per raggruppare regole di analisi codice](using-rule-sets-to-group-code-analysis-rules.md)
