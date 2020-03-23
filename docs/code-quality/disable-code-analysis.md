---
title: Disattivare l'analisi del codice
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8db6ad7bed4b1526d87112f33d3586728728d7f5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431397"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Come disabilitare l'analisi del codice sorgente per il codice gestitoHow to disable source code analysis for managed code

::: moniker range=">=vs-2019"

Questa pagina consente di disabilitare l'analisi del codice in Visual Studio.This page helps you disable code analysis in Visual Studio. Esistono limitazioni a ciò che è possibile disabilitare e la procedura per disattivare l'analisi del codice varia a seconda di alcuni fattori:

- Tipo di progetto (.NET Core/Standard e .NET Framework)

  I progetti .NET Core e .NET Standard dispongono di opzioni nella pagina delle proprietà Analisi codice che consentono di disattivare l'analisi del codice dagli analizzatori installati come pacchetto NuGet.NET Core and .NET Standard projects have options on their Code Analysis properties page that let you turn off code analysis from analyzers installed as a NuGet package. Per ulteriori informazioni, vedere [Progetti .NET Core e .NET Standard](#net-core-and-net-standard-projects). Per disattivare l'analisi del codice sorgente per i progetti .NET Framework, vedere [Progetti .NET Framework](#net-framework-projects).

- Analisi delle origini rispetto all'analisi legacy

  Questo argomento si applica all'analisi del codice sorgente e non all'analisi legacy (binaria). Per informazioni sulla disabilitazione dell'analisi legacy, vedere [Procedura: abilitare e disabilitare l'analisi](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)del codice legacy.

## <a name="net-core-and-net-standard-projects"></a>Progetti .NET Core e .NET Standard

A partire da Visual Studio 2019 versione 16.3, sono disponibili due caselle di controllo nella pagina delle proprietà Analisi codice che consentono di controllare se gli analizzatori vengono eseguiti in fase di compilazione e in fase di progettazione. Queste opzioni sono specifiche del progetto.

![Abilitare o disabilitare l'analisi del codice in tempo reale o in fase di compilazione in Visual StudioEnable or disable live code analysis or on build in Visual Studio](media/run-on-build-run-live-analysis.png)

Per aprire questa pagina, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**. Selezionare la scheda **Analisi codice.**

- Per disabilitare l'analisi di origine in fase di compilazione, deselezionare l'opzione **Esegui in fase** di compilazione.
- Per disattivare l'analisi delle origini dinamiche, deselezionare l'opzione **Esegui analisi in tempo reale.**

> [!NOTE]
> A partire da Visual Studio 2019 versione 16.5, se si preferisce il flusso di lavoro di esecuzione dell'analisi del codice su richiesta, è possibile disabilitare l'esecuzione dell'analizzatore durante l'analisi in tempo reale e/o la compilazione e l'attivazione manuale dell'analisi del codice una volta su un progetto o in una soluzione su richiesta. Per informazioni sull'esecuzione manuale dell'analisi del codice, vedere [Procedura: eseguire manualmente l'analisi](how-to-run-code-analysis-manually-for-managed-code.md)del codice per il codice gestito .  

## <a name="net-framework-projects"></a>Progetti .NET Framework

Per disattivare l'analisi del codice sorgente per gli analizzatori, aggiungere una o più delle seguenti proprietà MSBuild al file di [progetto.](../ide/solutions-and-projects-in-visual-studio.md#project-file)

| MSBuild (proprietà) | Descrizione | Predefinito |
| - | - | - |
| `RunAnalyzersDuringBuild` | Controlla se gli analizzatori vengono eseguiti in fase di compilazione. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Controlla se gli analizzatori analizzano il codice in tempo reale in fase di progettazione. | `true` |
| `RunAnalyzers` | Disabilita gli analizzatori sia in fase di compilazione che in fase di progettazione. Questa proprietà ha `RunAnalyzersDuringBuild` la `RunAnalyzersDuringLiveAnalysis`precedenza su e . | `true` |

Esempi:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Analisi dell'origine

Non è possibile disattivare [l'analisi di origine](roslyn-analyzers-overview.md) in Visual Studio 2017.You cannot turn off source analysis in Visual Studio 2017. Se si desidera cancellare gli errori dell'analizzatore dall'Elenco errori, è possibile eliminare tutte le violazioni correnti scegliendo **Analizza** > analisi codice di esecuzione**ed Elimina problemi attivi** sulla barra dei menu. Per ulteriori informazioni, consultate [Eliminazione delle violazioni.](use-roslyn-analyzers.md#suppress-violations)

A partire da Visual Studio 2019 versione 16.3, è possibile disattivare l'analisi del codice sorgente o eseguirla su richiesta. Valutare la possibilità di eseguire l'aggiornamento a Visual Studio 2019.Consider upgrading to Visual Studio 2019.

## <a name="legacy-analysis"></a>Analisi legacy

È possibile disabilitare l'analisi legacy in fase di compilazione nella pagina delle proprietà **Analisi codice.** Per ulteriori informazioni, vedere [Procedura: abilitare e disabilitare l'analisi](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)del codice legacy.

::: moniker-end

## <a name="see-also"></a>Vedere anche

- [Eliminazione delle violazioni](use-roslyn-analyzers.md#suppress-violations)
- [Procedura: abilitare e disabilitare l'analisi del codice legacyHow to: Enable and disable legacy code analysis](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
