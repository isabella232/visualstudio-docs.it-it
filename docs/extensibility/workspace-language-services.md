---
title: Le aree di lavoro e i servizi di linguaggio in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8631ffea-83c8-4fd4-a01e-c59772e89c84
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: be9fb8c1e3ae363898e0438bdd1ec34c9fd23727
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735458"
---
# <a name="workspaces-and-language-services"></a>Aree di lavoro e servizi di linguaggio

I servizi di linguaggio possono fornire [Apri cartella](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) agli utenti le stesse funzionalità di linguaggio avanzato vengono usati per quando si lavora con progetti e soluzioni. Un servizio di linguaggio potrebbe attivarsi in base all'estensione di file o il contenuto di un documento aperto anche se questo servizio di linguaggio "loose file" è limitato per l'evidenziazione della sintassi. Sono necessarie informazioni aggiuntive per offrire un'esperienza più completa durante la modifica/revisione di codice sorgente. Ogni servizio di linguaggio ha un'API per l'inizializzazione con i dati contestuali extra per un documento. È in genere gestita da un sistema di progetto, è strettamente collegato al servizio di linguaggio e al sistema di compilazione.

## <a name="initialization"></a>Inizializzazione

In un [dell'area di lavoro](workspaces.md), servizi di linguaggio vengono inizializzati da un <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> punto di estensione che specializza solo in tale servizio di linguaggio e dispone di alcuna informazione di compilazione di creazione. In questo modo, un proprietario del servizio di linguaggio può gestire una singola cartella Apri estensione indipendentemente dal modo in cui molti modelli esiste all'interno di cartelle e file per l'esecuzione delle loro del compilatore durante la compilazione (ad esempio MSBuild, makefile e così via). Quando i file da cui è stato creato un contesto di file vengono modificati sul disco e il contesto del file viene aggiornato, il provider del servizio di linguaggio viene informato del set aggiornato di contesti di file. Il provider del servizio di linguaggio può quindi aggiornare il modello.

Quando un documento viene aperto nell'editor, Visual Studio considera solo linguaggio i provider di servizi che richiedono i tipi di contesto di file per cui è possibile trovare un provider di contesto di file corrispondente. Quindi passa i contesti dei file dai provider corrispondenti al provider del servizio di lingua selezionata tramite `ILanguageServiceProvider.InitializeAsync`. Il provider del servizio di linguaggio modo che i dati di contesto di file sono un dettaglio di implementazione del provider di servizi di linguaggio, ma l'esperienza utente previsto è un servizio di linguaggio più completo per tale documento aperto.

## <a name="using-ilanguageserviceprovider"></a>Usando ILanguageServiceProvider

Il servizio di linguaggio riceverà una notifica quando viene creato un contesto di file con un `ContextType` che corrisponde a una del `SupportedContextTypes` valori del server di linguaggio export (attributo).

Per supportare un servizio di linguaggio, un'estensione sarà necessario:

- Un valore univoco `Guid`. Verrà usato per `SupportedContextTypes` argomenti dell'attributo e in un `FileContext` oggetto.
- Contesto del file del linguaggio
  - Factory del provider
    - `ExportFileContextProviderAttribute` generato in modo univoco l'attributo con il codice precedente `Guid` in `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementazione del provider `IFileContextProvider.GetContextsForFileAsync`
    - Creare una nuova `FileContext` con il `contextType` argomento del costruttore come generato in modo univoco `Guid`
    - Usare il `Context` proprietà del `FileContext` per fornire dati aggiuntivi per il `ILanguageServiceProvider`
- servizio di linguaggio
  - Factory del provider
    - `ExportLanguageServiceProvider` generato in modo univoco l'attributo con il codice precedente `Guid` in `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Provider
    - Implementa `ILanguageServiceProvider`
    - Usare `ILanguageServiceProvider.InitializeAsync` abilitare Servizi di linguaggio per gli argomenti forniti quando viene aperto un file
    - Usare `ILanguageServiceProvider.UninitializeAsync` disabilitare servizi di linguaggio per gli argomenti forniti quando viene chiuso un file

>[!WARNING]
>Il `ILanguageServiceProvider` metodi potrebbero essere chiamati dall'area di lavoro sul thread principale. È consigliabile pianificare il lavoro in un thread diverso per evitare l'introduzione dei ritardi dell'interfaccia utente.

## <a name="language-server-protocol"></a>Protocollo di server di linguaggio

Il `Microsoft.VisualStudio.Workspace.*` API non sono l'unico modo per abilitare il servizio di linguaggio in Apri cartella. Un'altra opzione consiste nell'usare un server di linguaggio. Per altre informazioni, vedere la [protocollo di Server di linguaggio](language-server-protocol.md).

## <a name="related-interfaces"></a>Interfacce correlate

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> viene richiamato quando un file di corrispondenti tipi di file è aperto o chiuso per la modifica.

## <a name="next-steps"></a>Passaggi successivi

* [Compilazione dell'area di lavoro](workspace-build.md) -Apri cartella supporta i sistemi, ad esempio makefile e MSBuild di compilazione. 