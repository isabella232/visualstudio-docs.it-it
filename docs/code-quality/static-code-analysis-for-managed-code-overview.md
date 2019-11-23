---
title: Analisi codice per il codice gestito
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4eac88d56399b7f8552962afa50b52c8431232b9
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974931"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Panoramica dell'analisi codice per il codice gestito in Visual Studio

Visual Studio è in grado di eseguire l'analisi codice del codice gestito in due modi: con l' [analisi legacy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), nota anche come analisi statica FxCop degli assembly gestiti e con gli [analizzatori di codice](../code-quality/roslyn-analyzers-overview.md)più moderni basati su .NET Compiler Platform. In questo argomento viene illustrata l'analisi legacy. Per altre informazioni sull'analisi del codice basata su .NET Compiler Platform, vedere [Cenni preliminari sugli analizzatori basati su .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md).

L'analisi del codice per il codice gestito analizza gli assembly gestiti e fornisce informazioni sugli assembly, ad esempio le violazioni delle regole di programmazione e progettazione definite nelle [linee guida di progettazione di .NET](/dotnet/standard/design-guidelines/).

Lo strumento di analisi rappresenta i controlli eseguiti durante un'analisi come messaggi di avviso. I messaggi di avviso identificano eventuali problemi di programmazione e progettazione e, se possibile, forniscono informazioni su come risolverli.

> [!NOTE]
> L'analisi legacy (analisi statica del codice) non è supportata per i progetti .NET Core e .NET Standard in Visual Studio. Se si esegue l'analisi del codice in un progetto .NET Core o .NET Standard come parte di MSBuild, verrà visualizzato un errore simile a **errore: CA0055: Impossibile identificare la piattaforma per \<il > dll**. Per analizzare il codice nei progetti .NET Core o .NET Standard, usare invece gli [analizzatori di codice](../code-quality/roslyn-analyzers-overview.md) .

## <a name="ide-integrated-development-environment-integration"></a>Integrazione con IDE (Integrated Development Environment)

È possibile eseguire l'analisi del codice nel progetto manualmente o automaticamente.

Per eseguire l'analisi del codice ogni volta che si compila un progetto, selezionare l'opzione nella pagina delle proprietà **analisi codice** del progetto. Per altre informazioni, vedere [procedura: abilitare e disabilitare l'analisi automatica del codice](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Per eseguire manualmente l'analisi del codice su un progetto, dalla barra dei menu scegliere **analizza** > **esegui analisi codice** > **eseguire l'analisi del codice su \<progetto >** .

## <a name="rule-sets"></a>Set di regole

Le regole per l'analisi del codice gestito vengono raggruppate in [set di regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). È possibile utilizzare uno dei set di regole standard Microsoft oppure è possibile [creare un set di regole personalizzato](../code-quality/how-to-create-a-custom-rule-set.md) per soddisfare esigenze specifiche.

## <a name="suppress-warnings"></a>Non visualizzare gli avvisi

È in genere utile indicare se un avviso non è applicabile. In questo modo lo sviluppatore e altri individui che potrebbero esaminare il codice in un secondo momento verranno informati del fatto che un avviso è stato sottoposto ad analisi, quindi è stato eliminato o ignorato.

L'eliminazione in origine degli avvisi viene implementata tramite attributi personalizzati. Per non visualizzare un avviso, aggiungere l'attributo `SuppressMessage` al codice sorgente, come illustrato nell'esempio seguente:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Per ulteriori informazioni, vedere la pagina relativa all' [eliminazione degli avvisi](../code-quality/in-source-suppression-overview.md).

::: moniker range="vs-2017"

> [!NOTE]
> Se si esegue la migrazione di un progetto a Visual Studio 2017, è possibile che si facciano improvvisamente molti avvisi di analisi del codice. Se non si è pronti per correggere gli avvisi, è possibile eliminarli tutti scegliendo **analizza** > **Esegui analisi codice ed elimina problemi attivi**.
>
> ![Eseguire l'analisi del codice ed escludere i problemi in Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Se si esegue la migrazione di un progetto a Visual Studio 2019, è possibile che si facciano improvvisamente molti avvisi di analisi del codice. Se non si è pronti per correggere gli avvisi, è possibile eliminarli tutti scegliendo **analizza** > **compilare ed eliminare i problemi attivi**.

::: moniker-end

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Eseguire l'analisi del codice come parte dei criteri di archiviazione

Le organizzazioni richiedono talvolta che tutte le archiviazioni soddisfino determinati criteri, tra cui, in particolare:

- Non sono presenti errori di compilazione nel codice da archiviare.

- L'analisi del codice viene eseguita come parte della build più recente.

A tale scopo, è utile quindi definire dei criteri specifici per l'archiviazione. Per altre informazioni, vedere [miglioramento della qualità del codice con i criteri di archiviazione del progetto](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Integrazione Team Build

È possibile utilizzare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi come parte del processo di compilazione. Per altre informazioni, vedere [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori basati su .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
- [Uso di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Procedura: Abilitare e disabilitare l'analisi codice automatica](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
