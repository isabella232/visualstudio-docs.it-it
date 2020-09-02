---
title: Compilazione dell'area di lavoro in Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 82660ee772280563b91830aaf1a18da0bc742b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62553328"
---
# <a name="workspace-build"></a>Compilazione dell'area di lavoro

Per il supporto della compilazione in scenari di [cartelle aperte](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) è necessario che un dispositivo Extender fornisca dati di contesto [indicizzato](workspace-indexing.md) e [file](workspace-file-contexts.md) per l' [area di lavoro](workspaces.md), nonché l'azione di compilazione da eseguire.

Di seguito è riportata una descrizione delle funzionalità necessarie per l'estensione.

## <a name="build-file-context"></a>Contesto del file di compilazione

- Factory del provider
  - `ExportFileContextProviderAttribute` attributo con `supportedContextTypeGuids` come tutte le `string` costanti applicabili da `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Provider di contesto file
    - Restituisce un oggetto `FileContext` per ogni operazione di compilazione e la configurazione supportata
      - `contextType` da <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementa <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> con la `Configuration` proprietà come configurazione della compilazione (ad esempio `"Debug|x86"` , `"ret"` o `null` se non applicabile). In alternativa, utilizzare un'istanza di <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext> . Il valore di configurazione **deve** corrispondere alla configurazione del valore dei dati del file indicizzato.

## <a name="indexed-build-file-data-value"></a>Valore dati del file di compilazione indicizzato

- Factory del provider
  - `ExportFileScannerAttribute` attributo con `IReadOnlyCollection<FileDataValue>` come tipo supportato
  - Implementa `IWorkspaceProviderFactory<IFileScanner>`
- Scanner file su `ScanContentAsync<T>`
  - Restituisce i dati quando `FileScannerTypeConstants.FileDataValuesType` è l'argomento di tipo
  - Restituisce un valore di dati di file per ogni configurazione costruita con:
    - `type` come `BuildConfigurationContext.ContextTypeGuid`
    - `context` come configurazione della build (ad esempio `"Debug|x86"` , `"ret"` o `null` se non applicabile). Questo valore **deve** corrispondere alla configurazione del contesto del file.

## <a name="build-file-context-action"></a>Azione contesto file di compilazione

- Factory del provider
  - `ExportFileContextActionProvider` attributo con `supportedContextTypeGuids` come tutte le `string` costanti applicabili da `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Provider di azioni su `IFileContextActionProvider.GetActionsAsync`
  - Restituisce un oggetto `IFileContextAction` che corrisponde al `FileContext.ContextType` valore specificato
- Azione contesto file
  - Implementa `IFileContextAction` e <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` Restituisce la proprietà `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` per la `0x1000` compilazione, `0x1010` per la ricompilazione o `0x1020` per la pulizia

>[!NOTE]
>Poiché l'oggetto `FileDataValue` deve essere indicizzato, ci sarà una certa quantità di tempo tra l'apertura dell'area di lavoro e il punto in cui il file viene analizzato per la funzionalità di compilazione completa. Il ritardo verrà visualizzato alla prima apertura di una cartella perché non è presente alcun indice precedentemente memorizzato nella cache.

## <a name="reporting-messages-from-a-build"></a>Segnalazione di messaggi da una compilazione

La compilazione può presentare messaggi di informazioni, avvisi e messaggi di errore agli utenti in uno dei due modi. Il modo più semplice consiste nell'usare <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> e fornire un oggetto <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> , come segue:

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

`BuildMessage.Type` e `BuildMessage.LogMessage` controllano il comportamento di in cui le informazioni vengono presentate all'utente. Qualsiasi `BuildMessage.TaskType` valore diverso da `None` produrrà una voce di **Elenco errori** con i dettagli specificati. `LogMessage` verrà sempre restituito nel riquadro **Compila** della finestra degli strumenti di **output** .

In alternativa, le estensioni possono interagire direttamente con il **Elenco errori** o il riquadro di **compilazione** . Un bug è presente nelle versioni precedenti a Visual Studio 2017 versione 15,7 in cui l' `pszProjectUniqueName` argomento di <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> viene ignorato.

>[!WARNING]
>I chiamanti di `IFileContextAction.ExecuteAsync` possono fornire implementazioni sottostanti arbitrarie per l' `IProgress<IFileContextActionProgressUpdate>` argomento. Non richiamare mai `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` direttamente. Attualmente non sono disponibili linee guida generali per l'utilizzo di questo argomento, ma queste linee guida sono soggette a modifiche.

## <a name="build-related-apis"></a>API correlate alla compilazione

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> fornisce i dettagli di configurazione della compilazione.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> Mostra <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> gli utenti.

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.json e launch.vs.json

Per informazioni sulla creazione di un tasks.vs.jso launch.vs.jssu file, vedere [personalizzare le attività di compilazione e debug](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Passaggi successivi

* [Protocollo server di linguaggio](language-server-protocol.md) : informazioni su come integrare i server di linguaggio in Visual Studio.