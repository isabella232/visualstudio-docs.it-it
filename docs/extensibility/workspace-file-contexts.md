---
title: Contesti di file dell'area di lavoro Visual Studio | Microsoft Docs
description: Informazioni sui provider di contesto di file che implementano l'interfaccia IFileContextProvider per supportare informazioni dettagliate sulle aree di lavoro Apri cartella.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 92658912e6910f21c6e79f779dff66b6c8b85a04b55f138a0971903789d4c8a2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121374585"
---
# <a name="workspace-file-contexts"></a>Contesti di file dell'area di lavoro

Tutte le informazioni dettagliate [sulle aree di lavoro](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Apri cartella vengono prodotte dai "provider di contesto file" che implementano l'interfaccia <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> . Queste estensioni possono cercare modelli in cartelle o file, leggere file MSBuild e makefile, rilevare le dipendenze dei pacchetti e così via per accumulare le informazioni dettagliate necessarie per definire un contesto di file. Un contesto di file di per sé non esegue alcuna azione, ma fornisce invece dati su cui un'altra estensione può quindi agire.

A <xref:Microsoft.VisualStudio.Workspace.FileContext> ogni oggetto è associato un oggetto che identifica il tipo di dati che `Guid` contiene. Un'area di lavoro usa questa funzionalità in un secondo momento per `Guid` associarla alle estensioni che utilizzano i dati tramite la <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> proprietà . Un provider di contesto di file viene esportato con metadati che identificano il contesto di file per cui `Guid` può produrre dati.

Una volta definito, un contesto di file può essere associato a un numero qualsiasi di file o cartelle nell'area di lavoro. Un determinato file o cartella può essere associato a un numero qualsiasi di contesti di file. Si tratta di una relazione molti-a-molti.

Gli scenari più comuni per i contesti di file sono correlati ai servizi di compilazione, debug e linguaggio. Per altre informazioni, vedere gli altri argomenti correlati a questi scenari.

## <a name="file-context-lifecycle"></a>Ciclo di vita del contesto di file

I cicli di vita `FileContext` per un sono non deterministici. In qualsiasi momento, un componente può richiedere in modo asincrono alcuni set di tipi di contesto. Verranno sottoposti a query i provider che supportano alcuni subset dei tipi di contesto della richiesta. `IWorkspace`L'istanza funge da intermediario tra il consumer e i provider tramite il <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> metodo . I consumer possono richiedere un contesto ed eseguire un'azione a breve termine in base al contesto, mentre altri potrebbero richiedere un contesto e mantenere un riferimento di lunga durata.

È possibile che si apportare modifiche ai file che causano l'obsoleto di un contesto di file. Il provider può genera un evento su per `FileContext` notificare agli utenti gli aggiornamenti. Ad esempio, se viene fornito un contesto di compilazione per un file ma una modifica su disco invalida tale contesto, il producer originale può richiamare l'evento . Tutti i consumer che fanno ancora riferimento a `FileContext` che possono quindi rieseguire query per un nuovo `FileContext` oggetto .

>[!NOTE]
>Non esiste alcun modello push per i consumer. I consumer non verranno informati del nuovo provider dopo `FileContext` la richiesta.

## <a name="expensive-file-context-computations"></a>Calcoli costosi del contesto di file

La lettura del contenuto dei file dal disco può risultare costosa, soprattutto quando un provider deve risolvere la relazione tra i file. Ad esempio, è possibile eseguire query su un provider per il contesto del file di origine, ma il contesto del file dipende dai metadati di un file di progetto. L'analisi del file di progetto o la valutazione con MSBuild è costosa. L'estensione può invece esportare un oggetto per `IFileScanner` creare dati durante l'indicizzazione `FileDataValue` dell'area di lavoro. A questo punto, quando viene richiesto per i contesti di file, `IFileContextProvider` è possibile eseguire rapidamente una query per i dati indicizzati. Per altre informazioni sull'indicizzazione, vedere l'argomento [Indicizzazione dell'area di](workspace-indexing.md) lavoro.

>[!WARNING]
>Fare attenzione ad altri modi in `FileContext` cui l'utente potrebbe essere costoso da calcolare. Alcune interazioni dell'interfaccia utente sono sincrone e si basano su un volume elevato di `FileContext` richieste. Alcuni esempi includono l'apertura di una scheda dell'editor e Esplora soluzioni menu **di scelta** rapida. Queste azioni effettuano molte richieste di tipo di contesto di compilazione.

## <a name="file-context-related-apis"></a>API correlate al contesto di file

- <xref:Microsoft.VisualStudio.Workspace.FileContext> contiene dati e metadati.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> e <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> creare il contesto del file.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> esporta un provider di contesto di file.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> viene usato per i consumer per ottenere contesti di file.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> definisce i tipi di contesto di compilazione che verranno utilizzati da Open Folder.

## <a name="file-context-actions"></a>Azioni del contesto di file

Anche se un oggetto è solo dati su alcuni file, un è un modo per esprimere e `FileContext` <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> agire su tale dati. `IFileContextAction` è flessibile nell'utilizzo. Due dei casi più comuni sono la compilazione e il debug.

## <a name="reporting-progress"></a>Segnalazione dello stato

Il <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> metodo viene passato , ma `IProgress<IFileContextActionProgressUpdate>` l'argomento non deve essere usato come tipo. `IFileContextActionProgressUpdate` è un'interfaccia vuota e la chiamata potrebbe `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` generare `NotImplementedException` . Deve invece `IFileContextAction` eseguire il cast dell'argomento a un altro tipo in base alle esigenze per lo scenario.

Per informazioni sui tipi forniti da Visual Studio, vedere la documentazione del rispettivo scenario.

## <a name="file-context-action-related-apis"></a>API correlate all'azione del contesto di file

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> esegue un comportamento basato su un oggetto `FileContext` .
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> crea istanze di `IFileContextAction` .
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> esporta il tipo `IWorkspaceProviderFactory<IFileContextActionProvider>` .

## <a name="file-watching"></a>Controllo dei file

Un'area di lavoro è in ascolto delle notifiche di modifica dei file e fornisce <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> tramite <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . I file che corrispondono all'impostazione "ExcludedItems" non produrranno eventi di notifica dei file. Una soglia tra gli eventi viene usata per la semplificazione delle notifiche e la riduzione dei duplicati. Quando è necessario reagire a una modifica del file, è necessario sottoscrivere questo servizio.

>[!TIP]
>Il servizio di indicizzazione di [un'area di lavoro](workspace-indexing.md) sottoscrive gli eventi dei file per impostazione predefinita. Le aggiunte e le modifiche ai file causeranno la chiamata degli eventi s pertinenti `IFileScanner` per i nuovi dati per tale file. Le eliminazioni di file rimuoveranno i dati indicizzati. Non è necessario sottoscrivere il `IFileScanner` servizio File Watcher.

## <a name="next-steps"></a>Passaggi successivi

* [Indicizzazione: l'indicizzazione](workspace-indexing.md) dell'area di lavoro raccoglie e rende persistenti le informazioni sull'area di lavoro.
* [Aree di lavoro: esaminare](workspaces.md) i concetti e le impostazioni dell'archiviazione dell'area di lavoro.
