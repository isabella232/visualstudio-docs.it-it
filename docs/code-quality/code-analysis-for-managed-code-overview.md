---
title: Analisi del codice statico per il codice gestito
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 04ae73deb4bc4dfba550df2c663d8f77a4b1efcf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030080"
---
# <a name="overview-of-static-code-analysis-for-managed-code-in-visual-studio"></a>Panoramica dell'analisi codice statico per il codice gestito in Visual Studio

Visual Studio 2017 è possibile eseguire analisi del codice del codice gestito in due modi: con *FxCop* analisi statica di assembly gestiti e con le altre modern *analizzatori di Roslyn*. Questo argomento illustra l'analisi statica del codice di FxCop. Per altre informazioni su analisi del codice tramite gli analizzatori di codice, vedere [analizzatori di panoramica di Roslyn](../code-quality/roslyn-analyzers-overview.md).

L'analisi del codice gestito analizza gli assembly gestiti e fornisce informazioni sugli assembly, ad esempio le violazioni delle regole di programmazione e progettazione definite nelle linee guida di progettazione di Microsoft .NET Framework.

Lo strumento di analisi rappresenta i controlli eseguiti durante un'analisi come messaggi di avviso. I messaggi di avviso identificano eventuali problemi di programmazione e progettazione e, se possibile, forniscono informazioni su come risolverli.

> [!NOTE]
> Analisi statica del codice non sono supportata per i progetti .NET Core e .NET Standard in Visual Studio. Se si esegue l'analisi del codice in un progetto .NET Core o .NET Standard come parte di msbuild, si noterà un errore simile al **errore: CA0055: Impossibile identificare la piattaforma per \<your.dll >**. Per analizzare codice nei progetti .NET Core o .NET Standard, utilizzare [analizzatori di Roslyn](../code-quality/roslyn-analyzers-overview.md) invece.

## <a name="ide-integrated-development-environment-integration"></a>Integrazione nell'IDE (ambiente di sviluppo integrato)

È possibile eseguire l'analisi del codice sul progetto manualmente o automaticamente.

Per eseguire l'analisi del codice ogni volta che si compila un progetto, selezionare **Abilita analisi codice su compilazione** nella pagina delle proprietà del progetto. Per altre informazioni, vedere [Procedura: Abilitare e disabilitare l'analisi automatica del codice](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Per eseguire manualmente l'analisi del codice in un progetto, dalla barra dei menu scegliere **Analyze** > **Esegui analisi del codice** > **Esegui analisi del codice \<progetto >**.

## <a name="rule-sets"></a>Set di regole

Regole di analisi codice per il codice gestito vengono raggruppate in [set di regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). È possibile usare uno dei set di regole standard Microsoft oppure è possibile [creare un set di regole personalizzate](../code-quality/how-to-create-a-custom-rule-set.md) per soddisfare esigenze specifiche.

## <a name="suppress-warnings"></a>Non visualizzare gli avvisi

È in genere utile indicare se un avviso non è applicabile. In questo modo lo sviluppatore e altri individui che potrebbero esaminare il codice in un secondo momento verranno informati del fatto che un avviso è stato sottoposto ad analisi, quindi è stato eliminato o ignorato.

L'eliminazione nell'origine degli avvisi viene implementata attraverso attributi personalizzati. Per non visualizzare un avviso, aggiungere l'attributo `SuppressMessage` al codice sorgente, come illustrato nell'esempio seguente:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Per altre informazioni, vedere [non visualizzare avvisi](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Se si esegue la migrazione di un progetto di Visual Studio 2017, possono incontrare improvvisamente con un numero elevato di avvisi dell'analisi codice. Se non si è pronti per risolvere gli avvisi e vogliono essere produttivi sin da subito, è possibile *baseline* lo stato di analisi del progetto. Dal **Analyze** dal menu **Esegui analisi del codice ed Elimina problemi attivi**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Eseguire l'analisi del codice come parte dei criteri di archiviazione

Le organizzazioni richiedono talvolta che tutte le archiviazioni soddisfino determinati criteri, tra cui, in particolare:

- Nel codice da archiviare non siano presenti errori di compilazione.

- Analisi del codice viene eseguito come parte della build più recente.

A tale scopo, è utile quindi definire dei criteri specifici per l'archiviazione. Per altre informazioni, vedere [miglioramento della qualità del codice con i criteri di controllo progetto](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Integrazione di team build

È possibile utilizzare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi come parte del processo di compilazione. Per altre informazioni, vedere [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori di Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Uso di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Procedura: Abilitare e disabilitare l'analisi automatica del codice](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
