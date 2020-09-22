---
title: 'Elenco di controllo: creazione di un servizio di linguaggio legacy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b79afe64aafac473d4fe5d22464998d0c2f0537
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840071"
---
# <a name="checklist-creating-a-legacy-language-service"></a>Elenco di controllo: Creazione di un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nell'elenco di controllo seguente vengono riepilogati i passaggi di base che è necessario eseguire per creare un servizio di linguaggio per l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor principale. Per integrare il servizio di linguaggio in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , è necessario creare un analizzatore di espressioni di debug. Per ulteriori informazioni, vedere [scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) nell' [estensibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Passaggi per la creazione di un servizio di linguaggio  
  
1. Implementare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
    - Nel pacchetto VSPackage implementare l' <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaccia per fornire il servizio di linguaggio.  
  
    - Rendere disponibile il servizio di linguaggio per il Integrated Development Environment (IDE) nell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementazione.  
  
2. Implementare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia nella classe principale del servizio di linguaggio.  
  
     L' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia è il punto iniziale di interazione tra l'editor principale e il servizio di linguaggio.  
  
### <a name="optional-features"></a>Funzionalità facoltative  
 Le funzionalità seguenti sono facoltative e possono essere implementate in qualsiasi ordine. Queste funzionalità aumentano la funzionalità del servizio di linguaggio.  
  
- Colorazione della sintassi  
  
   Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. L'implementazione di questa interfaccia deve avere le informazioni sul parser per restituire le informazioni sul colore appropriate.  
  
   Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo restituisce l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia. Per ogni buffer di testo viene creata un'istanza del coloratore separata, pertanto è necessario implementare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia separatamente. Per ulteriori informazioni, vedere [colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
- Finestra del codice  
  
   Implementare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaccia per consentire al servizio di linguaggio di ricevere una notifica quando viene creata una nuova finestra del codice.  
  
   Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metodo restituisce l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaccia. Il servizio di linguaggio può quindi aggiungere una speciale interfaccia utente alla finestra del codice in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . Il servizio di linguaggio può anche eseguire qualsiasi elaborazione speciale, ad esempio l'aggiunta di un filtro di visualizzazione di testo in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A> .  
  
- Filtro visualizzazione testo  
  
   Per fornire il completamento delle istruzioni IntelliSense in un servizio di linguaggio, è necessario intercettare alcuni dei comandi che la visualizzazione di testo altrimenti gestirebbe. Per intercettare questi comandi, completare i passaggi seguenti:  
  
  - Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> per partecipare alla catena di comandi e gestire i comandi dell'editor.  
  
  - Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo e passare l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementazione.  
  
  - Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> metodo quando si scollega dalla visualizzazione in modo che questi comandi non vengano più passati all'utente.  
  
    I comandi che devono essere gestiti dipendono dai servizi forniti. Per ulteriori informazioni, vedere [comandi importanti per i filtri dei servizi di linguaggio](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
  > [!NOTE]
  > L' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interfaccia deve essere implementata nello stesso oggetto dell' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia.  
  
- Completamento istruzioni  
  
   Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.  
  
   Supportano il comando di completamento delle istruzioni, ovvero, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> e chiamano il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo nell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia, passando l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaccia. Per ulteriori informazioni, vedere [completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
- Suggerimenti per i metodi  
  
   Implementare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaccia per fornire i dati per la finestra del suggerimento sul metodo.  
  
   Installare il filtro di visualizzazione di testo per gestire i comandi in modo appropriato, in modo da stabilire quando visualizzare una finestra suggerimento dati metodo. Per ulteriori informazioni, vedere [informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
- Marcatori di errore  
  
   Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.  
  
   Creare gli oggetti marcatore di errore che implementano l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia e chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodo, passando l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia dell'oggetto indicatore di errore.  
  
   In genere, ogni marcatore di errore gestisce un elemento nella finestra elenco attività.  
  
- Elementi Elenco attività  
  
   Implementare una classe di elementi attività che fornisca l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> interfaccia.  
  
   Implementare una classe di provider di attività <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> che fornisca l'interfaccia e l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> interfaccia.  
  
   Implementare una classe di enumeratori di attività che fornisca l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interfaccia.  
  
   Registrare il provider di attività con il metodo dell'elenco attività <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> .  
  
   Ottenere l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfaccia chiamando il provider di servizi del servizio di linguaggio con il GUID del servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .  
  
   Creare oggetti elemento attività e chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> metodo nell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfaccia quando sono presenti attività nuove o aggiornate.  
  
- Elementi di attività di commento  
  
   Usare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfaccia e l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfaccia per ottenere i token delle attività di commento.  
  
   Ottenere un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> servizio.  
  
   Ottenere l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> metodo.  
  
   Implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> interfaccia per restare in ascolto delle modifiche nell'elenco dei token.  
  
- struttura  
  
   Sono disponibili diverse opzioni per il supporto della struttura. È ad esempio possibile supportare il comando **Comprimi alle definizioni** , fornire aree della struttura controllate dall'editor o supportare aree controllate dal client. Per altre informazioni, vedere [procedura: fornire supporto per la struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
- Registrazione del servizio di linguaggio  
  
   Per ulteriori informazioni su come registrare un servizio di linguaggio, vedere la pagina relativa alla [registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service2.md) e alla [gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md).  
  
- Guida sensibile al contesto  
  
   Fornire il contesto all'editor in uno dei modi seguenti:  
  
  - Fornire il contesto per i marcatori di testo implementando l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaccia.  
  
  Fornire tutto il contesto utente implementando l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
