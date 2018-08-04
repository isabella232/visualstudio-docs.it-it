---
title: Analizzatori di Roslyn in Visual Studio
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3d5836c0522ef97a634f44799934aab2750b3a45
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511422"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Panoramica degli analizzatori .NET Compiler Platform

Visual Studio 2017 include un set predefinito di analizzatori .NET Compiler Platform che analizzano il codice c# o Visual Basic mentre si digita. È possibile installare altri analizzatori come estensione di Visual Studio o in base al progetto come pacchetto NuGet. Gli analizzatori è esaminiamo lo stile codice, la qualità del codice e manutenibilità, progettazione di codice e altri problemi.

Se vengono rilevate violazioni delle regole da un analizzatore, vengono segnalate sia nell'editor del codice come un *ondulata* sotto il codice che e nel **elenco errori**.

Molte regole di Analizzatore, o *diagnostics*, una o più associati *correzioni del codice* che è possibile applicare per correggere il problema. Gli strumenti di diagnostica dell'analizzatore sono integrate in Visual Studio hanno una correzione del codice associato. Le correzioni del codice vengono visualizzate nel menu insieme ad altri tipi di icona lampadina *azioni rapide*. Per informazioni su queste correzioni del codice, vedere [azioni rapide comuni](../ide/common-quick-actions.md).

![Violazione dell'analizzatore e correzione del codice azione rapida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analizzatori di Roslyn e analisi statica del codice

Gli analizzatori .NET compiler Platform ("Roslyn") sostituirà [analisi statica del codice](../code-quality/code-analysis-for-managed-code-overview.md) per codice gestito. Molte delle regole di analisi statica del codice sono già state riscritte come diagnostica analizzatore Roslyn.

Come violazioni delle regole di analisi statica del codice, le violazioni di Analizzatore Roslyn vengono visualizzati nei **elenco errori**. Inoltre, le violazioni di Analizzatore Roslyn visualizzati anche nell'editor del codice come *ondulate* sotto il codice che causa l'errore. Il colore dell'ondulata dipende il [impostazione di gravità](../code-quality/use-roslyn-analyzers.md#rule-severity) della regola. Lo screenshot seguente mostra tre violazioni&mdash;uno rosso, uno verde e un grigio:

![Linee ondulate nell'editor del codice](media/diagnostics-severity-colors.png)

Gli analizzatori di Roslyn analizzare il codice in fase di compilazione, ad esempio per analisi statica del codice se è abilitata, ma anche in tempo reale durante la digitazione. Gli analizzatori di Roslyn possono anche fornire analisi in fase di progettazione dei file di codice che non sono aperti nell'editor se si abilita [analisi della soluzione completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Errori in fase di compilazione e gli avvisi da analizzatori di Roslyn vengono visualizzati solo se gli analizzatori vengono installati come pacchetto NuGet.

Non solo eseguono gli analizzatori di Roslyn segnalano gli stessi tipi di problemi che esegue analisi statica del codice, ma semplificano le operazioni per la correzione di una o tutte le occorrenze della violazione in un progetto o di file. Queste azioni sono denominate *correzioni del codice*. Le correzioni del codice sono specifici dell'IDE; in Visual Studio, vengono implementate come [azioni rapide](../ide/quick-actions.md). Non tutti i dati diagnostici di Analizzatore hanno una correzione del codice associato.

> [!NOTE]
> L'opzione di menu **Analyze** > **Esegui analisi del codice** applica analisi del codice solo come statico. Inoltre, in un progetto **analisi del codice** pagina delle proprietà, il **Abilita analisi codice su compilazione** e **non visualizzare i risultati dal codice generato** caselle di controllo si applicano solo a analisi statica del codice. Non hanno alcun effetto su analizzatori di Roslyn.

Per distinguere le violazioni di analizzatori di Roslyn e analisi statica del codice nel **elenco errori**, esaminare le **strumento** colonna. Se il valore di strumento corrisponde a uno degli assembly nell'analizzatore **Esplora soluzioni**, ad esempio **Microsoft.CodeQuality.Analyzers**, la violazione proviene da un analizzatore Roslyn. In caso contrario, la violazione proviene dall'analisi statica del codice.

![Colonna strumento nell'elenco errori](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-versus-vsix-extension"></a>Pacchetto NuGet o estensione VSIX

.NET compiler Platform analizzatori possono essere installato al progetto tramite un pacchetto NuGet, o livello di Visual Studio come un'estensione di Visual Studio. Esistono alcune differenze di comportamento del tasto tra questi due metodi [installazione di analizzatori](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Ambito

Se si installano gli analizzatori come estensione di Visual Studio, si applicano a livello di soluzione, a tutte le istanze di Visual Studio. Se si installano gli analizzatori come pacchetto NuGet, che rappresenta il metodo preferito, si applicano solo al progetto in cui è stato installato il pacchetto NuGet. Negli ambienti di team, gli analizzatori installati come pacchetti NuGet sono inclusi nell'ambito del *tutti gli sviluppatori* che funzionano in tale progetto.

### <a name="build-errors"></a>Errori di compilazione

Per disporre di regole applicate in fase di compilazione, tra cui tramite la riga di comando o come parte di un'integrazione continua (CI) build, installare gli analizzatori come un pacchetto NuGet. Errori e avvisi di analizzatore non vengono visualizzati nel report del build se si installano gli analizzatori come un'estensione.

Lo screenshot seguente mostra l'output di compilazione da riga di comando di compilazione di un progetto che contiene una violazione della regola dell'analizzatore:

![Output di MSBuild con violazione della regola](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravità della regola

Non è possibile impostare la gravità di regole da analizzatori che sono stati installati come un'estensione di Visual Studio. Per configurare [gravità della regola](../code-quality/use-roslyn-analyzers.md#rule-severity), installare gli analizzatori come un pacchetto NuGet.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Installare gli analizzatori di Roslyn in Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usare gli analizzatori di Roslyn in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vedere anche

- [Azioni rapide in Visual Studio](../ide/quick-actions.md)
- [Scrivere il proprio analizzatore Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)