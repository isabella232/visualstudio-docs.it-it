---
title: Aree di lavoro e servizi linguistici in Visual Studio | Microsoft Docs
description: Informazioni su come i servizi di linguaggio possono offrire agli utenti di Open Folder le stesse funzionalità avanzate del linguaggio a cui vengono usati quando lavorano con soluzioni e progetti.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: ccf64a52ec4a832fc6e73290fe1deaff3ed4db0de4cf442d2d6da3ecb65e5746
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400452"
---
# <a name="workspaces-and-language-services"></a>Aree di lavoro e servizi linguistici

I servizi di linguaggio possono fornire agli utenti [di Open Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) le stesse funzionalità avanzate del linguaggio a cui vengono usati quando lavorano con soluzioni e progetti. Un servizio di linguaggio può essere attivato automaticamente in base all'estensione di file o al contenuto di un documento aperto, anche se questo servizio di linguaggio "file libero" è limitato all'evidenziazione della sintassi. Sono necessarie informazioni aggiuntive per offrire un'esperienza più completa durante la modifica/revisione del codice sorgente. Ogni servizio di linguaggio ha una propria API per l'inizializzazione con questi dati contestuali aggiuntivi per un documento. Questa operazione viene in genere gestita da un sistema di progetto, strettamente abbinato sia al servizio di linguaggio che al sistema di compilazione.

## <a name="initialization"></a>Inizializzazione

In [un'area](workspaces.md)di lavoro i servizi di linguaggio vengono inizializzati da un punto di estensione specializzato solo in tale servizio di linguaggio e non conosce la creazione <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> della compilazione. In questo modo, il proprietario di un servizio di linguaggio può mantenere una singola estensione Open Folder indipendentemente dal numero di modelli presenti all'interno di cartelle e file per l'esecuzione del compilatore durante una compilazione ,ad esempio MSBuild, makefile e così via. Quando i file da cui è stato creato un contesto di file vengono modificati su disco e il contesto del file viene aggiornato, il provider del servizio di linguaggio viene informato del set aggiornato di contesti di file. Il provider di servizi di linguaggio può quindi aggiornare il modello.

Quando un documento viene aperto nell'editor, Visual Studio solo i provider di servizi di linguaggio che richiedono tipi di contesto di file per cui è possibile trovare un provider di contesto file corrispondente. Passa quindi i contesti di file dai provider corrispondenti al provider del servizio di linguaggio selezionato tramite `ILanguageServiceProvider.InitializeAsync` . Ciò che il provider di servizi di linguaggio esegue con i dati del contesto di file è un dettaglio di implementazione del provider di servizi di linguaggio, ma l'esperienza utente prevista è un servizio di linguaggio più ricco per il documento aperto.

## <a name="using-ilanguageserviceprovider"></a>Uso di ILanguageServiceProvider

Il servizio di linguaggio riceverà una notifica quando viene creato un contesto di file con un oggetto che corrisponde a uno dei valori dell'attributo `ContextType` di esportazione del server di `SupportedContextTypes` lingua.

Per supportare un servizio di linguaggio, un'estensione dovrà:

- Oggetto `Guid` univoco. Verrà usato per gli argomenti `SupportedContextTypes` dell'attributo e in un `FileContext` oggetto .
- Contesto del file di lingua
  - Factory del provider
    - `ExportFileContextProviderAttribute` attributo con l'elemento precedente generato `Guid` in modo univoco in `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementazione del provider di `IFileContextProvider.GetContextsForFileAsync`
    - Costruire un nuovo `FileContext` con `contextType` l'argomento del costruttore come generato in modo univoco `Guid`
    - Usare la `Context` proprietà `FileContext` dell'oggetto per fornire dati aggiuntivi all'oggetto `ILanguageServiceProvider`
- Servizio di linguaggio
  - Factory del provider
    - `ExportLanguageServiceProvider` attributo con l'elemento precedente generato `Guid` in modo univoco in `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Provider
    - Implementa `ILanguageServiceProvider`
    - Usare `ILanguageServiceProvider.InitializeAsync` per abilitare i servizi di linguaggio per gli argomenti forniti quando viene aperto un file
    - Usare `ILanguageServiceProvider.UninitializeAsync` per disabilitare i servizi di linguaggio per gli argomenti forniti quando un file viene chiuso

>[!WARNING]
>I `ILanguageServiceProvider` metodi possono essere richiamati dall'area di lavoro nel thread principale. Valutare la possibilità di pianificare il lavoro su un thread diverso per evitare ritardi dell'interfaccia utente.

## <a name="language-server-protocol"></a>Protocollo di server di linguaggio

Le `Microsoft.VisualStudio.Workspace.*` API non sono l'unico modo per abilitare il servizio di linguaggio in Apri cartella. Un'altra opzione è usare un server di linguaggio. Per altre informazioni, vedere Language [Server Protocol](language-server-protocol.md).

## <a name="related-interfaces"></a>Interfacce correlate

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> viene richiamato quando un file con tipi di file corrispondenti viene aperto o chiuso per la modifica.

## <a name="next-steps"></a>Passaggi successivi

* [Compilazione dell'area](workspace-build.md) di lavoro: Open Folder supporta sistemi di compilazione come MSBuild e makefile.