---
title: Analisi del codice tramite gli analizzatori Roslyn
ms.date: 09/01/2020
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d0489950b9132a36aef8ecb3d8374c02d1a1aee2
ms.sourcegitcommit: d77da260d79471ab139973c51d65b04e0f80fe2e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2020
ms.locfileid: "90560736"
---
# <a name="overview-of-source-code-analysis"></a>Panoramica dell'analisi del codice sorgente

Gli analizzatori .NET Compiler Platform (Roslyn) esaminano il codice C# o Visual Basic per lo stile, la qualità, la gestibilità, la progettazione e altri problemi. Questa ispezione o analisi viene eseguita in fase di progettazione in tutti i file aperti. 

Gli analizzatori possono essere divisi nei gruppi seguenti:

- Gli analizzatori di [stili di codice](/visualstudio/ide/editorconfig-code-style-settings-reference?view=vs-2019#convention-categories) sono incorporati in Visual Studio. L'ID di diagnostica, o codice, per questi analizzatori è nel formato IDExxxx, ad esempio IDE0067. È possibile configurare le preferenze nella [pagina Opzioni editor di testo](../ide/code-styles-and-code-cleanup.md) o in un [file EditorConfig](../ide/editorconfig-code-style-settings-reference.md). A partire da .NET 5,0, gli analizzatori di stili di codice sono inclusi in .NET SDK e possono essere applicati in modo rigoroso come avvisi o errori di compilazione. Per altre informazioni, vedere [qui](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis).

- Gli analizzatori di [qualità del codice](code-analysis-warnings-for-managed-code-by-checkid.md) sono ora inclusi in .NET 5 SDK e abilitati per impostazione predefinita. L'ID di diagnostica, o codice, per questi analizzatori è nel formato CAXXXX, ad esempio CA1822. Per altre informazioni, vedere [Panoramica dell'analisi della qualità del codice .NET](/dotnet/fundamentals/productivity/code-analysis#code-quality-analysis).

- Gli analizzatori di terze parti possono essere installati come un pacchetto NuGet o un'estensione di Visual Studio. Analizzatori di terze parti, ad esempio [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [xUnit](https://www.nuget.org/packages/xunit.analyzers/)Analyzers e [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).

## <a name="severity-levels-of-analyzers"></a>Livelli di gravità degli analizzatori

Ogni analizzatore ha uno dei livelli di gravità seguenti:

| Gravità (Esplora soluzioni) | Gravità (file EditorConfig) | Comportamento in fase di compilazione | Comportamento dell'editor |
|-|-|-|
| Errore | `error` | Le violazioni vengono visualizzate come *errori* nel elenco errori e nell'output di compilazione da riga di comando e causano l'esito negativo delle compilazioni.| Il codice che offende è sottolineato con una zigzag rossa e contrassegnato da una piccola casella rossa nella barra di scorrimento. |
| Avviso | `warning` | Le violazioni vengono visualizzate come *avvisi* nell'elenco errori e nell'output di compilazione da riga di comando, ma non comportano la mancata riuscita delle compilazioni. | Il codice offensivo è sottolineato con una zigzag verde e contrassegnato da una piccola casella verde nella barra di scorrimento. |
| Info | `suggestion` | Le violazioni vengono visualizzate come *messaggi* nell'elenco errori e non nell'output di compilazione da riga di comando. | Il codice che causa il danneggiamento è sottolineato con un zigzag grigio e contrassegnato da una piccola casella grigia nella barra di scorrimento. |
| Nascosto | `silent` | Non visibile all'utente. | Non visibile all'utente. Tuttavia, la diagnostica viene segnalata al motore di diagnostica IDE. |
| nessuno | `none` | Eliminati completamente. | Eliminati completamente. |
| Impostazione predefinita | `default` | Corrisponde alla gravità predefinita della regola. Per determinare il valore predefinito di una regola, cercare nell'Finestra Proprietà. | Corrisponde alla gravità predefinita della regola. |

Se le violazioni delle regole vengono trovate da un analizzatore, vengono segnalate nell'editor del codice (come *zigzag* sotto il codice che causa il errore) e nella finestra Elenco errori.

![Violazione dell'analizzatore nella finestra Elenco errori](../code-quality/media/code-analysis-error-list.png)

Le violazioni dell'analizzatore segnalate nell'elenco errori corrispondono all' [impostazione del livello di gravità](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) della regola. Le violazioni dell'analizzatore vengono visualizzate anche nell'editor di codice come controllo ortografia durante sotto il codice danneggiato. Nella figura seguente vengono illustrate tre violazioni di &mdash; un errore (rosso zigzag), un avviso (zigzag verde) e un suggerimento (tre punti grigi):

![Controllo ortografia durante nell'editor di codice in Visual Studio](media/diagnostics-severity-colors.png)

Molte regole dell'analizzatore o *diagnostica*hanno una o più *correzioni del codice* associate che è possibile applicare per correggere la violazione della regola. Le correzioni del codice vengono visualizzate nel menu con l'icona a forma di lampadina insieme ad altri tipi di [azioni rapide](../ide/quick-actions.md). Per informazioni su queste correzioni del codice, vedere [Azioni rapide comuni](../ide/quick-actions.md).

![Violazione dell'analizzatore e correzione del codice tramite azione rapida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>Configurare i livelli di gravità dell'analizzatore

È possibile configurare la gravità delle regole dell'analizzatore o della *diagnostica*in un [file EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) o dal [menu lampadina](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu). 

Gli analizzatori possono anche essere configurati per esaminare il codice in fase di compilazione e vivere durante la digitazione. È possibile configurare l'ambito dell'analisi codice in tempo reale da eseguire solo per il documento corrente, tutti i documenti aperti o l'intera soluzione. Vedere [procedura: configurare l'ambito dell'analisi codice in tempo reale](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> Gli errori e gli avvisi in fase di compilazione degli analizzatori del codice vengono visualizzati solo se gli analizzatori sono installati come pacchetto NuGet. Gli analizzatori incorporati, ad esempio IDE0067 e IDE0068, non vengono mai eseguiti durante la compilazione.

## <a name="nuget-package-versus-vsix-extension"></a>Pacchetto NuGet ed estensione VSIX

Gli analizzatori di terze parti possono essere installati per progetto tramite un pacchetto NuGet. Alcuni sono disponibili anche come estensione di Visual Studio, nel qual caso si applicano a qualsiasi soluzione aperta in Visual Studio. Esistono alcune differenze di comportamento fondamentali tra questi due metodi di [installazione degli analizzatori](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Ambito

Se si installano gli analizzatori come estensione di Visual Studio, si applicano a livello di soluzione e a tutte le istanze di Visual Studio. Se si installano gli analizzatori come pacchetto NuGet (metodo preferito), si applicano solo al progetto in cui è stato installato il pacchetto NuGet. Negli ambienti di team gli analizzatori installati come pacchetti NuGet sono inclusi nell'ambito per *tutti gli sviluppatori* che lavorano sul progetto.

### <a name="build-errors"></a>Errori di compilazione

Per applicare le regole in fase di compilazione, anche tramite la riga di comando o come parte di una compilazione di integrazione continua, è possibile scegliere una delle opzioni seguenti:

- Creare un progetto .NET 5,0 che includa gli analizzatori per impostazione predefinita in .NET SDK. L'analisi del codice è abilitata per impostazione predefinita per i progetti destinati a .NET 5.0 o versione successiva. È possibile abilitare l'analisi del codice per i progetti destinati a versioni precedenti di .NET impostando la proprietà [EnableNETAnalyzers](https://docs.microsoft.com/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) su true.

- Installare gli analizzatori come pacchetto NuGet. Gli errori e avvisi dell'analizzatore non vengono visualizzati nel report di compilazione se si installano gli analizzatori come estensione.

Nell'immagine seguente viene illustrato l'output di compilazione da riga di comando della compilazione di un progetto che contiene una violazione della regola dell'analizzatore:

![Output MSBuild con violazione della regola](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravità della regola

Non è possibile configurare la gravità delle regole degli analizzatori installate come estensioni di Visual Studio. Per configurare la [gravità della regola](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) installare gli analizzatori come pacchetto NuGet.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Installare gli analizzatori del codice in Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usare gli analizzatori del codice in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vedere anche

- [Domande frequenti sugli analizzatori](analyzers-faq.md)
- [Scrivere un analizzatore del codice personalizzato](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
