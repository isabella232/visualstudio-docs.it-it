---
title: 'Elenco di controllo: Creazione di un servizio di linguaggio legacy | Microsoft Docs'
description: Informazioni sui passaggi di base da eseguire per creare un servizio di linguaggio legacy per l'editor Visual Studio core.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 87ebb7ebbacbf03dcbf3275fc809ec26bffbada80c2786df10260aa1eab4a075
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359767"
---
# <a name="checklist-create-a-legacy-language-service"></a>Elenco di controllo: Creare un servizio di linguaggio legacy
L'elenco di controllo seguente riepiloga i passaggi di base da eseguire per creare un servizio di linguaggio per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'editor principale. Per integrare il servizio di linguaggio in , è necessario creare un analizzatore di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] espressioni di debug. Per altre informazioni, vedere [Scrivere un analizzatore](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) di espressioni CLR nell'estendibilità Visual Studio [debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Passaggi per creare un servizio di linguaggio

1. Implementare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - Nel pacchetto VSPackage implementare <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> l'interfaccia per fornire il servizio di linguaggio.

    - Rendere il servizio di linguaggio disponibile per l'ambiente di sviluppo integrato (IDE) <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> nell'implementazione.

2. Implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> l'interfaccia nella classe del servizio di linguaggio principale.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>L'interfaccia è il punto di partenza dell'interazione tra l'editor principale e il servizio di linguaggio.

### <a name="optional-features"></a>Funzionalità facoltative
 Le funzionalità seguenti sono facoltative e possono essere implementate in qualsiasi ordine. Queste funzionalità aumentano le funzionalità del servizio di linguaggio.

- Colorazione della sintassi

  Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. L'implementazione di questa interfaccia deve restituire le informazioni sul colore appropriate dal parser.

  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo restituisce <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> l'interfaccia . Viene creata un'istanza di colorizer separata per ogni buffer di testo, pertanto è necessario implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> l'interfaccia separatamente. Per altre informazioni, vedere [Colorazione della sintassi in un servizio di linguaggio legacy.](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

- Finestra del codice

  Implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> l'interfaccia per consentire al servizio di linguaggio di ricevere una notifica quando viene creata una nuova finestra del codice.

  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metodo restituisce <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> l'interfaccia . Il servizio di linguaggio può quindi aggiungere un'interfaccia utente speciale alla finestra del codice in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . Il servizio di linguaggio può anche eseguire qualsiasi elaborazione speciale, ad esempio l'aggiunta di un filtro di visualizzazione testo in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A> .

- Filtro visualizzazione testo

  Per fornire il completamento dell'istruzione IntelliSense in un servizio di linguaggio, è necessario intercettare alcuni dei comandi che altrimenti verrebbero gestiti dalla visualizzazione testo. Per intercettare questi comandi, seguire questa procedura:

  - Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> per partecipare alla catena di comandi e gestire i comandi dell'editor.

  - Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo e passare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'implementazione.

  - Chiamare il metodo quando si esegue lo scollegamento dalla visualizzazione in modo che questi comandi non <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> siano più passati all'utente.

  I comandi che devono essere gestiti dipendono dai servizi forniti. Per altre informazioni, vedere [Comandi importanti per i filtri del servizio di linguaggio](../../extensibility/internals/important-commands-for-language-service-filters.md).

  > [!NOTE]
  > <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>L'interfaccia deve essere implementata nello stesso oggetto dell'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- Completamento istruzioni

  Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

  Supportare il comando di completamento dell'istruzione , ovvero <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> , e chiamare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nell'interfaccia , passando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> l'interfaccia . Per altre informazioni, vedere [Completamento delle istruzioni in un servizio di linguaggio legacy.](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

- Suggerimenti per i metodi

  Implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> l'interfaccia per fornire dati per la finestra di suggerimento del metodo.

  Installare il filtro della visualizzazione testo per gestire i comandi in modo appropriato, in modo da sapere quando visualizzare una finestra di suggerimento dati del metodo. Per altre informazioni, vedere [Informazioni sui parametri in un servizio di linguaggio legacy.](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

- Marcatori di errore

  Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

  Creare gli oggetti marcatore di errore che implementano <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> l'interfaccia e chiamare il metodo , passando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> l'interfaccia dell'oggetto marcatore di errore.

  In genere ogni marcatore di errore gestisce un elemento nella finestra dell'elenco attività.

- Elementi dell'elenco attività

  Implementare una classe dell'elemento attività che fornisce <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> l'interfaccia .

  Implementare una classe del provider di attività che <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> fornisce l'interfaccia e <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> l'interfaccia .

  Implementare una classe di enumeratore di attività che fornisce <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> l'interfaccia .

  Registrare il provider di attività con il metodo dell'elenco <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> attività.

  Ottenere l'interfaccia chiamando il provider di servizi del servizio <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> di linguaggio con il GUID del servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .

  Creare oggetti elemento attività e chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> nell'interfaccia quando sono presenti attività nuove o aggiornate.

- Aggiungere commenti agli elementi dell'attività

  Usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> l'interfaccia e <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> l'interfaccia per ottenere i token dell'attività di commento.

  Ottenere <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> un'interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> servizio.

  Ottenere <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> l'interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> metodo .

  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> l'interfaccia per restare in ascolto delle modifiche nell'elenco di token.

- struttura

  Esistono diverse opzioni per il supporto della struttura. Ad esempio, è possibile supportare il comando **Comprimi** in definizioni, fornire aree struttura controllate dall'editor o supportare aree controllate dal client. Per altre informazioni, vedere Procedura: Fornire supporto della struttura espansa [in un servizio di linguaggio legacy.](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

- Registrazione del servizio di linguaggio

  Per altre informazioni su come registrare un servizio di linguaggio, vedere Registrare un servizio [di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service2.md) e Gestire [VSPackage.](../../extensibility/managing-vspackages.md)

- Guida sensibile al contesto

  Fornire il contesto all'editor in uno dei modi seguenti:

  - Fornire il contesto per i marcatori di testo implementando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> l'interfaccia .

  - Fornire tutto il contesto utente implementando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> l'interfaccia .

## <a name="see-also"></a>Vedi anche
- [Sviluppare un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
