---
title: Aree di lavoro e servizi di linguaggio in Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2893ae2bcd70ff317ba799fea6cfd2751c685731
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952701"
---
# <a name="workspaces-and-language-services"></a>Aree di lavoro e servizi di linguaggio

I servizi di linguaggio possono fornire agli utenti di [cartelle aperte](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) le stesse funzionalità avanzate del linguaggio utilizzate quando si utilizzano soluzioni e progetti. Un servizio di linguaggio può essere attivato in modo automatico in base all'estensione di file o al contenuto di un documento aperto, sebbene questo servizio di linguaggio "Loose file" sia limitato all'evidenziazione della sintassi. Sono necessarie informazioni aggiuntive per offrire un'esperienza più completa durante la modifica o la revisione del codice sorgente. Ogni servizio di linguaggio dispone di una propria API per l'inizializzazione con questi dati contestuali aggiuntivi per un documento. Questa operazione viene in genere gestita da un sistema di progetto, che è strettamente associato al servizio di linguaggio e al sistema di compilazione.

## <a name="initialization"></a>Inizializzazione

In un' [area di lavoro](workspaces.md), i servizi di linguaggio vengono inizializzati da un <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> punto di estensione che è specializzato solo in tale servizio di linguaggio e non conosce la creazione della compilazione. In questo modo, un proprietario del servizio di linguaggio può mantenere una singola estensione Open Folder indipendentemente dal numero di modelli presenti nelle cartelle e nei file per l'esecuzione del compilatore durante una compilazione, ad esempio MSBuild, makefile e così via. Quando i file da cui è stato creato un contesto di file vengono modificati sul disco e il contesto del file viene aggiornato, il provider di servizi di linguaggio riceve una notifica del set di contesti di file aggiornato. Il provider di servizi di linguaggio può quindi aggiornare il relativo modello.

Quando un documento viene aperto nell'editor, Visual Studio considera solo i provider di servizi di linguaggio che richiedono tipi di contesto del file per i quali è possibile trovare un provider del contesto del file corrispondente. Passa quindi i contesti di file dai provider corrispondenti al provider di servizi di lingua selezionato tramite `ILanguageServiceProvider.InitializeAsync` . Ciò che il provider di servizi di linguaggio esegue con i dati di contesto del file è un dettaglio di implementazione del provider di servizi di linguaggio, ma l'esperienza utente prevista è un servizio di linguaggio più completo per il documento aperto.

## <a name="using-ilanguageserviceprovider"></a>Uso di ILanguageServiceProvider

Il servizio di linguaggio riceverà una notifica quando viene creato un contesto di file con un `ContextType` che corrisponde a uno dei `SupportedContextTypes` valori dell'attributo di esportazione del server di linguaggio.

Per supportare un servizio di linguaggio, è necessario disporre di un'estensione:

- Oggetto univoco `Guid` . Questa funzione verrà utilizzata per gli `SupportedContextTypes` argomenti dell'attributo e in un `FileContext` oggetto.
- Contesto file di lingua
  - Factory del provider
    - `ExportFileContextProviderAttribute` attributo con la versione precedente generata in modo univoco `Guid` in `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementazione del provider di `IFileContextProvider.GetContextsForFileAsync`
    - Costruisce un nuovo oggetto `FileContext` con l' `contextType` argomento del costruttore come generato in modo univoco `Guid`
    - Utilizzare la `Context` proprietà di `FileContext` per fornire dati aggiuntivi al `ILanguageServiceProvider`
- Servizio di linguaggio
  - Factory del provider
    - `ExportLanguageServiceProvider` attributo con la versione precedente generata in modo univoco `Guid` in `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Provider
    - Implementa `ILanguageServiceProvider`
    - Usare `ILanguageServiceProvider.InitializeAsync` per abilitare i servizi di linguaggio per gli argomenti forniti quando viene aperto un file
    - Utilizzare `ILanguageServiceProvider.UninitializeAsync` per disabilitare i servizi di linguaggio per gli argomenti forniti quando un file viene chiuso

>[!WARNING]
>I `ILanguageServiceProvider` metodi possono essere richiamati dall'area di lavoro sul thread principale. Si consiglia di pianificare il lavoro in un thread diverso per evitare l'introduzione di ritardi dell'interfaccia utente.

## <a name="language-server-protocol"></a>Protocollo di server di linguaggio

Le `Microsoft.VisualStudio.Workspace.*` API non sono l'unico modo per abilitare il servizio di linguaggio in una cartella aperta. Un'altra opzione consiste nell'usare un server di linguaggio. Per ulteriori informazioni, vedere informazioni sul [protocollo server di linguaggio](language-server-protocol.md).

## <a name="related-interfaces"></a>Interfacce correlate

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> viene richiamato quando un file di tipi di file corrispondenti viene aperto o chiuso per la modifica.

## <a name="next-steps"></a>Passaggi successivi

* [Compilazione area di lavoro](workspace-build.md) : la cartella Apri supporta sistemi di compilazione quali MSBuild e Makefile.