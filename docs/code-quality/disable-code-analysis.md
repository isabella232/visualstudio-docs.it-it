---
title: Disattiva analisi codice
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb1a41642e405046459f6196a98cd6290a217223
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649656"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Come disabilitare l'analisi del codice sorgente per il codice gestito

::: moniker range=">=vs-2019"

Questa pagina consente di disabilitare l'analisi del codice in Visual Studio. Esistono limitazioni a ciò che è possibile disabilitare e la procedura per la disattivazione dell'analisi del codice varia a seconda dei fattori seguenti:

- Tipo di progetto (.NET Core/standard e .NET Framework)

  I progetti .NET Core e .NET Standard includono opzioni nella pagina delle proprietà dell'analisi del codice che consentono di disattivare l'analisi del codice dagli analizzatori installati come pacchetto NuGet. Per altre informazioni, vedere [progetti .NET Core e .NET standard](#net-core-and-net-standard-projects). Per disattivare l'analisi del codice sorgente per i progetti .NET Framework, vedere [progetti di .NET Framework](#net-framework-projects).

- Pacchetto di NuGet Analyzer rispetto a VSIX o a analizzatori predefiniti

  Attualmente, non è possibile disabilitare l'analisi del codice in tempo reale per gli analizzatori incorporati, ad esempio l'ID regola IDE0067. Analogamente, non è possibile disabilitare l'analisi del codice in tempo reale per gli analizzatori installati come parte di un'estensione di Visual Studio (VSIX). Per escludere gli errori e gli avvisi dagli analizzatori basati su VSIX e incorporati, scegliere **analizza**  > **compilare ed evitare i problemi attivi** nella barra dei menu. È *possibile* disabilitare l'analisi in tempo reale e predefinita per gli analizzatori installati come parte di un pacchetto NuGet.

- Analisi dell'origine rispetto all'analisi legacy

  Questo argomento è valido per l'analisi del codice sorgente e non per l'analisi legacy (binaria). Per informazioni sulla disabilitazione dell'analisi legacy, vedere [procedura: abilitare e disabilitare l'analisi del codice legacy](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>Progetti .NET Core e .NET Standard

A partire da Visual Studio 2019 versione 16,3, sono disponibili due caselle di controllo nella pagina delle proprietà di analisi del codice che consentono di controllare se gli analizzatori basati su NuGet vengono eseguiti in fase di compilazione e di progettazione. Queste opzioni sono specifiche del progetto.

![Abilitare o disabilitare l'analisi del codice in tempo reale o la compilazione in Visual Studio](media/run-on-build-run-live-analysis.png)

Per aprire questa pagina, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**. Selezionare la scheda **analisi codice** .

- Per disabilitare l'analisi dell'origine in fase di compilazione, deselezionare l'opzione **Esegui su compilazione** .
- Per disabilitare l'analisi dell'origine dinamica, deselezionare l'opzione **Esegui su analisi Live** .

> [!NOTE]
> Gli analizzatori basati su VSIX e incorporati continueranno a offrire l'analisi in tempo reale del codice, anche se l' **esecuzione in Live Analysis** è deselezionata. Se si desidera impedire errori e avvisi da questi analizzatori, scegliere **analizza**  > **compilare ed evitare problemi attivi** nella barra dei menu.

## <a name="net-framework-projects"></a>Progetti .NET Framework

Per disattivare l'analisi del codice sorgente per gli analizzatori installati come parte di un pacchetto NuGet, aggiungere una o più delle seguenti proprietà di MSBuild al [file di progetto](../ide/solutions-and-projects-in-visual-studio.md#project-file).

| MSBuild (proprietà) | Descrizione | Impostazione predefinita |
| - | - | - |
| `RunAnalyzersDuringBuild` | Controlla se gli analizzatori basati su NuGet vengono eseguiti in fase di compilazione. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Controlla se gli analizzatori basati su NuGet analizzano il codice in tempo reale in fase di progettazione. | `true` |
| `RunAnalyzers` | Disabilita gli analizzatori basati su NuGet in fase di compilazione e di progettazione. Questa proprietà ha la precedenza rispetto a `RunAnalyzersDuringBuild` e `RunAnalyzersDuringLiveAnalysis`. | `true` |

Esempi:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Analisi dell'origine

Non è possibile disattivare l' [analisi dell'origine](roslyn-analyzers-overview.md) in Visual Studio 2017. Se si desidera cancellare gli errori dell'analizzatore dalla Elenco errori, è possibile eliminare tutte le violazioni correnti scegliendo **analizza**  > **Esegui analisi codice ed elimina problemi attivi** sulla barra dei menu. Per ulteriori informazioni, vedere la pagina relativa all' [eliminazione delle violazioni](use-roslyn-analyzers.md#suppress-violations).

A partire da Visual Studio 2019 versione 16,3, è possibile disattivare l'analisi del codice sorgente basata su NuGet. Provare a eseguire l'aggiornamento a Visual Studio 2019.

## <a name="legacy-analysis"></a>Analisi legacy

È possibile disabilitare l'analisi legacy della fase di compilazione nella pagina delle proprietà dell' **analisi del codice** . Per altre informazioni, vedere [procedura: abilitare e disabilitare l'analisi del codice legacy](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Vedere anche

- [Non visualizzare le violazioni](use-roslyn-analyzers.md#suppress-violations)
- [Procedura: abilitare e disabilitare l'analisi del codice legacy](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
