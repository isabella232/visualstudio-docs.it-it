---
title: Area di lavoro di compilazione in Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 82660ee772280563b91830aaf1a18da0bc742b28
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951228"
---
# <a name="workspace-build"></a>Compilazione dell'area di lavoro

Supporto per la compilazione [Apri cartella](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) scenari richiede un extender per fornire [indicizzata](workspace-indexing.md) e [contesto file](workspace-file-contexts.md) i dati per il [dell'area di lavoro](workspaces.md), come nonché l'azione di compilazione da eseguire.

Di seguito è una struttura di ciò che sarà necessario l'estensione.

## <a name="build-file-context"></a>Contesto del file di compilazione

- Factory del provider
  - `ExportFileContextProviderAttribute` attributo con `supportedContextTypeGuids` modo di tutte le applicabili `string` costanti da `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Provider di contesto file
    - Restituire un `FileContext` per ogni compilazione operazione e la configurazione supportata
      - `contextType` Da <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementa <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> con il `Configuration` proprietà come la configurazione della build (ad esempio `"Debug|x86"`, `"ret"`, o `null` se non applicabile). In alternativa, usare un'istanza di <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. Il valore di configurazione **necessario** corrispondono alla configurazione dal valore di dati di file indicizzati.

## <a name="indexed-build-file-data-value"></a>Valore dei dati di file indicizzati compilazione

- Factory del provider
  - `ExportFileScannerAttribute` attributo con `IReadOnlyCollection<FileDataValue>` come un tipo supportato
  - Implementa `IWorkspaceProviderFactory<IFileScanner>`
- Analisi dei file in `ScanContentAsync<T>`
  - Restituisce i dati quando `FileScannerTypeConstants.FileDataValuesType` è costituito dall'argomento di tipo
  - Restituisce un valore di dati di file per ogni configurazione costruito con:
    - `type` come `BuildConfigurationContext.ContextTypeGuid`
    - `context` come la configurazione di compilazione (ad esempio `"Debug|x86"`, `"ret"`, o `null` se non applicabile). Questo valore **necessario** corrispondono alla configurazione dal contesto del file.

## <a name="build-file-context-action"></a>Azione contesto file di compilazione

- Factory del provider
  - `ExportFileContextActionProvider` attributo con `supportedContextTypeGuids` modo di tutte le applicabili `string` costanti da `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Provider di azioni su `IFileContextActionProvider.GetActionsAsync`
  - Restituisce un `IFileContextAction` che corrisponde al determinato `FileContext.ContextType` valore
- Azione contesto file
  - Implementa `IFileContextAction` e <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` restituisce proprietà `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` viene `0x1000` per la compilazione, `0x1010` per la ricompilazione, o `0x1020` per pulire

>[!NOTE]
>Poiché il `FileDataValue` devono essere indicizzati, sarà presente un intervallo di tempo tra aprendo l'area di lavoro e il punto in corrispondenza del quale il file viene analizzato per la funzionalità di compilazione completa. Il ritardo sarà presenti di prima apertura di una cartella, perché nessun indice precedentemente memorizzata nella cache.

## <a name="reporting-messages-from-a-build"></a>Creazione di report dei messaggi da una compilazione

La compilazione può rendere visibili i messaggi di errore, avviso e informazioni agli utenti uno dei due modi. La più semplice consiste nell'utilizzare il <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> e fornire un <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, come illustrato di seguito:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` e `BuildMessage.LogMessage` controllano il comportamento di in cui vengono visualizzate informazioni all'utente. Eventuali `BuildMessage.TaskType` valore diverso da `None` produrrà un' **elenco errori** voce con i dettagli specificati. `LogMessage` verranno sempre restituiti nel **compilare** riquadro della finestra di **Output** finestra degli strumenti.

In alternativa, le estensioni possono interagire direttamente con il **elenco errori** oppure **compilazione** riquadro. Esiste un bug nelle versioni precedenti a Visual Studio 2017 versione 15.7 in cui il `pszProjectUniqueName` argomento di <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> viene ignorato.

>[!WARNING]
>I chiamanti del `IFileContextAction.ExecuteAsync` possono fornire le implementazioni sottostanti arbitrari per il `IProgress<IFileContextActionProgressUpdate>` argomento. Evitare chiamate `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` direttamente. Non esistono attualmente alcun indicazioni generali per l'uso di questo argomento, ma queste linee guida sono soggette a modifiche.

## <a name="build-related-apis"></a>API correlate alle build

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> Fornisce i dettagli di configurazione di compilazione.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> Mostra <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>s agli utenti.

## <a name="tasksvsjson-and-launchvsjson"></a>Tasks e Launch

Per informazioni sulla creazione di un file Tasks o Launch, vedere [personalizzare la compilazione e il debug di attività](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Passaggi successivi

* [Protocollo di Server di linguaggio](language-server-protocol.md) -informazioni su come integrare i server di linguaggio in Visual Studio.