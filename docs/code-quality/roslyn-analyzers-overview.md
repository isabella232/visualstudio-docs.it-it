---
title: Analisi del codice tramite gli analizzatori Roslyn
ms.date: 10/03/2019
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 78a47cb2a5aefd7d20e0b8087f5f3ad735716175
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "79431280"
---
# <a name="overview-of-source-code-analyzers"></a>Panoramica degli analizzatori del codice sorgente

Gli analizzatori di codice .NET Compiler Platform ("Roslyn") esaminano il codice C# o Visual Basic per lo stile, la qualità e la gestibilità, la progettazione e altri problemi.

- Alcuni analizzatori sono incorporati in Visual Studio. L'ID di diagnostica, o codice, per questi analizzatori è nel formato IDExxxx, ad esempio IDE0067. La maggior parte di questi analizzatori incorporati controlla [lo stile del codice](../ide/code-styles-and-code-cleanup.md)ed è possibile configurare le preferenze nella [pagina delle opzioni dell'editor di testo](../ide/code-styles-and-code-cleanup.md) o in un [file EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Alcuni analizzatori incorporati esaminano la qualità del codice.

- È possibile installare altri analizzatori come un pacchetto NuGet o un'estensione di Visual Studio. Ad esempio:

  - [Analizzatori FxCop](../code-quality/install-fxcop-analyzers.md), analizzatori di qualità del codice consigliati da Microsoft
  - Analizzatori di terze parti, ad esempio [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [xUnit](https://www.nuget.org/packages/xunit.analyzers/)Analyzers e [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

Se le violazioni delle regole vengono trovate da un analizzatore, vengono segnalate nell'editor del codice (come *zigzag* sotto il codice che causa il errore) e nella finestra Elenco errori.

Molte regole dell'analizzatore, o *utilità di diagnostica*, hanno una o più *correzioni del codice* associate che possono essere applicate per correggere il problema. Tutte le utilità di diagnostica dell'analizzatore integrate in Visual Studio hanno una correzione del codice associata. Le correzioni del codice vengono visualizzate nel menu con l'icona a forma di lampadina insieme ad altri tipi di [azioni rapide](../ide/quick-actions.md). Per informazioni su queste correzioni del codice, vedere [Azioni rapide comuni](../ide/common-quick-actions.md).

![Violazione dell'analizzatore e correzione del codice tramite azione rapida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Analisi del codice sorgente rispetto all'analisi legacy

L'analisi dell'origine da analizzatori Roslyn sostituisce l' [analisi legacy](../code-quality/code-analysis-for-managed-code-overview.md) per il codice gestito. Molte delle regole di analisi legacy sono già state riscritte come analizzatori di codice Roslyn. Per i modelli di progetto più recenti, ad esempio i progetti .NET Core e .NET Standard, l'analisi legacy non è ancora disponibile.

Analogamente alle violazioni delle regole di analisi legacy, le violazioni dell'analisi del codice sorgente vengono visualizzate nella finestra di Elenco errori in Visual Studio. Inoltre, le violazioni dell'analisi del codice sorgente vengono visualizzate nell'editor di codice come *controllo ortografia durante* sotto il codice che causa il danneggiamento. Il colore della linea ondulata dipende dall'[impostazione di gravità](../code-quality/use-roslyn-analyzers.md#rule-severity) della regola. Nella figura seguente sono illustrate tre violazioni &mdash; , una rossa, una verde e una grigia:

![Controllo ortografia durante nell'editor di codice in Visual Studio](media/diagnostics-severity-colors.png)

Gli analizzatori di codice ispezionano il codice in fase di compilazione, ad esempio l'analisi legacy se è abilitata, ma anche durante la digitazione. È possibile configurare l'ambito dell'analisi codice in tempo reale da eseguire solo per il documento corrente, tutti i documenti aperti o l'intera soluzione. Vedere [procedura: configurare l'ambito dell'analisi codice in tempo reale](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> Gli errori e gli avvisi in fase di compilazione degli analizzatori del codice vengono visualizzati solo se gli analizzatori sono installati come pacchetto NuGet. Gli analizzatori incorporati, ad esempio IDE0067 e IDE0068, non vengono mai eseguiti durante la compilazione.

Gli analizzatori di codice Roslyn non solo segnalano gli stessi tipi di problemi che l'analisi legacy esegue, ma semplificano la correzione di una o tutte le occorrenze della violazione nel file o nel progetto. Queste azioni sono denominate *correzioni del codice*. Le correzioni del codice sono specifiche dell'IDE. in Visual Studio sono implementate come [azioni rapide](../ide/quick-actions.md). Non tutte le utilità diagnostiche dell'analizzatore hanno una correzione del codice associata.

> [!NOTE]
> Prima della versione di Visual Studio 2019 16,5, l'opzione di menu **analizza**  >  **esecuzione codice** esegue l'analisi legacy. A partire da Visual Studio 2019 16,5, l'opzione di menu **Esegui analisi codice** esegue gli analizzatori basati su Roslyn per il progetto o la soluzione selezionata.

Per distinguere tra le violazioni degli analizzatori di codice e dell'analisi legacy nel Elenco errori, vedere la colonna **degli strumenti** . Se il valore di Strumento corrisponde a uno degli assembly nell'analizzatore in **Esplora soluzioni**, ad esempio **Microsoft.CodeQuality.Analyzers**, la violazione proviene da un analizzatore del codice. In caso contrario, la violazione proviene dall'analisi legacy.

![Colonna Strumento nell'Elenco errori](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> La proprietà MSBuild **RunCodeAnalysis** in un file di progetto si applica solo all'analisi legacy. Se si installano gli analizzatori, impostare **RunCodeAnalysis** su **false** nel file di progetto, per impedire l'esecuzione dell'analisi legacy dopo la compilazione.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Pacchetto NuGet ed estensione VSIX

Gli analizzatori di codice Roslyn possono essere installati per progetto tramite un pacchetto NuGet. Alcuni sono disponibili anche come estensione di Visual Studio, nel qual caso si applicano a qualsiasi soluzione aperta in Visual Studio. Esistono alcune differenze di comportamento fondamentali tra questi due metodi di [installazione degli analizzatori](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Ambito

Se si installano gli analizzatori come estensione di Visual Studio, si applicano a livello di soluzione e a tutte le istanze di Visual Studio. Se si installano gli analizzatori come pacchetto NuGet (metodo preferito), si applicano solo al progetto in cui è stato installato il pacchetto NuGet. Negli ambienti di team gli analizzatori installati come pacchetti NuGet sono inclusi nell'ambito per *tutti gli sviluppatori* che lavorano sul progetto.

### <a name="build-errors"></a>Errori di compilazione

Per avere regole applicate in fase di compilazione, anche tramite la riga di comando o nell'ambito di una compilazione di integrazione continua (CI, Continuous Integration), installare gli analizzatori come pacchetto NuGet. Gli errori e avvisi dell'analizzatore non vengono visualizzati nel report di compilazione se si installano gli analizzatori come estensione.

Nell'immagine seguente viene illustrato l'output di compilazione da riga di comando della compilazione di un progetto che contiene una violazione della regola dell'analizzatore:

![Output MSBuild con violazione della regola](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravità della regola

Non è possibile configurare la gravità delle regole degli analizzatori installate come estensioni di Visual Studio. Per configurare la [gravità della regola](../code-quality/use-roslyn-analyzers.md#rule-severity) installare gli analizzatori come pacchetto NuGet.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Installare gli analizzatori del codice in Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usare gli analizzatori del codice in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vedere anche

- [Domande frequenti sugli analizzatori](analyzers-faq.md)
- [Scrivere un analizzatore del codice personalizzato](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
