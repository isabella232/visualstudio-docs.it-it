---
title: Analisi del codice FxCop (analisi binaria) e analizzatori .NET (analisi del codice sorgente)
ms.date: 09/06/2018
description: Comprendere la differenza tra fxCop legacy (analisi binaria) e analizzatori .NET (analisi dell'origine) in Visual Studio. Vedere le risposte alle domande su come usare questi analizzatori.
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
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800504"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Domande frequenti sugli analizzatori FxCop e .NET legacy

Può generare un po' di confusione comprendere le differenze tra gli analizzatori FxCop legacy (analisi binaria) e gli analizzatori .NET (analisi dell'origine). Questo articolo aiuta a chiarire alcune possibili domande.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>Qual è la differenza tra gli analizzatori FxCop legacy e .NET?

FxCop legacy esegue l'analisi post-compilazione in un assembly compilato. Viene eseguito come un eseguibile separato di nome **FxCopCmd.exe**. FxCopCmd.exe carica l'assembly compilato, esegue l'analisi del codice e quindi genera un report dei risultati (o *utilità di diagnostica*).

Gli analizzatori .NET sono basati sulla .NET Compiler Platform ("Roslyn"). È [possibile abilitarli da .NET SDK](install-net-analyzers.md) o installarli come pacchetto NuGet a cui fa riferimento il progetto o la soluzione. Gli analizzatori eseguono l'analisi basata sul codice sorgente durante l'esecuzione del compilatore. Gli analizzatori sono ospitati nel  processo del compilatore,csc.exeovbc.exe, **ed** eseguono l'analisi quando viene compilato il progetto. I risultati degli analizzatori vengono indicati insieme ai risultati del compilatore.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>Qual è la differenza tra gli analizzatori FxCop e gli analizzatori .NET?

Sia gli analizzatori FxCop che gli analizzatori .NET fanno riferimento alle implementazioni dell'analizzatore .NET Compiler Platform ("Roslyn") delle regole della CA FxCop. Prima di Visual Studio 2019 16.8 e .NET 5.0, questi analizzatori sono stati forniti come `Microsoft.CodeAnalysis.FxCopAnalyzers` [pacchetto NuGet.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) A partire Visual Studio 2019 16.8 e .NET 5.0, questi analizzatori sono [inclusi in .NET SDK.](/dotnet/fundamentals/code-analysis/overview) Sono disponibili anche come `Microsoft.CodeAnalysis.NetAnalyzers` [pacchetto NuGet.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) Valutare la [possibilità di eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET.](migrate-from-fxcop-analyzers-to-net-analyzers.md)

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>Il comando Esegui Code Analysis esegue analizzatori .NET?

Prima di Visual Studio versione 2019 16.5, quando si seleziona Analizza Code Analysis esegue l'analisi  >  legacy. A Visual Studio 2019 16.5,  l'opzione di menu Esegui Code Analysis esegue analizzatori basati su Roslyn per il progetto o la soluzione selezionata. Se sono stati installati analizzatori .NET, verranno eseguiti anche questi. Per altre informazioni, vedere [Procedura: Eseguire manualmente Code Analysis codice gestito.](how-to-run-code-analysis-manually-for-managed-code.md)

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>La proprietà del progetto msbuild RunCodeAnalysis esegue gli analizzatori?

No. La proprietà **RunCodeAnalysis** in un file di progetto (ad esempio, un file con estensione *csproj*) viene usata solo per l'esecuzione di FxCop legacy. Esegue un'attività msbuild di post-compilazione che richiama **FxCopCmd.exe**.

## <a name="so-how-do-i-run-net-analyzers-then"></a>Come si eseguono quindi gli analizzatori .NET?

Per eseguire gli analizzatori .NET, abilitarli prima [da .NET SDK o installarli come pacchetto NuGet.](install-net-analyzers.md) Compilare quindi il progetto o soluzione da Visual Studio o mediante msbuild. Gli avvisi e gli errori generati dall'analizzatore Roslyn verranno visualizzati **nell'Elenco errori** o nella finestra di comando.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>Viene visualizzato l'avviso CA0507 anche dopo aver installato il pacchetto NuGet degli analizzatori .NET

Se sono stati installati analizzatori .NET ma si continua a ricevere l'avviso CA0507 **""Esegui Code Analysis"** è stato deprecato a favore degli analizzatori FxCop, che vengono eseguiti durante la compilazione", potrebbe essere necessario impostare la proprietà msbuild **RunCodeAnalysis** nel [file](../ide/solutions-and-projects-in-visual-studio.md#project-file) di progetto **su false.** In caso contrario, l'analisi legacy verrà eseguita dopo ogni compilazione.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>Quali regole sono state portate agli analizzatori .NET?

Per informazioni sulle regole di analisi legacy che sono state portate agli analizzatori .NET, vedere [Stato delle porte delle regole Fxcop.](fxcop-rule-port-status.md)

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Gli avvisi di analisi del codice vengono considerati errori

Se il progetto usa l'opzione di compilazione per considerare gli avvisi come errori, gli avvisi dell'analizzatore possono essere visualizzati come errori. Per evitare che gli avvisi di analisi del codice vengano considerati come errori, seguire la procedura descritta in [Code analysis FAQ (Domande frequenti sull'analisi del codice).](../code-quality/analyzers-faq.md#treat-warnings-as-errors)

## <a name="see-also"></a>Vedi anche

- [Panoramica degli analizzatori .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Eseguire la migrazione ad analizzatori .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Installare gli analizzatori .NET](install-net-analyzers.md)
