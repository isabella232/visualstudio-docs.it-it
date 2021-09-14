---
title: Analisi legacy per il codice gestito
ms.date: 06/12/2019
description: Informazioni sull'analisi legacy in Visual Studio. Informazioni su come eliminare gli avvisi e su come eseguire le analisi manualmente, automaticamente e durante le archiviazioni e le compilazioni.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 6ec5d5a5bc491ef820631af942db8ad5c320fa22
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631818"
---
# <a name="overview-of-legacy-analysis-for-managed-code-in-visual-studio"></a>Panoramica dell'analisi legacy per il codice gestito in Visual Studio

Visual Studio possibile eseguire l'analisi del codice gestito in due modi: con l'analisi [legacy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), nota anche come analisi statica FxCop degli assembly gestiti, e con i più moderni analizzatori di codice basati su .NET Compiler Platform [.](../code-quality/roslyn-analyzers-overview.md) In questo argomento viene illustrata l'analisi legacy. Per altre informazioni sull'.NET Compiler Platform di codice basata .NET Compiler Platform, vedere Panoramica degli analizzatori [basati su .NET Compiler Platform.](../code-quality/roslyn-analyzers-overview.md)

L'analisi del codice gestito analizza gli assembly gestiti e segnala informazioni sugli assembly, ad esempio le violazioni delle regole di programmazione e progettazione impostate nelle Linee guida per la progettazione [di .NET.](/dotnet/standard/design-guidelines/)

Lo strumento di analisi rappresenta i controlli eseguiti durante un'analisi come messaggi di avviso. I messaggi di avviso identificano eventuali problemi di programmazione e progettazione e, se possibile, forniscono informazioni su come risolverli.

> [!NOTE]
> L'analisi legacy (analisi statica del codice) non è supportata per i progetti .NET Core e .NET Standard in Visual Studio. Se si esegue l'analisi del codice in un progetto .NET Core o .NET Standard come parte di msbuild, verrà visualizzato un errore simile all'errore **: CA0055 : Could not identify platform for \<your.dll>**. Per analizzare il codice in .NET Core o .NET Standard progetti, usare [invece gli analizzatori di](../code-quality/roslyn-analyzers-overview.md) codice.

## <a name="ide-integrated-development-environment-integration"></a>Integrazione ide (ambiente di sviluppo integrato)

È possibile eseguire l'analisi del codice sul progetto manualmente o automaticamente.

Per eseguire l'analisi del codice ogni volta che si compila un progetto, selezionare l'opzione nella pagina delle **Code Analysis** del progetto. Per altre informazioni, vedere [Procedura: Abilitare e disabilitare l'accesso Code Analysis](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Per eseguire manualmente l'analisi del codice in un progetto, dalla barra dei menu scegliere Analizza esegui Code Analysis  >    >  **esegui Code Analysis in \<project>**.

## <a name="rule-sets"></a>Set di regole

Le regole per l'analisi del codice gestito vengono raggruppate in [set di regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). È possibile usare uno dei set di regole standard Microsoft oppure creare [un set di](../code-quality/how-to-create-a-custom-rule-set.md) regole personalizzato per soddisfare esigenze specifiche.

## <a name="suppress-warnings"></a>Non visualizzare gli avvisi

È in genere utile indicare se un avviso non è applicabile. In questo modo lo sviluppatore e altri individui che potrebbero esaminare il codice in un secondo momento verranno informati del fatto che un avviso è stato sottoposto ad analisi, quindi è stato eliminato o ignorato.

L'eliminazione degli avvisi nel codice sorgente viene implementata tramite attributi personalizzati. Per non visualizzare un avviso, aggiungere l'attributo `SuppressMessage` al codice sorgente, come illustrato nell'esempio seguente:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Per altre informazioni, vedere Non [visualizzare avvisi.](../code-quality/in-source-suppression-overview.md)

::: moniker range="vs-2017"

> [!NOTE]
> Se si esegue la migrazione di un progetto Visual Studio 2017, si potrebbero improvvisamente verificare numerosi avvisi di analisi del codice. Se non si è pronti per correggere gli avvisi, è possibile sopprimerli tutti scegliendo Analizza e Code Analysis  >  **elimina problemi attivi.**
>
> ![Eseguire l'analisi del codice ed eliminare i problemi Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Se si esegue la migrazione di un progetto Visual Studio 2019, si potrebbero improvvisamente verificare numerosi avvisi di analisi del codice. Se non si è pronti per correggere gli avvisi, è possibile sopprimerli tutti scegliendo **Analizza** compilazione  >  **ed Elimina problemi attivi.**

::: moniker-end

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Eseguire l'analisi del codice come parte dei criteri di archiviazione

Le organizzazioni richiedono talvolta che tutte le archiviazioni soddisfino determinati criteri, tra cui, in particolare:

- Non sono presenti errori di compilazione nel codice archiviato.

- L'analisi del codice viene eseguita come parte della compilazione più recente.

A tale scopo, è utile quindi definire dei criteri specifici per l'archiviazione. Per altre informazioni, vedere [Miglioramento della qualità del codice con Project criteri di archiviazione.](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Integrazione di Team Build

È possibile utilizzare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi come parte del processo di compilazione. Per altre informazioni, vedere [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

## <a name="see-also"></a>Vedi anche

- [Panoramica degli .NET Compiler Platform basati su test](../code-quality/roslyn-analyzers-overview.md)
- [Uso di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Procedura: Abilitare e disabilitare l'analisi codice automatica](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
