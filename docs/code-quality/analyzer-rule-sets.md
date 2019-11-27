---
title: Set di regole e file EditorConfig di FxCop Analyzer
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2cf385aaf24db2172a61ddbe7ecf77dcbe40f3c
ms.sourcegitcommit: 08105865a9643fb20dce9b8b7580452cfbbe7ee7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74537777"
---
# <a name="enable-a-category-of-rules"></a>Abilitare una categoria di regole

I pacchetti dell'analizzatore possono includere file di [set](using-rule-sets-to-group-code-analysis-rules.md) di regole e [EditorConfig](use-roslyn-analyzers.md#rule-severity) predefiniti che consentono di abilitare in modo semplice e rapido una categoria di regole, ad esempio regole di sicurezza o di progettazione. Il pacchetto [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet Analyzer include entrambi i set di regole (a partire dalla versione 2.6.2) e i file EditorConfig (a partire dalla versione 2.9.5). Abilitando una categoria specifica di regole, è possibile identificare i problemi di destinazione e le condizioni specifiche.

> [!NOTE]
> L'abilitazione delle regole dell'analizzatore e l'impostazione della loro gravità usando un file EditorConfig sono supportate a partire da Visual Studio 2019 versione 16,3.

Il pacchetto NuGet dell'analizzatore FxCop include set di regole e file EditorConfig predefiniti per le categorie di regole seguenti:

- Tutte le regole
- Flusso di dati
- Progettazione
- Documentazione
- Globalizzazione
- Interoperabilità
- Manutenibilità
- Denominazione
- Prestazioni
- Portata da FxCop
- Affidabilità
- Sicurezza
- Utilizzo

Ognuna di queste categorie di regole ha un file EditorConfig o set di regole per:

- abilitare tutte le regole nella categoria (e disabilitare tutte le altre regole)
- Usa l'impostazione di abilitazione e gravità predefinite di ogni regola (e Disabilita tutte le altre regole)

> [!TIP]
> La categoria "tutte le regole" include un file EditorConfig o set di regole aggiuntivo per disabilitare tutte le regole. Utilizzare questo file per eliminare rapidamente eventuali avvisi o errori dell'analizzatore in un progetto.

> [!TIP]
> Se si esegue la migrazione da un'analisi "FxCop" legacy a un'analisi del codice basata su .NET Compiler Platform, i file EditorConfig e set di regole consentono di continuare a usare configurazioni di regole simili a [quelle usate in precedenza](rule-set-reference.md).

## <a name="predefined-editorconfig-files"></a>File EditorConfig predefiniti

I file EditorConfig predefiniti per il pacchetto Microsoft. CodeAnalysis. FxCopAnalyzers Analyzer si trovano nella directory *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<versione\>\editorconfig* . Ad esempio, il file EditorConfig per abilitare tutte le regole di sicurezza si trova in *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<versione\>\editorconfig\SecurityRulesEnabled\\. EditorConfig*.

Copiare il file con estensione EditorConfig scelto nella directory radice del progetto.

## <a name="predefined-rule-sets"></a>Set di regole predefiniti

I file del set di regole predefiniti per il pacchetto Microsoft. CodeAnalysis. FxCopAnalyzers Analyzer si trovano nella directory *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<versione\>\rulesets* . Ad esempio, il file del set di regole per abilitare tutte le regole di sicurezza si trova in *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<versione\>\rulesets\SecurityRulesEnabled.RuleSet*.

Copiare uno o più set di regole e incollarli nella directory che contiene il progetto di Visual Studio o direttamente in **Esplora soluzioni**.

È anche possibile [personalizzare un set di regole predefinito](how-to-create-a-custom-rule-set.md) per le proprie preferenze. Ad esempio, è possibile modificare la gravità di una o più regole in modo che le violazioni vengano visualizzate come errori o avvisi nell' **Elenco errori**.

### <a name="set-the-active-rule-set"></a>Imposta il set di regole attive

Il processo di impostazione del set di regole attivo è leggermente diverso a seconda che si disponga di un progetto .NET Core/.NET standard o di un progetto .NET Framework.

#### <a name="net-core"></a>.NET Core

Per impostare una regola come set di regole attivo per l'analisi nei progetti .NET Core o .NET Standard, aggiungere manualmente la proprietà **CodeAnalysisRuleSet** al file di progetto. Il frammento di codice seguente, ad esempio, imposta `HelloWorld.ruleset` come set di regole attive.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

#### <a name="net-framework"></a>.NET Framework

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

## <a name="see-also"></a>Vedere anche

- [Domande frequenti sugli analizzatori](analyzers-faq.md)
- [Panoramica degli analizzatori .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Installare gli analizzatori](install-roslyn-analyzers.md)
- [Configurare gli analizzatori](use-roslyn-analyzers.md)
- [Usare set di regole per raggruppare le regole di analisi del codice](using-rule-sets-to-group-code-analysis-rules.md)
