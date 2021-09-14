---
title: Disattivare l'analisi del codice
ms.date: 09/01/2020
description: Informazioni su come disattivare Visual Studio'analisi del codice sorgente in progetti .NET Core, .NET Standard e .NET Framework codice sorgente.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 8d86945cb39e1e6c37e62726b920ee774c0f7146
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632051"
---
# <a name="disable-source-code-analysis-for-net"></a>Disabilitare l'analisi del codice sorgente per .NET

::: moniker range=">=vs-2019"

Questa pagina consente di disabilitare l'analisi del codice Visual Studio. Esistono limitazioni a ciò che è possibile disabilitare e la procedura per disattivare l'analisi del codice varia a seconda di alcuni fattori:

- Project (.NET Core/Standard rispetto .NET Framework)

  I progetti .NET Core e .NET Standard hanno opzioni nella pagina delle proprietà Code Analysis che consentono di disattivare l'analisi del codice dagli analizzatori installati come NuGet pacchetto. Per altre informazioni, vedere [.NET Core e .NET Standard progetti](#net-core-and-net-standard-projects). Per disattivare l'analisi del codice sorgente .NET Framework progetti, vedere .NET Framework [progetti](#net-framework-projects).

- Analisi di origine e analisi legacy

  Questo argomento si applica all'analisi del codice sorgente e non all'analisi legacy (binaria). Per informazioni sulla disabilitazione dell'analisi legacy, vedere [Procedura: Abilitare e disabilitare l'analisi del codice legacy.](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

## <a name="net-core-and-net-standard-projects"></a>.NET Core e .NET Standard progetti

A partire da Visual Studio 2019 versione 16.3, nella pagina delle proprietà Code Analysis sono disponibili due caselle di controllo che consentono di controllare se gli analizzatori vengono eseguiti in fase di compilazione e in fase di progettazione. Queste opzioni sono specifiche del progetto.

![Abilitare o disabilitare l'analisi del codice in tempo reale o in fase di compilazione in Visual Studio](media/run-on-build-run-live-analysis.png)

Per aprire questa pagina, fare clic con il pulsante destro del mouse sul nodo del **progetto** Esplora soluzioni e scegliere **Proprietà**. Selezionare la **Code Analysis** dati.

- Per disabilitare l'analisi di origine in fase di compilazione, deselezionare **l'opzione Esegui in fase di** compilazione.
- Per disabilitare l'analisi delle origini in tempo reale, deselezionare **l'opzione Esegui analisi in** tempo reale.

> [!NOTE]
> A partire da Visual Studio 2019 versione 16.5, se si preferisce il flusso di lavoro di esecuzione dell'analisi del codice su richiesta, è possibile disabilitare l'esecuzione dell'analizzatore durante l'analisi in tempo reale e/o la compilazione e attivare manualmente l'analisi del codice una volta su un progetto o una soluzione su richiesta. Per informazioni sull'esecuzione manuale dell'analisi del codice, vedere [Procedura: Eseguire manualmente Code Analysis codice gestito](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="net-framework-projects"></a>.NET Framework progetti

Per disattivare l'analisi del codice sorgente per gli analizzatori, aggiungere una o più delle proprietà MSBuild seguenti al [file di progetto](../ide/solutions-and-projects-in-visual-studio.md#project-file).

| MSBuild proprietà | Descrizione | Predefinito |
| - | - | - |
| `RunAnalyzersDuringBuild` | Controlla se gli analizzatori vengono eseguiti in fase di compilazione. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Controlla se gli analizzatori analizzano il codice in tempo reale in fase di progettazione. | `true` |
| `RunAnalyzers` | Disabilita gli analizzatori sia in fase di compilazione che in fase di progettazione. Questa proprietà ha la precedenza su `RunAnalyzersDuringBuild` e `RunAnalyzersDuringLiveAnalysis` . | `true` |

Esempi:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Analisi dell'origine

Non è possibile disattivare [l'analisi](roslyn-analyzers-overview.md) dell'origine Visual Studio 2017. Per cancellare gli errori dell'analizzatore dall'Elenco **errori,** è possibile eliminare tutte le violazioni correnti selezionando Analizza Code Analysis ed Elimina problemi attivi sulla barra  >   dei menu. Per altre informazioni, vedere [Eliminare le violazioni](use-roslyn-analyzers.md#suppress-violations).

A partire Visual Studio 2019 versione 16.3, è possibile disattivare l'analisi del codice sorgente o eseguirla su richiesta. Valutare la possibilità di eseguire Visual Studio 2019.

## <a name="legacy-analysis"></a>Analisi legacy

È possibile disabilitare l'analisi legacy in fase di compilazione **nella pagina Code Analysis** proprietà. Per altre informazioni, vedere Procedura: Abilitare e [disabilitare l'analisi del codice legacy.](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Eliminare le violazioni](use-roslyn-analyzers.md#suppress-violations)
- [Procedura: Abilitare e disabilitare l'analisi del codice legacy](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
