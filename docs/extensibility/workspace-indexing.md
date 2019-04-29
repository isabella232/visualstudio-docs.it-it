---
title: Area di lavoro di indicizzazione in Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 9bf7df777d27003fa5763debc772a8804ec28ef5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952706"
---
# <a name="workspace-indexing"></a>Area di lavoro di indicizzazione

In una soluzione, sono responsabili di fornire funzionalità per la compilazione per i sistemi di progetto, eseguire il debug, **GoTo** la ricerca di simboli e altro ancora. I sistemi di progetto possono eseguire queste operazioni perché comprendono la relazione e la funzionalità di file all'interno di un progetto. Un' [Apri cartella](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) dell'area di lavoro richiede le stesse informazioni per fornire anche numerose funzionalità dell'IDE. La raccolta e l'archiviazione permanente dei dati è un processo denominato l'indicizzazione dell'area di lavoro. I dati indicizzati è possibile eseguire query tramite un set di API asincrone. Dispositivi Extender possono far parte del processo di indicizzazione, fornendo <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>che sa come gestire determinati tipi di file.

## <a name="types-of-indexed-data"></a>Tipi di dati indicizzati

Esistono tre tipi di dati che vengono indicizzati. Si noti il tipo previsto dagli scanner di file è diverso dal tipo deserializzato dall'indice.

|Dati|Tipo di scanner di file|Tipo di risultato di query dell'indice|Tipi correlati|
|--|--|--|--|
|Riferimenti|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Simboli|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> deve essere usato al posto della `IIndexWorkspaceService` per le query|
|Valori dei dati|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>L'esecuzione di query per i dati indicizzati

Esistono due tipi asincroni disponibili per accedere ai dati persistenti. Il primo è tramite <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Fornisce accesso a un singolo file di base `FileReferenceResult` e `FileDataResult` dati e lo memorizza nella cache i risultati. Il secondo è il <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> che non usa la memorizzazione nella cache, ma consente di altre funzionalità per eseguire query.

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

## <a name="participating-in-indexing"></a>Che fanno parte di indicizzazione

Area di lavoro di indicizzazione segue approssimativamente la sequenza seguente:

1. Individuazione e la persistenza delle entità di sistema di file nell'area di lavoro (solo in analisi di apertura iniziale).
1. Per ogni file, viene richiesto il provider di corrispondenza con la priorità più alta a cercare `FileReferenceInfo`s.
1. Per ogni file, viene richiesto il provider di corrispondenza con la priorità più alta a cercare `SymbolDefinition`s.
1. Per ogni file, vengono richiesti tutti i provider `FileDataValue`s.

Le estensioni è possono esportare uno scanner implementando `IWorkspaceProviderFactory<IFileScanner>` ed esportare il tipo con <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. Il `SupportedTypes` argomento di attributo deve essere uno o più valori da <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Per uno scanner di esempio, vedere il SDK di Visual Studio [esempio](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Non si esporta un'analisi di file che supporta il `FileScannerTypeConstants.FileScannerContentType` tipo. Viene usato Microsoft solo per scopi interni.

In situazioni avanzate, un'estensione potrebbe supportare in modo dinamico un set arbitrario di tipi di file. Invece di esportazione MEF `IWorkspaceProviderFactory<IFileScanner>`, un'estensione può esportare `IWorkspaceProviderFactory<IFileScannerProvider>`. Quando l'indicizzazione viene avviata, questo tipo di factory verrà importato, crea un'istanza e hanno relativo <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> metodo richiamato. `IFileScanner` le istanze che supportano qualsiasi valore compreso `FileScannerTpeConstants` verrà rispettata, non solo i simboli.

## <a name="next-steps"></a>Passaggi successivi

* [Aree di lavoro e servizi di linguaggio](workspace-language-services.md) -informazioni su come integrare servizi di linguaggio in un'area di lavoro di Apri cartella.
* [Compilazione dell'area di lavoro](workspace-build.md) -Apri cartella supporta i sistemi, ad esempio makefile e MSBuild di compilazione.