---
title: Disattiva analisi codice
ms.date: 09/01/2020
description: Informazioni su come disattivare l'analisi del codice sorgente di Visual Studio nei progetti .NET Core, .NET Standard e .NET Framework.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.openlocfilehash: 6a1f1466caa921d46ce4701f5074b98f3d5ba051
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860386"
---
# <a name="disable-source-code-analysis-for-net"></a>Disabilitare l'analisi del codice sorgente per .NET

::: moniker range=">=vs-2019"

Questa pagina consente di disabilitare l'analisi del codice in Visual Studio. Esistono limitazioni a ciò che è possibile disabilitare e la procedura per la disattivazione dell'analisi del codice varia a seconda dei fattori seguenti:

- Tipo di progetto (.NET Core/standard e .NET Framework)

  I progetti .NET Core e .NET Standard includono opzioni nella pagina delle proprietà dell'analisi del codice che consentono di disattivare l'analisi del codice dagli analizzatori installati come pacchetto NuGet. Per altre informazioni, vedere [progetti .NET Core e .NET standard](#net-core-and-net-standard-projects). Per disattivare l'analisi del codice sorgente per i progetti .NET Framework, vedere [progetti di .NET Framework](#net-framework-projects).

- Analisi dell'origine rispetto all'analisi legacy

  Questo argomento è valido per l'analisi del codice sorgente e non per l'analisi legacy (binaria). Per informazioni sulla disabilitazione dell'analisi legacy, vedere [procedura: abilitare e disabilitare l'analisi del codice legacy](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>Progetti .NET Core e .NET Standard

A partire da Visual Studio 2019 versione 16,3, nella pagina delle proprietà dell'analisi del codice sono disponibili due caselle di controllo che consentono di controllare se gli analizzatori vengono eseguiti in fase di compilazione e di progettazione. Queste opzioni sono specifiche del progetto.

![Abilitare o disabilitare l'analisi del codice in tempo reale o la compilazione in Visual Studio](media/run-on-build-run-live-analysis.png)

Per aprire questa pagina, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**. Selezionare la scheda **analisi codice** .

- Per disabilitare l'analisi dell'origine in fase di compilazione, deselezionare l'opzione **Esegui su compilazione** .
- Per disabilitare l'analisi dell'origine dinamica, deselezionare l'opzione **Esegui su analisi Live** .

> [!NOTE]
> A partire da Visual Studio 2019 versione 16,5, se si preferisce il flusso di lavoro di esecuzione dell'analisi del codice su richiesta, è possibile disabilitare l'esecuzione dell'analizzatore durante l'analisi in tempo reale e/o compilare e attivare manualmente l'analisi del codice una sola volta in un progetto o in una soluzione su richiesta. Per informazioni sull'esecuzione manuale dell'analisi del codice, vedere [procedura: eseguire manualmente l'analisi del codice per il codice gestito](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="net-framework-projects"></a>Progetti .NET Framework

Per disattivare l'analisi del codice sorgente per gli analizzatori, aggiungere una o più delle seguenti proprietà MSBuild al [file di progetto](../ide/solutions-and-projects-in-visual-studio.md#project-file).

| MSBuild (proprietà) | Descrizione | Predefinito |
| - | - | - |
| `RunAnalyzersDuringBuild` | Controlla se gli analizzatori vengono eseguiti in fase di compilazione. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Controlla se gli analizzatori analizzano il codice in tempo reale in fase di progettazione. | `true` |
| `RunAnalyzers` | Disabilita gli analizzatori in fase di compilazione e di progettazione. Questa proprietà ha la precedenza rispetto `RunAnalyzersDuringBuild` a e `RunAnalyzersDuringLiveAnalysis` . | `true` |

Esempi:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Analisi dell'origine

Non è possibile disattivare l' [analisi dell'origine](roslyn-analyzers-overview.md) in Visual Studio 2017. Se si desidera cancellare gli errori dell'analizzatore dalla **Elenco errori**, è possibile eliminare tutte le violazioni correnti selezionando **analizza**  >  **Esegui analisi codice ed elimina problemi attivi** sulla barra dei menu. Per ulteriori informazioni, vedere la pagina relativa all' [eliminazione delle violazioni](use-roslyn-analyzers.md#suppress-violations).

A partire da Visual Studio 2019 versione 16,3, è possibile disattivare l'analisi del codice sorgente o eseguirla su richiesta. Provare a eseguire l'aggiornamento a Visual Studio 2019.

## <a name="legacy-analysis"></a>Analisi legacy

È possibile disabilitare l'analisi legacy della fase di compilazione nella pagina delle proprietà dell' **analisi del codice** . Per altre informazioni, vedere [procedura: abilitare e disabilitare l'analisi del codice legacy](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Non visualizzare le violazioni](use-roslyn-analyzers.md#suppress-violations)
- [Procedura: abilitare e disabilitare l'analisi del codice legacy](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
