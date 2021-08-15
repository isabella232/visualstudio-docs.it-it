---
title: Indicizzazione dell'area di lavoro Visual Studio | Microsoft Docs
description: Informazioni sull'indicizzazione dell'area di lavoro, ovvero la raccolta e l'archiviazione permanente dei dati per supportare funzionalità IDE avanzate per un'area di lavoro Apri cartella.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 57342120ccd8a2305bad83eb237e41b28065a102919d8a99dee0dd827aff58cb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121234226"
---
# <a name="workspace-indexing"></a>Indicizzazione dell'area di lavoro

In una soluzione i sistemi di progetto sono responsabili di fornire funzionalità per la compilazione, il debug, la ricerca di simboli **GoTo** e altro ancora. Project sistemi operativi possono eseguire questa operazione perché comprendono la relazione e le funzionalità dei file all'interno di un progetto. [Un'area di lavoro](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Apri cartella richiede le stesse informazioni dettagliate per offrire funzionalità IDE avanzate. La raccolta e l'archiviazione permanente di questi dati è un processo denominato indicizzazione dell'area di lavoro. È possibile eseguire query su questi dati indicizzati tramite un set di API asincrone. Gli extender possono partecipare al processo di indicizzazione fornendo <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner> s che sanno come gestire determinati tipi di file.

## <a name="types-of-indexed-data"></a>Tipi di dati indicizzati

Esistono tre tipi di dati indicizzati. Si noti che il tipo previsto dagli scanner di file è diverso dal tipo deserializzato dall'indice.

|Dati|Tipo di file scanner|Tipo di risultato della query di indice|Tipi correlati|
|--|--|--|--|
|Riferimenti|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Simboli|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> deve essere usato invece di `IIndexWorkspaceService` per le query|
|Valori dei dati|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Esecuzione di query per i dati indicizzati

Sono disponibili due tipi asincroni per accedere ai dati persistenti. Il primo è tramite <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData> . Fornisce l'accesso di base ai dati e ai dati di un singolo file `FileReferenceResult` e memorizza nella cache i `FileDataResult` risultati. Il secondo è <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> l'oggetto che non usa la memorizzazione nella cache, ma consente altre funzionalità di query.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Partecipazione all'indicizzazione

L'indicizzazione dell'area di lavoro segue approssimativamente la sequenza seguente:

1. Individuazione e persistenza di file system entità nell'area di lavoro (solo all'analisi iniziale di apertura).
1. Per ogni file, al provider corrispondente con la priorità più alta viene richiesto di eseguire l'analisi di `FileReferenceInfo` .
1. Per ogni file, al provider corrispondente con la priorità più alta viene richiesto di eseguire l'analisi di `SymbolDefinition` .
1. Per ogni file, a tutti i provider viene richiesto `FileDataValue` di s.

Le estensioni possono esportare uno scanner `IWorkspaceProviderFactory<IFileScanner>` implementando ed esportando il tipo con <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute> . `SupportedTypes`L'argomento dell'attributo deve essere uno o più valori di <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants> . Per uno scanner di esempio, vedere [l'esempio](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)di VS SDK .

> [!WARNING]
> Non esportare uno scanner di file che supporta il `FileScannerTypeConstants.FileScannerContentType` tipo . Viene usato solo per scopi interni Microsoft.

In situazioni avanzate, un'estensione potrebbe supportare dinamicamente un set arbitrario di tipi di file. Anziché esportare `IWorkspaceProviderFactory<IFileScanner>` MEF, un'estensione può esportare `IWorkspaceProviderFactory<IFileScannerProvider>` . All'inizio dell'indicizzazione, verrà importato, creato un'istanza di questo tipo factory e verrà <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> richiamato il metodo . `IFileScanner` Le istanze che supportano qualsiasi valore da `FileScannerTpeConstants` verranno rispettate, non solo i simboli.

## <a name="next-steps"></a>Passaggi successivi

* [Aree di lavoro e servizi linguistici:](workspace-language-services.md) informazioni su come integrare i servizi linguistici in un'area di lavoro Apri cartella.
* [Compilazione dell'area](workspace-build.md) di lavoro: Open Folder supporta sistemi di compilazione come MSBuild e makefile.