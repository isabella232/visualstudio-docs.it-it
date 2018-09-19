---
title: Analisi del codice FxCop e gli analizzatori FxCop
ms.date: 09/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e05dd0e01254bf1222a8a7de497b11ec2a808bfb
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2018
ms.locfileid: "46136367"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Domande frequenti su FxCop e FxCop analizzatori

Può essere un po' fuorviante comprendere le differenze tra legacy FxCop e FxCop analizzatori. Questo articolo contribuisce a risolvere alcune delle domande che è possibile.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Qual è la differenza tra legacy FxCop e FxCop analizzatori?

FxCop legacy viene eseguita l'analisi post-compilazione in un assembly compilato. Viene eseguito come un altro file eseguibile chiamato **FxCopCmd.exe**. FxCopCmd.exe carica l'assembly compilato, esegue l'analisi del codice e quindi segnala i risultati (o *diagnostica*).

Gli analizzatori FxCop sono basati su .NET Compiler Platform ("Roslyn"). Si [installarli come pacchetto NuGet](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) che fa riferimento il progetto o soluzione. Gli analizzatori FxCop Esegui del codice sorgente basato su analisi durante l'esecuzione del compilatore. Gli analizzatori FxCop sono ospitati all'interno del processo di compilazione, ovvero **csc.exe** oppure **vbc.exe**, ed eseguire l'analisi quando viene compilato il progetto. Analizzatore i risultati insieme ai risultati del compilatore.

> [!NOTE]
> È anche possibile [installare gli analizzatori FxCop come un'estensione di Visual Studio](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). In questo caso, gli analizzatori vengono eseguiti i digitazione nell'editor del codice, ma non come eseguirle in fase di compilazione. Se si desidera eseguire gli analizzatori FxCop come parte di integrazione continua (CI), installarli come pacchetto NuGet invece.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Il comando Esegui analisi del codice esegue gli analizzatori FxCop?

No. Quando si seleziona **Analyze** > **Esegui analisi del codice** in Visual Studio 2017, esegue l'analisi statica del codice o FxCop legacy. **Esegui analisi del codice** ha effetto sugli analizzatori basati su Roslyn, inclusi gli analizzatori FxCop basati su Roslyn.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>La proprietà del progetto msbuild RunCodeAnalysis esegue gli analizzatori?

No. Il **RunCodeAnalysis** proprietà in un file di progetto (ad esempio *csproj*) viene utilizzato solo per l'esecuzione di FxCop legacy. Esegue un'attività di post-compilazione msbuild che richiama **FxCopCmd.exe**. Ciò equivale a selezione **Analyze** > **Esegui analisi del codice** in Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>In che modo eseguire quindi gli analizzatori FxCop?

Per eseguire gli analizzatori FxCop, innanzitutto [installare il pacchetto NuGet](install-fxcop-analyzers.md) per loro. Quindi compilare il progetto o soluzione da Visual Studio o mediante msbuild. Verranno visualizzati gli avvisi e gli errori che generano gli analizzatori FxCop nel **elenco errori** o la finestra di comando.

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Introduzione a analizzatori](fxcop-analyzers.yml)
- [Installare gli analizzatori FxCop](install-fxcop-analyzers.md)
