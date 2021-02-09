---
title: Analisi del codice FxCop (analisi binaria) e analizzatori .NET (analisi dell'origine)
ms.date: 09/06/2018
description: Comprendere la differenza tra FxCop legacy (analisi binaria) e analizzatori .NET (analisi dell'origine) in Visual Studio. Vedere le risposte alle domande su come usare questi analizzatori.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 951e9b951f1d90077fe29506e9c288fb19f2d5ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867763"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Domande frequenti sugli analizzatori FxCop e .NET legacy

Per comprendere le differenze tra le differenze tra FxCop legacy (analisi binaria) e gli analizzatori .NET (analisi dell'origine), è possibile creare un po' di confusione. Questo articolo aiuta a chiarire alcune possibili domande.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>Qual è la differenza tra gli analizzatori FxCop e .NET legacy?

FxCop legacy esegue l'analisi post-compilazione in un assembly compilato. Viene eseguito come un eseguibile separato di nome **FxCopCmd.exe**. FxCopCmd.exe carica l'assembly compilato, esegue l'analisi del codice e quindi genera un report dei risultati (o *utilità di diagnostica*).

Gli analizzatori .NET sono basati sulla .NET Compiler Platform ("Roslyn"). È possibile [abilitarli da .NET SDK o installarli come pacchetto NuGet](install-net-analyzers.md) a cui fa riferimento il progetto o la soluzione. Gli analizzatori eseguono l'analisi basata sul codice sorgente durante l'esecuzione del compilatore. Gli analizzatori sono ospitati all'interno del processo del compilatore, **csc.exe** o **vbc.exe**, ed eseguire l'analisi al momento della compilazione del progetto. I risultati degli analizzatori vengono indicati insieme ai risultati del compilatore.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>Qual è la differenza tra gli analizzatori FxCop e gli analizzatori .NET?

Sia gli analizzatori FxCop che gli analizzatori .NET fanno riferimento alle implementazioni dell'analizzatore .NET Compiler Platform ("Roslyn") delle regole CA FxCop. Prima di Visual Studio 2019 16,8 e .NET 5,0, questi analizzatori venivano forniti come `Microsoft.CodeAnalysis.FxCopAnalyzers` [pacchetto NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). A partire da Visual Studio 2019 16,8 e .NET 5,0, questi analizzatori sono [inclusi in .NET SDK](/dotnet/fundamentals/code-analysis/overview). Sono disponibili anche come `Microsoft.CodeAnalysis.NetAnalyzers` [pacchetto NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Si consiglia [di eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>Il comando Esegui analisi codice esegue gli analizzatori .NET?

Prima della versione di Visual Studio 2019 16,5, quando si seleziona **analizza**  >  **Esegui analisi codice**, viene eseguita l'analisi legacy. A partire da Visual Studio 2019 16,5, l'opzione di menu **Esegui analisi codice** esegue gli analizzatori basati su Roslyn per il progetto o la soluzione selezionata. Se sono stati installati analizzatori .NET, verranno eseguiti anche. Per altre informazioni, vedere [procedura: eseguire manualmente l'analisi del codice per il codice gestito](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>La proprietà del progetto msbuild RunCodeAnalysis esegue gli analizzatori?

No. La proprietà **RunCodeAnalysis** in un file di progetto (ad esempio, un file con estensione *csproj*) viene usata solo per l'esecuzione di FxCop legacy. Esegue un'attività msbuild di post-compilazione che richiama **FxCopCmd.exe**.

## <a name="so-how-do-i-run-net-analyzers-then"></a>In che modo è possibile eseguire gli analizzatori .NET?

Per eseguire gli analizzatori .NET, [abilitarli per prima cosa da .NET SDK o installarli come pacchetto NuGet](install-net-analyzers.md). Compilare quindi il progetto o soluzione da Visual Studio o mediante msbuild. Gli avvisi e gli errori generati dagli analizzatori Roslyn verranno visualizzati nel **Elenco errori** o nella finestra di comando.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>Viene visualizzato un avviso CA0507 anche dopo aver installato il pacchetto NuGet di .NET Analyzers

Se sono stati installati analizzatori .NET ma si continua a ricevere l'avviso CA0507 **"" Esegui analisi codice "è stato deprecato a favore degli analizzatori FxCop, che vengono eseguiti durante la compilazione"**, potrebbe essere necessario impostare la proprietà MSBuild **RunCodeAnalysis** nel [file di progetto](../ide/solutions-and-projects-in-visual-studio.md#project-file) su **false**. In caso contrario, l'analisi legacy verrà eseguita dopo ogni compilazione.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>Quali regole sono state trasferite agli analizzatori .NET?

Per informazioni sulle regole di analisi legacy che sono state trasferite agli analizzatori .NET, vedere [stato della porta della regola FxCop](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Gli avvisi di analisi del codice vengono considerati errori

Se il progetto usa l'opzione di compilazione per considerare gli avvisi come errori, gli avvisi dell'analizzatore possono apparire come errori. Per evitare che gli avvisi di analisi del codice vengano considerati errori, attenersi alla procedura descritta in [domande frequenti sull'analisi del codice](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Vedi anche

- [Panoramica degli analizzatori .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Eseguire la migrazione ad analizzatori .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Installare gli analizzatori .NET](install-net-analyzers.md)
