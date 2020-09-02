---
title: Contesti di file dell'area di lavoro in Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 36f986db6f2c7b483b46060e1f514acc8dd9e758
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952814"
---
# <a name="workspace-file-contexts"></a>Contesti di file dell'area di lavoro

Tutte le informazioni sulle aree di lavoro [Apri cartella](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) vengono generate da "provider di contesto file" che implementano l' <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interfaccia. Queste estensioni possono cercare i modelli in cartelle o file, leggere file e Makefile di MSBuild, rilevare le dipendenze dei pacchetti e così via per accumulare le informazioni necessarie per definire un contesto di file. Un contesto di file non esegue alcuna azione, bensì fornisce dati su cui può agire un'altra estensione.

A ciascuna <xref:Microsoft.VisualStudio.Workspace.FileContext> è `Guid` associato un oggetto che identifica il tipo di dati che contiene. Un'area di lavoro viene usata `Guid` in un secondo momento per trovare una corrispondenza con le estensioni che utilizzano i dati tramite la <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> Proprietà. Un provider di contesto di file viene esportato con i metadati che identificano il contesto del file per il quale `Guid` può produrre dati.

Una volta definito, un contesto di file può essere associato a un numero qualsiasi di file o cartelle nell'area di lavoro. Un file o una cartella specifica può essere associata a un numero qualsiasi di contesti di file. Si tratta di una relazione molti-a-molti.

Gli scenari più comuni per i contesti di file sono correlati ai servizi di compilazione, debug e linguaggio. Per ulteriori informazioni, vedere gli altri argomenti correlati a questi scenari.

## <a name="file-context-lifecycle"></a>Ciclo di vita del contesto del file

I cicli di vita di un oggetto `FileContext` sono non deterministici. In qualsiasi momento, un componente può richiedere in modo asincrono un set di tipi di contesto. I provider che supportano alcuni subset dei tipi di contesto della richiesta verranno sottoposti a query. L' `IWorkspace` istanza funge da intermediario tra il consumer e i provider tramite il <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> metodo. I consumer potrebbero richiedere un contesto ed eseguire alcune azioni a breve termine in base al contesto, mentre altri potrebbero richiedere un contesto e mantenere un riferimento di lunga durata.

È possibile che vengano apportate modifiche ai file che fanno sì che un contesto di file diventi obsoleto. Il provider può generare un evento in `FileContext` per notificare agli utenti gli aggiornamenti. Se, ad esempio, viene fornito un contesto di compilazione per un file ma una modifica su disco invalida tale contesto, il producer originale può richiamare l'evento. Tutti i consumer che fanno riferimento a `FileContext` possono quindi eseguire una nuova query per un nuovo `FileContext` .

>[!NOTE]
>Nessun modello push per i consumer. Gli utenti non riceveranno una notifica del nuovo provider `FileContext` dopo la richiesta.

## <a name="expensive-file-context-computations"></a>Calcoli costosi del contesto del file

La lettura del contenuto del file dal disco può essere costosa, specialmente quando un provider deve risolvere la relazione tra i file. Ad esempio, è possibile che venga eseguita una query su un provider per il contesto del file di un file di origine, ma che il contesto del file dipenda dai metadati di un file di progetto. L'analisi del file di progetto o la relativa valutazione con MSBuild è un'operazione costosa. L'estensione può invece esportare un `IFileScanner` per creare `FileDataValue` dati durante l'indicizzazione dell'area di lavoro. A questo punto, quando vengono richiesti i contesti di file, il `IFileContextProvider` può eseguire rapidamente query per i dati indicizzati. Per ulteriori informazioni sull'indicizzazione, vedere l'argomento [indicizzazione dell'area di lavoro](workspace-indexing.md) .

>[!WARNING]
>Prestare attenzione ad altri modi `FileContext` in cui il calcolo potrebbe essere costoso. Alcune interazioni dell'interfaccia utente sono sincrone e si basano su un volume elevato di `FileContext` richieste. Gli esempi includono l'apertura di una scheda Editor e l'apertura di un menu di scelta rapida **Esplora soluzioni** . Queste azioni comportano molte richieste del tipo di contesto di compilazione.

## <a name="file-context-related-apis"></a>API correlate al contesto del file

- <xref:Microsoft.VisualStudio.Workspace.FileContext> include i dati e i metadati.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> e <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> creare il contesto del file.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> Esporta un provider del contesto del file.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> viene usato per i consumer per ottenere i contesti di file.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> definisce i tipi di contesto di compilazione che la cartella di apertura utilizzerà.

## <a name="file-context-actions"></a>Azioni di contesto file

Mentre un `FileContext` solo è costituito da dati su alcuni file, un <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> è un modo per esprimere e agire su tali dati. `IFileContextAction` è flessibile nell'utilizzo. Due dei casi più comuni sono la compilazione e il debug.

## <a name="reporting-progress"></a>Segnalazione dello stato

Il <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> metodo viene passato `IProgress<IFileContextActionProgressUpdate>` , ma l'argomento non deve essere usato come quel tipo. `IFileContextActionProgressUpdate` è un'interfaccia vuota e il richiamo `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` può generare `NotImplementedException` . Al contrario, `IFileContextAction` deve eseguire il cast dell'argomento a un altro tipo in modo necessario per lo scenario.

Per informazioni sui tipi forniti da Visual Studio, vedere la documentazione dello scenario corrispondente.

## <a name="file-context-action-related-apis"></a>API correlate all'azione del contesto file

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> esegue un comportamento in base a un oggetto `FileContext` .
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> Crea istanze di `IFileContextAction` .
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> Esporta il tipo `IWorkspaceProviderFactory<IFileContextActionProvider>` .

## <a name="file-watching"></a>Osservazione di file

Un'area di lavoro è in ascolto delle notifiche di modifica dei file e fornisce la <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> via <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . I file che corrispondono all'impostazione "ExcludedItems" non generano eventi di notifica dei file. Una soglia tra gli eventi viene utilizzata per semplificare la notifica e la riduzione dei duplicati. Per rispondere alla modifica di un file, è necessario sottoscrivere il servizio.

>[!TIP]
>Il servizio di [indicizzazione](workspace-indexing.md) di un'area di lavoro sottoscrive gli eventi di file per impostazione predefinita. Le aggiunte e le modifiche ai file causeranno `IFileScanner` la richiamata degli eventi rilevanti per i nuovi dati per tale file. Le eliminazioni di file rimuoveranno i dati indicizzati. Non è necessario sottoscrivere il `IFileScanner` servizio monitoraggio file.

## <a name="next-steps"></a>Passaggi successivi

* [Indicizzazione](workspace-indexing.md) : l'indicizzazione dell'area di lavoro raccoglie e rende permanente le informazioni sull'area di lavoro.
* [Aree di lavoro](workspaces.md) : esaminare i concetti e l'archiviazione delle impostazioni dell'area di lavoro.
