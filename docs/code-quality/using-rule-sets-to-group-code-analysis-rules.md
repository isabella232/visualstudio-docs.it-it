---
title: Set di regole di analisi del codice
ms.date: 07/23/2021
description: Informazioni sui set di regole predefiniti e personalizzati nell'analisi Visual Studio codice. Informazioni su come specificare i set di regole nei file e su come configurare i set di regole nei progetti.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 856fd236959b8335ded1ff2007bc5a5d1dd29a90
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631805"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Usare i set di regole per raggruppare le regole di analisi del codice

Quando si configura l'analisi del codice Visual Studio, è possibile scegliere da un elenco di set di regole *predefiniti.* Un set di regole è un raggruppamento di regole di analisi del codice che identificano i problemi di destinazione e le condizioni specifiche per il progetto. Ad esempio, è possibile applicare un set di regole progettato per analizzare il codice per le API disponibili pubblicamente. È anche possibile applicare un set di regole che include tutte le regole disponibili.

È possibile personalizzare un set di regole aggiungendo o eliminando regole o modificando i livelli di gravità delle regole in modo che vengano visualizzati come avvisi o errori in **Elenco errori**. I set di regole personalizzati possono soddisfare le esigenze dell'ambiente di sviluppo specifico. Quando si personalizza un set di regole, l'editor del set di regole fornisce strumenti di ricerca e filtro per facilitare il processo.

I set di regole sono disponibili [per l'analisi del codice gestito,](/dotnet/fundamentals/code-analysis/code-quality-rule-options) [l'analisi legacy del codice gestito](how-to-configure-code-analysis-for-a-managed-code-project.md)e [l'analisi del codice C++.](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run)

>[!NOTE]
> A partire Visual Studio 2019 versione 16.3, è possibile usare i file EditorConfig per configurare le regole per l'analisi del codice sorgente .NET, ma non l'analisi legacy. Per altre informazioni, vedere la [sezione EditorConfig rispetto ai set di](../code-quality/analyzers-faq.yml) regole nelle domande frequenti.

## <a name="rule-set-format"></a>Formato del set di regole

Un set di regole viene specificato in formato XML in un file *con estensione ruleset.* Le regole, costituite da un ID e *un'azione*, vengono raggruppate in base all'ID analizzatore e allo spazio dei nomi nel file.

Il contenuto di un file *con estensione ruleset* è simile al seguente XML:

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
> È più semplice modificare [un set di regole](../code-quality/working-in-the-code-analysis-rule-set-editor.md) nell'editor grafico dei set **di** regole anziché manualmente.

## <a name="specify-a-rule-set-for-a-project"></a>Specificare un set di regole per un progetto

Il set di regole per un progetto viene specificato dalla **proprietà CodeAnalysisRuleSet** nel file Visual Studio progetto. Ad esempio:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Vedere anche

- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)