---
title: 'Elenco di controllo: Creazione di un servizio di linguaggio Legacy Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11785dab63cbb6a95ab2d34c5edbfb4525ebf34c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709782"
---
# <a name="checklist-create-a-legacy-language-service"></a>Elenco di controllo: creare un servizio di linguaggio legacyChecklist: Create a legacy language service
Nell'elenco di controllo seguente sono riepilogati i passaggi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di base da eseguire per creare un servizio di linguaggio per l'editor principale. Per integrare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]servizio di linguaggio in , è necessario creare un analizzatore di espressioni di debug. Per ulteriori informazioni, vedere [Scrivere un analizzatore](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) di espressioni CLR nell'estensibilità del debugger di [Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Procedura per creare un servizio di linguaggioSteps to create a language service

1. Implementare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - Nel pacchetto VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementare l'interfaccia per fornire il servizio di linguaggio.

    - Rendere il servizio di linguaggio disponibile per l'ambiente di sviluppo integrato (IDE) nell'implementazione. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>

2. Implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> l'interfaccia nella classe principale del servizio di linguaggio.

     L'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> è il punto di partenza dell'interazione tra l'editor principale e il servizio di linguaggio.

### <a name="optional-features"></a>Funzionalità facoltative
 Le seguenti funzionalità sono facoltative e possono essere implementate in qualsiasi ordine. Queste funzionalità aumentano la funzionalità del servizio di linguaggio.

- Colorazione della sintassi

  Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. L'implementazione di questa interfaccia deve utilizzare le informazioni sul parser per restituire le informazioni sul colore appropriate.

  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> restituisce l'interfaccia. Viene creata un'istanza di colorizzatore separata <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> per ogni buffer di testo, pertanto è necessario implementare l'interfaccia separatamente. Per ulteriori informazioni, consultate [Colorazione della sintassi in un servizio di linguaggio legacy.](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

- Finestra del codice

  Implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> l'interfaccia per consentire al servizio di linguaggio di ricevere la notifica di quando viene creata una nuova finestra del codice.

  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> restituisce l'interfaccia. Il servizio di linguaggio può quindi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>aggiungere un'interfaccia utente speciale alla finestra del codice in . Il servizio di linguaggio può inoltre eseguire qualsiasi elaborazione speciale, ad esempio l'aggiunta di un filtro di visualizzazione di testo in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.

- Filtro visualizzazione testo

  Per fornire il completamento delle istruzioni IntelliSense in un servizio di linguaggio, è necessario intercettare alcuni dei comandi che la visualizzazione di testo sarebbe altrimenti gestire. La procedura seguente illustra come intercettare questi comandi:

  - Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> per partecipare alla catena di comandi e gestire i comandi dell'editor.

  - Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> il metodo e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> passare l'implementazione.

  - Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> il metodo quando ci si disconnette dalla visualizzazione in modo che questi comandi non vengono più passati all'utente.

  I comandi che devono essere gestiti dipendono dai servizi forniti. Per ulteriori informazioni, vedere Comandi importanti per i filtri del [servizio di linguaggio](../../extensibility/internals/important-commands-for-language-service-filters.md).

  > [!NOTE]
  > L'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> deve essere implementata <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> sullo stesso oggetto dell'interfaccia.

- Completamento istruzioni

  Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

  Supportare il comando di <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>completamento dell'istruzione <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> (ovvero , <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> ) e chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo nell'interfaccia, passando l'interfaccia . Per ulteriori informazioni, vedere [Completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Suggerimenti per i metodi

  Implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> l'interfaccia per fornire i dati per la finestra di suggerimento del metodo.

  Installare il filtro di visualizzazione di testo per gestire i comandi in modo appropriato, in modo da sapere quando visualizzare una finestra di suggerimento dati del metodo. Per ulteriori informazioni, consultate Informazioni sui parametri [in un servizio di linguaggio legacy.](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

- Marcatori di errore

  Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

  Creare gli oggetti indicatore <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> di errore <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> che implementano <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> l'interfaccia e chiamare il metodo , passando l'interfaccia dell'oggetto indicatore di errore.

  In genere ogni indicatore di errore gestisce un elemento nella finestra dell'elenco attività.

- Voci dell'elenco attività

  Implementare una classe <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> dell'elemento di attività fornendo l'interfaccia.

  Implementare una classe <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> di provider <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> di attività che fornisca l'interfaccia e l'interfaccia.

  Implementare una classe <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> enumeratore di attività che fornisca l'interfaccia.

  Registrare il provider di attività <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> con il metodo dell'elenco attività.

  Ottenere <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> l'interfaccia chiamando il provider di servizi <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>del servizio di linguaggio con il GUID del servizio .

  Creare oggetti elemento di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> attività <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> e chiamare il metodo nell'interfaccia quando sono presenti attività nuove o aggiornate.

- Commentare gli elementi attività

  Utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> e l'interfaccia per ottenere i token dell'attività di commento.

  Ottenere <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> un'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> dal servizio.

  Ottenere <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> dal metodo .

  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> l'interfaccia per restare in ascolto delle modifiche nell'elenco dei token.

- struttura

  Sono disponibili diverse opzioni per supportare la struttura. Ad esempio, è possibile supportare il comando **Comprimi alle definizioni,** fornire aree della struttura controllate dall'editor o supportare aree controllate dal client. Per ulteriori informazioni, vedere Procedura: fornire il supporto della [struttura espansa in un servizio di linguaggio legacy.](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

- Registrazione del servizio di linguaggio

  Per ulteriori informazioni su come registrare un servizio di linguaggio, vedere [registrare un servizio](../../extensibility/internals/registering-a-legacy-language-service2.md) di linguaggio legacy e gestire [VSPackage](../../extensibility/managing-vspackages.md).

- Guida sensibile al contesto

  Fornire il contesto all'editor in uno dei modi seguenti:Provide context to the editor in one of the following ways:

  - Fornire il contesto per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> gli indicatori di testo implementando l'interfaccia.

  - Fornire tutto il contesto utente implementando l'interfaccia. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>

## <a name="see-also"></a>Vedere anche
- [Sviluppare un servizio di linguaggio legacyDevelop a legacy language service](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Scrivere un analizzatore di espressioni CLRWrite a CLR expression evaluator](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
