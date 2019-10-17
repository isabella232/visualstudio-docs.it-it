---
title: Set di regole di analisi del codice
ms.date: 04/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f206ceb088683be4e0f66b27d8b4e9960a3543a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448764"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Usare set di regole per raggruppare le regole di analisi del codice

Quando si configura l'analisi del codice in Visual Studio, è possibile scegliere da un elenco di *set di regole*predefiniti. Un set di regole è un raggruppamento di regole di analisi del codice che identificano i problemi di destinazione e le condizioni specifiche per il progetto. Ad esempio, è possibile applicare un set di regole progettato per analizzare il codice per le API disponibili pubblicamente. È anche possibile applicare un set di regole che includa tutte le regole disponibili.

È possibile personalizzare un set di regole aggiungendo o eliminando regole o modificando i livelli di gravità delle regole in modo che vengano visualizzati come avvisi o errori nel **Elenco errori**. I set di regole personalizzati possono soddisfare la necessità di un ambiente di sviluppo specifico. Quando si personalizza un set di regole, l'editor dei set di regole fornisce strumenti di ricerca e filtro che consentono di semplificare il processo.

I set di regole sono disponibili per l' [analisi del codice gestito](analyzer-rule-sets.md), l' [analisi legacy del codice gestito](how-to-configure-code-analysis-for-a-managed-code-project.md)e [ C++ l'analisi del codice](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

## <a name="rule-set-format"></a>Formato set di regole

Un set di regole viene specificato in formato XML in un file con *estensione ruleset* . Le regole, che sono costituite da un ID e da un' *azione*, sono raggruppate in base all'ID analizzatore e allo spazio dei nomi nel file.

Il contenuto di un file con *estensione ruleset* è simile al codice XML seguente:

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> È più semplice [modificare un set di regole](../code-quality/working-in-the-code-analysis-rule-set-editor.md) nell'editor del **set di regole** grafico anziché manualmente.

## <a name="specify-a-rule-set-for-a-project"></a>Specificare un set di regole per un progetto

Il set di regole per un progetto viene specificato dalla proprietà **CodeAnalysisRuleSet** nel file di progetto di Visual Studio. Esempio:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Vedere anche

- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)
