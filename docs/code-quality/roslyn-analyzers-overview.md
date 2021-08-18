---
title: Analisi del codice tramite gli analizzatori Roslyn
ms.date: 09/01/2020
description: Acquisire familiarità con l'analisi del codice sorgente in Visual Studio. Informazioni sulle correzioni del codice e sui diversi tipi di analizzatori e livelli di gravità.
ms.custom: SEO-VS-2020
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: a0b477f4dcb5d7c2148b40f648c41b9fea5a1578
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059372"
---
# <a name="overview-of-source-code-analysis"></a>Panoramica dell'analisi del codice sorgente

.NET Compiler Platform analizzatori (Roslyn) controllano il codice C# o Visual Basic per verificare lo stile, la qualità, la manutenibilità, la progettazione e altri problemi. Questa ispezione o analisi viene eseguita in fase di progettazione in tutti i file aperti.

Gli analizzatori possono essere suddivisi nei gruppi seguenti:

- [Gli analizzatori](/dotnet/fundamentals/code-analysis/code-style-rule-options?preserve-view=true&view=vs-2019#convention-categories) di stile del codice sono incorporati per Visual Studio. L'ID di diagnostica, o codice, per questi analizzatori è nel formato IDExxxx, ad esempio IDE0067. È possibile configurare le preferenze nella pagina [delle opzioni dell'editor di testo](../ide/code-styles-and-code-cleanup.md) o in un file [EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options). A partire da .NET 5.0, gli analizzatori di stile del codice sono inclusi in .NET SDK e possono essere applicati rigorosamente come avvisi o errori di compilazione. Per altre informazioni, vedere [qui](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis).

- [Gli analizzatori](/dotnet/fundamentals/code-analysis/quality-rules/index) della qualità del codice sono ora inclusi in .NET 5 SDK e abilitati per impostazione predefinita. L'ID di diagnostica, o codice, per questi analizzatori è nel formato CAxxxx, ad esempio CA1822. Per altre informazioni, vedere [Panoramica dell'analisi della qualità del codice .NET.](/dotnet/fundamentals/productivity/code-analysis#code-quality-analysis)

- Gli analizzatori di terze parti possono essere installati come pacchetto NuGet o come estensione Visual Studio di terze parti. Analizzatori di terze parti, ad [esempio StyleCop,](https://www.nuget.org/packages/StyleCop.Analyzers/) [Roslynator,](https://www.nuget.org/packages/Roslynator.Analyzers/) [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/)e [Sonar Analyzer.](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="severity-levels-of-analyzers"></a>Livelli di gravità degli analizzatori

Ogni analizzatore ha uno dei livelli di gravità seguenti:

| Gravità (Esplora soluzioni) | Gravità (file EditorConfig) | Comportamento in fase di compilazione | Comportamento dell'editor |
|-|-|-|
| Errore | `error` | Le violazioni vengono visualizzate *come errori* nell'elenco errori e nell'output di compilazione della riga di comando e causano errori nelle compilazioni.| Il codice offensivo è sottolineato con una sottolineatura a sottolineatura rossa e contrassegnato da una piccola casella rossa nella barra di scorrimento. |
| Avviso | `warning` | Le violazioni vengono visualizzate *come avvisi* nell'elenco errori e nell'output di compilazione della riga di comando, ma non causano errori nelle compilazioni. | Il codice che ha commesso l'offesa è sottolineato con una sottolineatura a scorrimento verde e contrassegnato da una piccola casella verde nella barra di scorrimento. |
| Info | `suggestion` | Le violazioni vengono visualizzate *come Messaggi* nell'elenco errori e non nell'output di compilazione della riga di comando. | Il codice offensivo è sottolineato con una sottolineatura a sottolineatura a scorrimento grigia e contrassegnato da una piccola casella grigia nella barra di scorrimento. |
| Nascosto | `silent` | Non visibile all'utente. | Non visibile all'utente. La diagnostica viene tuttavia segnalata al motore di diagnostica IDE. |
| Nessuno | `none` | Eliminato completamente. | Eliminato completamente. |
| Predefinito | `default` | Corrisponde alla gravità predefinita della regola. Per determinare qual è il valore predefinito per una regola, cercare nella Finestra Proprietà. | Corrisponde alla gravità predefinita della regola. |

Se le violazioni delle regole vengono trovate da un analizzatore,  vengono segnalate nell'editor di codice (come a forma di antessamento sotto il codice in errore) e nella finestra Elenco errori.

![Violazione dell'analizzatore nella finestra Elenco errori](../code-quality/media/code-analysis-error-list.png)

Le violazioni dell'analizzatore segnalate nell'elenco errori corrispondono all'impostazione del livello [di gravità](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) della regola. Le violazioni dell'analizzatore vengono inoltre mostrate nell'editor di codice sotto il codice in errore. L'immagine seguente mostra tre violazioni: un errore &mdash; (arrotolamento), un avviso (arrotola verde) e un suggerimento (tre punti grigi):

![Aquiggles nell'editor di codice in Visual Studio](media/diagnostics-severity-colors.png)

Molte regole dell'analizzatore, *o diagnostica,* hanno una o più correzioni di codice *associate* che è possibile applicare per correggere la violazione della regola. Le correzioni del codice vengono visualizzate nel menu con l'icona a forma di lampadina insieme ad altri tipi di [azioni rapide](../ide/quick-actions.md). Per informazioni su queste correzioni del codice, vedere [Azioni rapide comuni](../ide/quick-actions.md).

![Violazione dell'analizzatore e correzione del codice tramite azione rapida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>Configurare i livelli di gravità dell'analizzatore

È possibile configurare la gravità delle regole dell'analizzatore, o *diagnostica,* in un [file EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) o dal [menu lampadina](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu).

Gli analizzatori possono anche essere configurati per controllare il codice in fase di compilazione e in tempo reale durante la digitazione. È possibile configurare l'ambito dell'analisi del codice in tempo reale da eseguire solo per il documento corrente, per tutti i documenti aperti o per l'intera soluzione. Vedere [Procedura: Configurare l'ambito dell'analisi del codice in tempo reale.](./configure-live-code-analysis-scope-managed-code.md)

> [!TIP]
> Gli errori e gli avvisi in fase di compilazione degli analizzatori del codice vengono visualizzati solo se gli analizzatori sono installati come pacchetto NuGet. Gli analizzatori predefiniti (ad esempio, IDE0067 e IDE0068) non vengono mai eseguiti durante la compilazione.

## <a name="nuget-package-versus-vsix-extension"></a>Pacchetto NuGet ed estensione VSIX

Gli analizzatori di terze parti possono essere installati per ogni progetto tramite un NuGet pacchetto. Alcuni sono anche disponibili come estensione Visual Studio, nel qual caso si applicano a qualsiasi soluzione aperta in Visual Studio. Esistono alcune differenze di comportamento fondamentali tra questi due metodi di [installazione degli analizzatori](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Ambito

Se si installano analizzatori come estensione Visual Studio, si applicano a livello di soluzione e a tutte le istanze di Visual Studio. Se si installano gli analizzatori come pacchetto NuGet (metodo preferito), si applicano solo al progetto in cui è stato installato il pacchetto NuGet. Negli ambienti di team gli analizzatori installati come pacchetti NuGet sono inclusi nell'ambito per *tutti gli sviluppatori* che lavorano sul progetto.

### <a name="build-errors"></a>Errori di compilazione

Per applicare regole in fase di compilazione, anche tramite la riga di comando o come parte di una compilazione di integrazione continua, è possibile scegliere una delle opzioni seguenti:

- Creare un progetto .NET 5.0 che include analizzatori per impostazione predefinita in .NET SDK. L'analisi del codice è abilitata per impostazione predefinita per i progetti destinati a .NET 5.0 o versione successiva. È possibile abilitare l'analisi del codice nei progetti che hanno come destinazione versioni precedenti di .NET impostando la [proprietà EnableNETAnalyzers](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) su true.

- Installare gli analizzatori come NuGet pacchetto. Gli errori e avvisi dell'analizzatore non vengono visualizzati nel report di compilazione se si installano gli analizzatori come estensione.

L'immagine seguente mostra l'output di compilazione della riga di comando dalla compilazione di un progetto che contiene una violazione della regola dell'analizzatore:

![Output MSBuild con violazione della regola](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravità della regola

Non è possibile configurare la gravità delle regole dagli analizzatori installati come Visual Studio predefinita. Per configurare la [gravità della regola](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) installare gli analizzatori come pacchetto NuGet.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Installare gli analizzatori del codice in Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usare gli analizzatori del codice in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vedi anche

- [Domande frequenti sugli analizzatori](analyzers-faq.yml)
- [Scrivere un analizzatore del codice personalizzato](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)