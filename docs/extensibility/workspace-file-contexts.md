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
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939190"
---
# <a name="workspace-file-contexts"></a>Contesti di file dell'area di lavoro

Tutte le informazioni dettagliate sui [Apri cartella](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) aree di lavoro vengono prodotte da "contesto provider di file" che implementano il <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interfaccia. Queste estensioni potrebbero cercare modelli nelle cartelle o file, leggere i file di MSBuild e makefile, rilevare le dipendenze dei pacchetti e così via per accumulare le informazioni critiche necessarie per definire un contesto di file. Un contesto di file per sé non esegue alcuna azione, ma piuttosto fornisce i dati che possa quindi utilizzare un'altra estensione.

Ciascuna <xref:Microsoft.VisualStudio.Workspace.FileContext> ha un `Guid` associato che identifica il tipo di dati esegue. Un'area di lavoro utilizza questo `Guid` in un secondo momento per abbinare con le estensioni che usano dati tramite il <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> proprietà. Un provider di contesto del file viene esportato con i metadati che identifica quale contesto di file `Guid`s può restituire i dati per.

Una volta definito, un contesto di file può essere associato a un numero qualsiasi di file o cartelle nell'area di lavoro. Un determinato file o cartella può essere associata a qualsiasi numero di contesti di file. Rappresenta una relazione molti-a-molti.

Gli scenari più comuni per i contesti di file sono correlati alla compilazione, debug e servizi di linguaggio. Per altre informazioni, vedere gli altri argomenti correlati a questi scenari.

## <a name="file-context-lifecycle"></a>Ciclo di vita del contesto file

Cicli di vita per un `FileContext` sono non deterministici. In qualsiasi momento, un componente può richiedere in modo asincrono per alcuni set di tipi di contesto. I provider che supportano un subset dei tipi di contesto richiesta verranno eseguite query. Il `IWorkspace` istanza agisce come intermediario tra i consumer e provider tramite il <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> (metodo). I consumer potrebbe essere un contesto di richiesta ed eseguire un'azione a breve termine basata sul contesto, mentre altri potrebbero richiedere un contesto e mantenere un riferimento lunga.

Potrebbero verificarsi modifiche ai file che causano un contesto di file a diventare obsoleto. Il provider può attivare un evento di `FileContext` per notificare i consumer degli aggiornamenti. Ad esempio, se viene fornito un contesto di compilazione per alcuni file, ma una modifica su disco invalida tale contesto, il producer originale può richiamare l'evento. Consumer ancora riferimento che `FileContext` può quindi rieseguire una query per un nuovo `FileContext`.

>[!NOTE]
>Non è disponibile alcun modello push agli utenti. Gli utenti non riceveranno una notifica di un provider di servizi nuovi `FileContext` dopo la richiesta.

## <a name="expensive-file-context-computations"></a>Calcoli di contesto file costosa

Contenuto del file durante la lettura dal disco può risultare costosi, specialmente quando un provider deve risolvere la relazione tra i file. Ad esempio, è possibile recuperare un provider di contesto del file del alcuni file di origine, ma il contesto del file è dipendente dai metadati da un file di progetto. L'analisi del file di progetto o la valutazione, tramite MSBuild è costosa. In alternativa, è possibile esportare l'estensione di un `IFileScanner` per creare `FileDataValue` dati durante l'indicizzazione dell'area di lavoro. Ora quando viene richiesto per i contesti di file, il `IFileContextProvider` possono effettuare rapidamente query per tali dati indicizzati. Per altre informazioni sull'indicizzazione, vedere la [dell'area di lavoro di indicizzazione](workspace-indexing.md) argomento.

>[!WARNING]
>Prestare attenzione in altri modi di `FileContext` può essere conveniente per il calcolo. Alcune interazioni dell'interfaccia utente sono sincroni e si basano su un volume elevato di `FileContext` richieste. Gli esempi includono aprendo una scheda dell'editor e un **Esplora soluzioni** menu di scelta rapida. Queste azioni apportare molte contesto di compilazione digitare le richieste.

## <a name="file-context-related-apis"></a>API correlate al contesto del file

- <xref:Microsoft.VisualStudio.Workspace.FileContext> contiene i dati e metadati.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> e <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> creare il contesto del file.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> Esporta un provider di contesto di file.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> viene utilizzato per gli utenti per ottenere i contesti di file.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> Definisce i tipi di contesto di compilazione che utilizzerà Apri cartella.

## <a name="file-context-actions"></a>Azioni di contesto file

Mentre un `FileContext` sé è solo i dati su alcuni file, un <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> è un modo per esprimere e agire su tali dati. `IFileContextAction` è flessibile nel relativo utilizzo. Due delle relative ai casi più comuni sono compilazione e debug.

## <a name="reporting-progress"></a>Creazione di report stato di avanzamento

Il <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> viene passato `IProgress<IFileContextActionProgressUpdate>`, ma l'argomento non deve essere utilizzato come quel tipo. `IFileContextActionProgressUpdate` è un'interfaccia vuota e richiamando `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` potrebbe generare `NotImplementedException`. Al contrario, il `IFileContextAction` deve eseguire il cast l'argomento a un altro tipo, se necessario per lo scenario.

Per informazioni sui tipi forniti da Visual Studio, vedere la documentazione del rispettivo scenario.

## <a name="file-context-action-related-apis"></a>API correlate all'azione contesto file

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> esegue un comportamento basato su un `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> Crea istanze di `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> il tipo esportato `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Il controllo dei file

Un'area di lavoro è in ascolto per le notifiche di modifica di file e fornisce il <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> tramite <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. File corrisponda a quella "ExcludedItems" non genera eventi di notifica di file. Una soglia compresa tra gli eventi viene usata per semplificare le operazioni di notifica e riduzione dei duplicati. Quando è necessario rispondere a una modifica del file, è necessario sottoscrivere questo servizio.

>[!TIP]
>Un'area di lavoro [servizio di indicizzazione](workspace-indexing.md) sottoscrive gli eventi di file per impostazione predefinita. File aggiunte e modifiche causerà rilevanti `IFileScanner`eventi s da richiamare per i nuovi dati per il file. L'eliminazione di file verranno rimossi i dati indicizzati. Non è necessario effettuare la sottoscrizione di `IFileScanner` nel servizio di controllo file.

## <a name="next-steps"></a>Passaggi successivi

* [L'indicizzazione](workspace-indexing.md) -area di lavoro di indicizzazione raccoglie e rende persistenti le informazioni sull'area di lavoro.
* [Le aree di lavoro](workspaces.md) -rivedere i concetti dell'area di lavoro e impostazioni di archiviazione.
