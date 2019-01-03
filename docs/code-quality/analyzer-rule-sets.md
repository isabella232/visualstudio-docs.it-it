---
title: Set di regole dell'analizzatore
ms.date: 07/20/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- analyzers, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 514f264186047c044e5db1b944cd62d517588e80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53885223"
---
# <a name="rule-sets-for-roslyn-analyzers"></a>Set di regole per gli analizzatori di Roslyn

Set di regole predefiniti sono inclusi alcuni pacchetti di Analizzatore NuGet. Ad esempio, i set di regole forniti con il [pacchetto dell'analizzatore NuGet fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) (a partire dalla versione 2.6.2) abilitare o disabilitare le regole in base alla relativa categoria, ad esempio la sicurezza, la denominazione, o prestazioni. Uso dei set di regole semplifica visualizzare rapidamente solo tali violazioni delle regole relative a una determinata categoria della regola.

Se si esegue la migrazione da legacy "FxCop" analisi statica del codice per gli analizzatori di Roslyn, questi set di regole consentono di continuare a usare le stesse configurazioni di regola usato in precedenza.

## <a name="use-analyzer-rule-sets"></a>Usare set di regole dell'analizzatore

Dopo aver [installa un pacchetto dell'analizzatore NuGet](install-roslyn-analyzers.md), individuare il set di regole predefinite relativi *ruleSet* directory, ad esempio *% USERPROFILE %\\.nuget\packages\ Microsoft.codequality.Analyzers\<versione > \rulesets*. Da qui, è possibile trascinare e rilasciare, oppure copiare e incollare, uno o più dei ruleSet al progetto in Visual Studio **Esplora soluzioni**.

Per creare una regola di impostare la regola attiva impostata per l'analisi, pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **proprietà**. Nelle pagine delle proprietà di progetto, selezionare la **analisi del codice** scheda. Sotto **eseguire questo set di regole**, selezionare **Sfoglia**e quindi selezionare il set di regole desiderato che è stato copiato nella directory del progetto. È ora possibile visualizzare solo le violazioni delle regole per tali regole sono attivate nel set di regole selezionato.

È anche possibile [personalizzare un set di regole predefiniti](how-to-create-a-custom-rule-set.md#create-a-custom-rule-set) secondo le proprie preferenze. Ad esempio, è possibile modificare la gravità di una o più regole in modo che le violazioni di vengono visualizzati come errori o avvisi nel **elenco errori**.

## <a name="available-rule-sets"></a>Set di regole disponibili

I set di regole analizzatore predefinito includono tre set di regole che influiscono su tutte le regole nel pacchetto&mdash;uno che consente a tutti, uno che disabilita tutte le e uno che rispetta le impostazioni di gravità e abilitazione predefinito ogni della regola:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Esistono inoltre due set di regole per ogni categoria delle regole nel pacchetto, ad esempio le prestazioni o sicurezza. Un set di regole abilita tutte le regole per la categoria e un set di regole rispetta le impostazioni predefinite di gravità e abilitazione di ogni regola nella categoria.

 Il [pacchetto dell'analizzatore NuGet fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) include set di regole per le categorie seguenti, in modo che corrisponda il set di regole disponibili per l'analisi statica del codice di "FxCop" legacy:

- progettazione
- documentazione
- manutenibilità
- denominazione
- prestazioni
- affidabilità
- sicurity
- utilizzo

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Installare gli analizzatori .NET Compiler Platform](install-roslyn-analyzers.md)
- [Configurare e usare le regole dell'analizzatore Roslyn](use-roslyn-analyzers.md)
- [Usare set di regole per raggruppare regole di analisi codice](using-rule-sets-to-group-code-analysis-rules.md)