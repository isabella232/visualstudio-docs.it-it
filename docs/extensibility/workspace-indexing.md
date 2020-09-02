---
title: Indicizzazione dell'area di lavoro in Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 9bf7df777d27003fa5763debc772a8804ec28ef5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952706"
---
# <a name="workspace-indexing"></a>Indicizzazione area di lavoro

In una soluzione, i sistemi di progetto sono responsabili di fornire funzionalità per compilazione, debug, **Vai** alla ricerca dei simboli e altro ancora. I sistemi di progetto possono eseguire questa operazione perché conoscono la relazione e le funzionalità dei file all'interno di un progetto. Un'area di lavoro [Apri cartella](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) necessita delle stesse informazioni per fornire funzionalità IDE avanzate. La raccolta e l'archiviazione permanente di questi dati sono un processo denominato indicizzazione dell'area di lavoro. È possibile eseguire query su questi dati indicizzati tramite un set di API asincrone. I dispositivi Extender possono partecipare al processo di indicizzazione, fornendo ai <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner> che sanno come gestire alcuni tipi di file.

## <a name="types-of-indexed-data"></a>Tipi di dati indicizzati

Sono disponibili tre tipi di dati indicizzati. Si noti che il tipo previsto da scanner di file è diverso dal tipo deserializzato dall'indice.

|Dati|Tipo di scanner di file|Tipo di risultato query indice|Tipi correlati|
|--|--|--|--|
|Riferimenti|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Simboli|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> deve essere usato al posto di `IIndexWorkspaceService` per le query|
|Valori dei dati|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Esecuzione di query per i dati indicizzati

Sono disponibili due tipi asincroni per accedere ai dati salvati in modo permanente. Il primo è tramite <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData> . Fornisce l'accesso di base a un singolo file `FileReferenceResult` e ai `FileDataResult` dati e memorizza nella cache i risultati. Il secondo è il <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> che non usa la memorizzazione nella cache, ma consente di eseguire più query sulle funzionalità.

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

1. Individuazione e persistenza delle entità file system nell'area di lavoro (solo per l'analisi di apertura iniziale).
1. Per ogni file, viene richiesto al provider corrispondente con la priorità più alta di eseguire l'analisi di `FileReferenceInfo` .
1. Per ogni file, viene richiesto al provider corrispondente con la priorità più alta di eseguire l'analisi di `SymbolDefinition` .
1. Per ogni file, vengono richiesti tutti i provider `FileDataValue` .

Le estensioni possono esportare uno scanner implementando `IWorkspaceProviderFactory<IFileScanner>` ed esportando il tipo con <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute> . L' `SupportedTypes` argomento dell'attributo deve essere uno o più valori di <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants> . Per un esempio di scanner, vedere l' [esempio](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)di Visual Studio SDK.

> [!WARNING]
> Non esportare uno scanner di file che supporta il `FileScannerTypeConstants.FileScannerContentType` tipo. Viene utilizzato solo per scopi interni Microsoft.

In situazioni avanzate, un'estensione può supportare in modo dinamico un set arbitrario di tipi di file. Anziché l'esportazione MEF `IWorkspaceProviderFactory<IFileScanner>` , un'estensione può essere esportata `IWorkspaceProviderFactory<IFileScannerProvider>` . Quando inizia l'indicizzazione, questo tipo di factory viene importato, ne viene creata un'istanza e ne viene <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> richiamato il metodo. `IFileScanner` le istanze che supportano qualsiasi valore da `FileScannerTpeConstants` verranno rispettate, non solo i simboli.

## <a name="next-steps"></a>Passaggi successivi

* [Aree di lavoro e servizi di linguaggio](workspace-language-services.md) : informazioni su come integrare i servizi di linguaggio in un'area di lavoro Apri cartella.
* [Compilazione area di lavoro](workspace-build.md) : la cartella Apri supporta sistemi di compilazione quali MSBuild e Makefile.