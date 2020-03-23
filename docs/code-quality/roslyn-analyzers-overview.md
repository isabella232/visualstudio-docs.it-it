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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "79431280"
---
# <a name="overview-of-source-code-analyzers"></a>Panoramica degli analizzatori di codice sorgente

Gli analizzatori di codice della piattaforma del compilatore .NET ("Roslyn") controllano il codice Di Visual Basic o di C.NET per verificare la ricerca di stili, qualità e manutenibilità, progettazione e altri problemi.

- Alcuni analizzatori sono incorporati in Visual Studio.Some analyzers are built in to Visual Studio. L'ID di diagnostica, o codice, per questi analizzatori è nel formato IDExxxx, ad esempio IDE0067. La maggior parte di questi analizzatori incorporati controlla lo stile del [codice](../ide/code-styles-and-code-cleanup.md)ed è possibile configurare le preferenze nella pagina delle opzioni dell'editor di [testo](../ide/code-styles-and-code-cleanup.md) o in un [file EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Una manciata di analizzatori incorporati esaminano la qualità del codice.

- È possibile installare analizzatori aggiuntivi come pacchetto NuGet o un'estensione di Visual Studio.You can install additional analyzers as a NuGet package or a Visual Studio extension. Ad esempio:

  - [Analizzatori FxCop](../code-quality/install-fxcop-analyzers.md), analizzatori di qualità del codice consigliati da Microsoft
  - Analizzatori di terze parti, ad esempio [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/)e [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

Se le violazioni delle regole vengono rilevate da un analizzatore, vengono segnalate nell'editor di codice (come sottolineacontore *ondulatore* sotto il codice che causa l'errore) e nella finestra Elenco errori.

Molte regole dell'analizzatore, o *utilità di diagnostica*, hanno una o più *correzioni del codice* associate che possono essere applicate per correggere il problema. Tutte le utilità di diagnostica dell'analizzatore integrate in Visual Studio hanno una correzione del codice associata. Le correzioni del codice vengono visualizzate nel menu con l'icona a forma di lampadina insieme ad altri tipi di [azioni rapide](../ide/quick-actions.md). Per informazioni su queste correzioni del codice, vedere [Azioni rapide comuni](../ide/common-quick-actions.md).

![Violazione dell'analizzatore e correzione del codice tramite azione rapida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Analisi del codice sorgente rispetto all'analisi legacy

L'analisi sorgente degli analizzatori Roslyn sostituisce [l'analisi legacy](../code-quality/code-analysis-for-managed-code-overview.md) per il codice gestito. Molte delle regole di analisi legacy sono già state riscritte come analizzatori di codice Roslyn. Per i modelli di progetto più recenti, ad esempio i progetti .NET Core e .NET Standard, l'analisi legacy non è ancora disponibile.

Analogamente alle violazioni delle regole di analisi legacy, le violazioni dell'analisi del codice sorgente vengono visualizzate nella finestra Elenco errori in Visual Studio.Like legacy analysis rule violations, source code analysis violations appear in the Error List window in Visual Studio. Inoltre, le violazioni dell'analisi del codice sorgente vengono visualizzate anche nell'editor di codice come *azigoma sotto* il codice offensivo. Il colore della linea ondulata dipende dall'[impostazione di gravità](../code-quality/use-roslyn-analyzers.md#rule-severity) della regola. L'immagine seguente mostra&mdash;tre violazioni una rossa, una verde e una grigia:

![Squiggles nell'editor di codice in Visual Studio](media/diagnostics-severity-colors.png)

Gli analizzatori di codice controllano il codice in fase di compilazione, ad esempio l'analisi legacy se è abilitata, ma risiedono anche durante la digitazione. È possibile configurare l'ambito dell'analisi del codice attivo da eseguire solo per il documento corrente, per tutti i documenti aperti o per l'intera soluzione. Vedere [Procedura: configurare l'ambito dell'analisi del codice in tempo reale.](./configure-live-code-analysis-scope-managed-code.md)

> [!TIP]
> Gli errori e gli avvisi in fase di compilazione degli analizzatori del codice vengono visualizzati solo se gli analizzatori sono installati come pacchetto NuGet. Gli analizzatori incorporati (ad esempio, IDE0067 e IDE0068) non vengono mai eseguiti durante la compilazione.

Non solo gli analizzatori di codice Roslyn segnalano gli stessi tipi di problemi che l'analisi legacy fa, ma rendono più facile per voi per risolvere una o tutte le occorrenze della violazione nel file o progetto. Queste azioni sono denominate *correzioni del codice*. Le correzioni del codice sono specifiche dell'IDE; in Visual Studio, vengono implementati come [azioni rapide](../ide/quick-actions.md). Non tutte le utilità diagnostiche dell'analizzatore hanno una correzione del codice associata.

> [!NOTE]
> Prima della versione di Visual Studio 2019 16.5, **l'opzione** > di menu Analizza**analisi codice** di esecuzione esegue l'analisi legacy. A partire da Visual Studio 2019 16.5, l'opzione di menu **Esegui analisi codice** esegue analizzatori basati su Roslyn per il progetto o la soluzione selezionata.

Per distinguere tra le violazioni dagli analizzatori di codice e l'analisi legacy nell'Elenco errori, esaminare la colonna **Strumento.To** differentiate between violations from code analyzers and legacy analysis in the Error List, look at the Tool column. Se il valore di Strumento corrisponde a uno degli assembly nell'analizzatore in **Esplora soluzioni**, ad esempio **Microsoft.CodeQuality.Analyzers**, la violazione proviene da un analizzatore del codice. In caso contrario, la violazione proviene dall'analisi legacy.

![Colonna Strumento nell'Elenco errori](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> La proprietà **MSBuild RunCodeAnalysis** in un file di progetto si applica solo all'analisi legacy. Se si installano analizzatori, impostare **RunCodeAnalysis** su **false** nel file di progetto, per impedire l'esecuzione dell'analisi legacy dopo la compilazione.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Pacchetto NuGet ed estensione VSIX

Gli analizzatori di codice Roslyn possono essere installati per progetto tramite un pacchetto NuGet.Roslyn code analyzers can be installed per-project via a NuGet package. Alcuni sono disponibili anche come estensione di Visual Studio, nel qual caso si applicano a qualsiasi soluzione aperta in Visual Studio.Some are also available as a Visual Studio extension, in which case they apply to any solution you open in Visual Studio. Esistono alcune differenze di comportamento fondamentali tra questi due metodi di [installazione degli analizzatori](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Scope

Se si installano analizzatori come estensione di Visual Studio, vengono applicati a livello di soluzione e a tutte le istanze di Visual Studio.If you install analyzers as a Visual Studio extension, they apply at the solution level and to all instances of Visual Studio. Se si installano gli analizzatori come pacchetto NuGet (metodo preferito), si applicano solo al progetto in cui è stato installato il pacchetto NuGet. Negli ambienti di team gli analizzatori installati come pacchetti NuGet sono inclusi nell'ambito per *tutti gli sviluppatori* che lavorano sul progetto.

### <a name="build-errors"></a>Errori di compilazione

Per avere regole applicate in fase di compilazione, anche tramite la riga di comando o nell'ambito di una compilazione di integrazione continua (CI, Continuous Integration), installare gli analizzatori come pacchetto NuGet. Gli errori e avvisi dell'analizzatore non vengono visualizzati nel report di compilazione se si installano gli analizzatori come estensione.

L'immagine seguente mostra l'output di compilazione da riga di comando dalla compilazione di un progetto che contiene una violazione della regola dell'analizzatore:The following image shows the command-line build output from building a project that contains an analyzer rule violation:

![Output MSBuild con violazione della regola](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravità della regola

Non è possibile configurare la gravità delle regole degli analizzatori installati come estensione di Visual Studio.You cannot configure the severity of rules from analyzers that were installed as a Visual Studio extension. Per configurare la [gravità della regola](../code-quality/use-roslyn-analyzers.md#rule-severity) installare gli analizzatori come pacchetto NuGet.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Installare gli analizzatori del codice in Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usare gli analizzatori del codice in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vedere anche

- [Domande frequenti sugli analizzatori](analyzers-faq.md)
- [Scrivere un analizzatore del codice personalizzato](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
