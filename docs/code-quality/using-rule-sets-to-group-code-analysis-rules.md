---
title: Set di regole di analisi del codice
ms.date: 04/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8dc70348ef2fe5826339bd58e1db17574449ff6c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53885155"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Usare set di regole per raggruppare regole di analisi codice

Quando si configura l'analisi del codice in Visual Studio, è possibile scegliere da un elenco di incorporati *set di regole*. Un set di regole viene applicato a un progetto e si intende un raggruppamento di codice le regole di analisi che identificano i problemi di destinazione e le condizioni specifiche per il progetto. Ad esempio, è possibile applicare un set di regole che è progettato per analizzare il codice per le API disponibili pubblicamente, o semplicemente di regole minime. È inoltre possibile applicare un set di regole che include tutte le regole.

È possibile personalizzare una set di regole mediante l'aggiunta o eliminazione di regole, o modificando i livelli di gravità regola vengono visualizzati come avvisi o errori nel **elenco errori**. Set di regole personalizzate può soddisfare un'esigenza per l'ambiente di sviluppo specifiche. Quando si personalizza un set di regole, l'editor set di regole fornisce ricerca e gli strumenti per semplificare il processo di filtraggio.

Sono disponibili per i set di regole [analisi statica del codice gestito](how-to-configure-code-analysis-for-a-managed-code-project.md), [analisi del codice C++](using-rule-sets-to-specify-the-cpp-rules-to-run.md), e [analizzatori di Roslyn](analyzer-rule-sets.md).

## <a name="rule-set-format"></a>Formato di set di regole

Viene specificato un set di regole in formato XML in un *ruleSet* file. Le regole, costituiti da un ID e un *azione*, sono raggruppati per ID analizzatore e dello spazio dei nomi nel file.

Il contenuto di un *ruleSet* file avrà un aspetto simile a questo file XML:

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
> È più facile [modifica un set di regole](../code-quality/working-in-the-code-analysis-rule-set-editor.md) nel grafico **Editor Set di regole** rispetto a mano.

## <a name="specify-a-rule-set-for-a-project"></a>Specificare una set di regole per un progetto

La regola impostata per un progetto viene specificato per il **CodeAnalysisRuleSet** proprietà nel file di progetto Visual Studio. Ad esempio:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Vedere anche

- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)