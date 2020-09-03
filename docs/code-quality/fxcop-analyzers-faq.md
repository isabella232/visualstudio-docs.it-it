---
title: Analisi del codice FxCop e analizzatori FxCop
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc04cbc6d46d8dc47a08d06c8c5949bb5d9107f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "79431365"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Domande frequenti su FxCop e gli analizzatori FxCop

La comprensione delle differenze tra FxCop legacy e gli analizzatori FxCop può non risultare immediata. Questo articolo aiuta a chiarire alcune possibili domande.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Qual è la differenza tra FxCop legacy e gli analizzatori FxCop?

FxCop legacy esegue l'analisi post-compilazione in un assembly compilato. Viene eseguito come un eseguibile separato di nome **FxCopCmd.exe**. FxCopCmd.exe carica l'assembly compilato, esegue l'analisi del codice e quindi genera un report dei risultati (o *utilità di diagnostica*).

Gli analizzatori FxCop sono basati su .NET Compiler Platform ("Roslyn"). Essi vengono [installati come pacchetto NuGet](install-fxcop-analyzers.md#nuget-package) al quale fa riferimento il progetto o soluzione. Gli analizzatori FxCop eseguono un'analisi basata sul codice sorgente durante l'esecuzione del compilatore. Gli analizzatori FxCop sono ospitati all'interno del processo di compilazione, **csc.exe** o **vbc.exe**, ed eseguono l'analisi quando viene compilato il progetto. I risultati degli analizzatori vengono indicati insieme ai risultati del compilatore.

> [!NOTE]
> È anche possibile [installare gli analizzatori FxCop come estensione di Visual Studio](install-fxcop-analyzers.md#vsix). In questo caso, gli analizzatori vengono eseguiti durante la digitazione nell'editor di codice, ma non vengono eseguiti in fase di compilazione. Se si vogliono eseguire gli analizzatori FxCop nell'ambito dell'integrazione continua, installarli come pacchetto NuGet.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Il comando Esegui analisi codice esegue gli analizzatori FxCop?

Prima della versione di Visual Studio 2019 16,5, quando si seleziona **analizza**  >  **Esegui analisi codice**, viene eseguita l'analisi legacy. A partire da Visual Studio 2019 16,5, l'opzione di menu **Esegui analisi codice** esegue gli analizzatori basati su Roslyn per il progetto o la soluzione selezionata. Se sono stati installati analizzatori FxCop basati su Roslyn, verranno eseguiti anche. Per altre informazioni, vedere [procedura: eseguire manualmente l'analisi del codice per il codice gestito](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>La proprietà del progetto msbuild RunCodeAnalysis esegue gli analizzatori?

No. La proprietà **RunCodeAnalysis** in un file di progetto (ad esempio, un file con estensione *csproj*) viene usata solo per l'esecuzione di FxCop legacy. Esegue un'attività msbuild di post-compilazione che richiama **FxCopCmd.exe**.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>In che modo eseguire quindi gli analizzatori FxCop?

Per eseguire gli analizzatori FxCop, per prima cosa [installare il pacchetto NuGet](install-fxcop-analyzers.md) applicabile. Compilare quindi il progetto o soluzione da Visual Studio o mediante msbuild. Gli avvisi ed errori generati dagli analizzatori FxCop verranno visualizzati nell'**Elenco errori** o nella finestra di comando.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Viene visualizzato l'avviso CA0507 anche dopo aver installato il pacchetto NuGet degli analizzatori FxCop

Se sono stati installati analizzatori FxCop ma si continua a ricevere l'avviso CA0507 **"" Esegui analisi codice "è stato deprecato a favore degli analizzatori FxCop, che vengono eseguiti durante la compilazione"**, potrebbe essere necessario impostare la proprietà MSBuild **RunCodeAnalysis** nel [file di progetto](../ide/solutions-and-projects-in-visual-studio.md#project-file) su **false**. In caso contrario, l'analisi legacy verrà eseguita dopo ogni compilazione.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>Quali regole sono state trasferite agli analizzatori FxCop?

Per informazioni sulle regole di analisi legacy che sono state trasferite agli [analizzatori FxCop](install-fxcop-analyzers.md), vedere [stato della porta della regola FxCop](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Gli avvisi di analisi del codice vengono considerati errori

Se il progetto usa l'opzione di compilazione per considerare gli avvisi come errori, gli avvisi di FxCop Analyzer possono apparire come errori. Per evitare che gli avvisi di analisi del codice vengano considerati errori, attenersi alla procedura descritta in [domande frequenti sull'analisi del codice](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Eseguire la migrazione agli analizzatori FxCop](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [Installare gli analizzatori FXCop](install-fxcop-analyzers.md)
