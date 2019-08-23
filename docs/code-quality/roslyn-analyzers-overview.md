---
title: Analisi del codice tramite gli analizzatori Roslyn
ms.date: 03/26/2018
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2d4a9bfca972f9c57688b19bd872b31ee5997f76
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550772"
---
# <a name="overview-of-net-compiler-platform-code-analyzers"></a>Panoramica degli analizzatori di codice .NET Compiler Platform

Gli analizzatori .NET Compiler Platform ("Roslyn") esaminano lo stile di codice, la qualità e manutenibilità del codice, la progettazione del codice e altri aspetti. Visual Studio include un set predefinito di analizzatori che analizzano il codice C# o Visual Basic durante la digitazione. Le preferenze per gli analizzatori predefiniti si configurano nella pagina [Opzioni dell'editor di testo](../ide/code-styles-and-code-cleanup.md) o in un [file .editorconfig](../ide/editorconfig-code-style-settings-reference.md). È possibile installare analizzatori aggiuntivi come estensione di Visual Studio o come pacchetto NuGet.

Se rilevate da un analizzatore, eventuali violazioni delle regole vengono segnalate nell'editor di codice con una *linea ondulata* sotto al codice che causa l'errore e nella finestra **Elenco errori**.

Molte regole dell'analizzatore, o *utilità di diagnostica*, hanno una o più *correzioni del codice* associate che possono essere applicate per correggere il problema. Tutte le utilità di diagnostica dell'analizzatore integrate in Visual Studio hanno una correzione del codice associata. Le correzioni del codice vengono visualizzate nel menu con l'icona a forma di lampadina insieme ad altri tipi di [azioni rapide](../ide/quick-actions.md). Per informazioni su queste correzioni del codice, vedere [Azioni rapide comuni](../ide/common-quick-actions.md).

![Violazione dell'analizzatore e correzione del codice tramite azione rapida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="net-compiler-platform-based-analysis-versus-legacy-analysis"></a>Analisi basata su .NET Compiler Platform o analisi legacy

L'analisi del codice con .NET Compiler Platform ("Roslyn") sostituirà infine l'[analisi legacy](../code-quality/code-analysis-for-managed-code-overview.md) per il codice gestito. Molte delle regole di analisi legacy sono già state riscritte come analizzatori di codice basati su .NET Compiler Platform.

Analogamente alle violazioni delle regole di analisi legacy, le violazioni dell'analisi del codice basata su .NET Compiler Platform vengono visualizzate nella finestra Elenco errori in Visual Studio. Inoltre, le violazioni dell'analisi del codice basata su .NET Compiler Platform vengono visualizzate anche nell'editor di codice come *linee ondulate* sotto il codice che causa l'errore. Il colore della linea ondulata dipende dall'[impostazione di gravità](../code-quality/use-roslyn-analyzers.md#rule-severity) della regola. Nello screenshot seguente sono illustrate tre violazioni: una rossa, una verde e una grigia.

![Linee ondulate nell'editor del codice](media/diagnostics-severity-colors.png)

Gli analizzatori del codice basati su .NET Compiler Platform analizzano il codice in fase di compilazione, come l'analisi legacy se abilitata, ma anche in tempo reale durante la digitazione. Se si abilita l'[analisi della soluzione completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis), gli analizzatori del codice offrono anche l'analisi in fase di progettazione dei file di codice che non sono aperti nell'editor.

> [!TIP]
> Gli errori e gli avvisi in fase di compilazione degli analizzatori del codice vengono visualizzati solo se gli analizzatori sono installati come pacchetto NuGet.

Gli analizzatori del codice basati su .NET Compiler Platform non solo segnalano gli stessi tipi di problemi rilevati dall'analisi legacy, ma consentono anche di correggere rapidamente una o tutte le occorrenze della violazione nel file o progetto. Queste azioni sono denominate *correzioni del codice*. Le correzioni del codice sono specifiche dell'IDE; in Visual Studio, vengono implementate come [azioni rapide](../ide/quick-actions.md). Non tutte le utilità diagnostiche dell'analizzatore hanno una correzione del codice associata.

> [!NOTE]
> Le opzioni dell'interfaccia utente seguenti si applicano solo all'analisi legacy:
>
> - Opzione di menu **Analisi** > **Esegui analisi del codice**.
> - Caselle di controllo **Abilita analisi codice su compilazione** e **Non visualizzare i risultati del codice generato** nella scheda **Analisi del codice** delle pagine delle proprietà di un progetto.

Per distinguere le violazioni degli analizzatori del codice dall'analisi legacy nella finestra Elenco errori, vedere la colonna **Strumento**. Se il valore di Strumento corrisponde a uno degli assembly nell'analizzatore in **Esplora soluzioni**, ad esempio **Microsoft.CodeQuality.Analyzers**, la violazione proviene da un analizzatore del codice. In caso contrario, la violazione proviene dall'analisi legacy.

![Colonna Strumento nell'Elenco errori](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> La proprietà msbuild **RunCodeAnalysis** in un file di progetto si applica solo all'analisi legacy. Se si installano gli analizzatori, impostare **RunCodeAnalysis** su **false** nel file di progetto per impedire l'esecuzione dell'analisi legacy dopo la compilazione.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Pacchetto NuGet ed estensione VSIX

Gli analizzatori .NET Compiler Platform possono essere installati in base al progetto tramite un pacchetto NuGet oppure a livello di Visual Studio come estensione di Visual Studio. Esistono alcune differenze di comportamento fondamentali tra questi due metodi di [installazione degli analizzatori](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Ambito

Se si installano gli analizzatori come estensione di Visual Studio, si applicano a livello di soluzione a tutte le istanze di Visual Studio. Se si installano gli analizzatori come pacchetto NuGet (metodo preferito), si applicano solo al progetto in cui è stato installato il pacchetto NuGet. Negli ambienti di team gli analizzatori installati come pacchetti NuGet sono inclusi nell'ambito per *tutti gli sviluppatori* che lavorano sul progetto.

### <a name="build-errors"></a>Errori di compilazione

Per avere regole applicate in fase di compilazione, anche tramite la riga di comando o nell'ambito di una compilazione di integrazione continua (CI, Continuous Integration), installare gli analizzatori come pacchetto NuGet. Gli errori e avvisi dell'analizzatore non vengono visualizzati nel report di compilazione se si installano gli analizzatori come estensione.

Nello screenshot seguente viene illustrato l'output di compilazione da riga di comando proveniente dalla compilazione di un progetto con una violazione della regola dell'analizzatore:

![Output MSBuild con violazione della regola](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravità della regola

Non è possibile impostare la gravità delle regole provenienti da analizzatori installati come estensione di Visual Studio. Per configurare la [gravità della regola](../code-quality/use-roslyn-analyzers.md#rule-severity) installare gli analizzatori come pacchetto NuGet.

## <a name="categories"></a>Categories

Di seguito sono illustrati i diversi tipi di analizzatori che risultano utili per analizzare il codice:

- Analizzatori consigliati da Microsoft: [Analizzatori FxCop](../code-quality/fxcop-analyzers.yml)
- Analizzatori dell'IDE di Visual Studio: [EditorConfig](../ide/code-styles-and-code-cleanup.md)
- Analizzatori di terze parti: [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/), [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Installare gli analizzatori del codice in Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usare gli analizzatori del codice in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vedere anche

- [Domande frequenti sugli analizzatori](analyzers-faq.md)
- [Scrivere un analizzatore del codice personalizzato](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
