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
ms.openlocfilehash: 36985ab7a0ee94cb735b1954a9e5ea9c2e0d2bbf
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "57869096"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Panoramica degli analizzatori .NET Compiler Platform

Gli analizzatori .NET Compiler Platform ("Roslyn") esaminano lo stile di codice, la qualità e manutenibilità del codice, la progettazione del codice e altri aspetti. Visual Studio include un set predefinito di analizzatori che analizzano il codice C# o Visual Basic durante la digitazione. Le preferenze per gli analizzatori predefiniti si configurano nella pagina [Opzioni dell'editor di testo](../ide/code-styles-and-quick-actions.md) o in un [file .editorconfig](../ide/editorconfig-code-style-settings-reference.md). È possibile installare analizzatori aggiuntivi come estensione di Visual Studio o come pacchetto NuGet.

Se rilevate da un analizzatore, eventuali violazioni delle regole vengono segnalate nell'editor di codice con una *linea ondulata* sotto al codice che causa l'errore e nella finestra **Elenco errori**.

Molte regole dell'analizzatore, o *utilità di diagnostica*, hanno una o più *correzioni del codice* associate che possono essere applicate per correggere il problema. Tutte le utilità di diagnostica dell'analizzatore integrate in Visual Studio hanno una correzione del codice associata. Le correzioni del codice vengono visualizzate nel menu con l'icona a forma di lampadina insieme ad altri tipi di [azioni rapide](../ide/quick-actions.md). Per informazioni su queste correzioni del codice, vedere [Azioni rapide comuni](../ide/common-quick-actions.md).

![Violazione dell'analizzatore e correzione del codice tramite azione rapida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analizzatori di Roslyn e analisi statica del codice

Gli analizzatori .NET Compiler Platform ("Roslyn") sostituiranno infine l'[analisi statica del codice](../code-quality/code-analysis-for-managed-code-overview.md) per il codice gestito. Molte delle regole di analisi statica del codice sono già state riscritte come diagnostica dell'analizzatore di Roslyn.

Come le violazioni delle regole di analisi statica del codice, le violazioni dell'analizzatore di Roslyn vengono visualizzate nell'**Elenco errori**. Le violazioni dell'analizzatore di Roslyn vengono visualizzate anche nell'editor del codice come *linee ondulate* sotto al codice che causa l'errore. Il colore della linea ondulata dipende dall'[impostazione di gravità](../code-quality/use-roslyn-analyzers.md#rule-severity) della regola. Nello screenshot seguente sono illustrate tre violazioni: una rossa, una verde e una grigia.

![Linee ondulate nell'editor di codice](media/diagnostics-severity-colors.png)

Gli analizzatori Roslyn analizzano il codice in fase di compilazione, ad esempio durante l'analisi statica del codice se abilitata, ma anche in tempo reale durante la digitazione. Se si abilita l'[analisi della soluzione completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis), gli analizzatori Roslyn offrono anche l'analisi in fase di progettazione dei file di codice che non sono aperti nell'editor.

> [!NOTE]
> Gli errori e gli avvisi in fase di compilazione degli analizzatori di Roslyn vengono visualizzati solo se gli analizzatori sono installati come pacchetto NuGet.

Gli analizzatori di Roslyn non solo segnalano gli stessi tipi di problemi rilevati dall'analisi statica del codice, ma consentono anche di correggere rapidamente una o tutte le occorrenze della violazione nel file o progetto. Queste azioni sono denominate *correzioni del codice*. Le correzioni del codice sono specifiche dell'IDE; in Visual Studio, vengono implementate come [azioni rapide](../ide/quick-actions.md). Non tutte le utilità diagnostiche dell'analizzatore hanno una correzione del codice associata.

> [!NOTE]
> L'opzione di menu **Analizza** > **Esegui analisi codice** si applica solo all'analisi statica del codice. Nella pagina delle proprietà **Analisi codice** di un progetto le caselle di controllo **Abilita analisi codice su compilazione** e **Non visualizzare i risultati del codice generato** si applicano solo all'analisi statica del codice. Non hanno alcun effetto sugli analizzatori di Roslyn.

Per distinguere le violazioni degli analizzatori di Roslyn dall'analisi statica del codice nell'**Elenco errori**, esaminare la colonna **Strumento**. Se il valore di Strumento corrisponde a uno degli assembly nell'analizzatore in **Esplora soluzioni**, ad esempio **Microsoft.CodeQuality.Analyzers**, la violazione proviene da un analizzatore di Roslyn. In caso contrario, la violazione proviene dall'analisi statica del codice.

![Colonna Strumento nell'Elenco errori](media/code-analysis-tool-in-error-list.png)

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

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Installare gli Analizzatori di Roslyn in Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usare gli analizzatori di Roslyn in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vedere anche

- [Domande frequenti sugli analizzatori](analyzers-faq.md)
- [Scrivere il proprio analizzatore di Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)