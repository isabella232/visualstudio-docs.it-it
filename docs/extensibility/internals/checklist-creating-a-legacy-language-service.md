---
title: 'Elenco di controllo: Creazione di un servizio di linguaggio Legacy | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17e9936561bd0ebaa3742610b9b481d60e8489fb
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823651"
---
# <a name="checklist-create-a-legacy-language-service"></a>Elenco di controllo: Creare un servizio di linguaggio legacy
Elenco di controllo seguente sono riepilogati i passaggi di base è necessario eseguire per creare un servizio di linguaggio per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor principale. Integrare il servizio di linguaggio in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è necessario creare un analizzatore di espressioni di debug. Per altre informazioni, vedere [scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) nel [estendibilità del debugger Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Passaggi per creare un servizio di linguaggio

1. Implementare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - Nel pacchetto VSPackage, implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaccia per fornire il servizio di linguaggio.

    - Rendere il servizio di linguaggio disponibili per l'ambiente di sviluppo integrato (IDE) nei <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementazione.

2. Implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia nella classe del servizio principale del linguaggio.

     Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia è il punto iniziale dell'interazione tra l'editor principale e il servizio di linguaggio.

### <a name="optional-features"></a>Funzionalità facoltative
 Le funzionalità seguenti sono facoltative e possono essere implementate in qualsiasi ordine. Queste funzioni migliorano le funzionalità del servizio di linguaggio.

- Colorazione della sintassi

  Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. L'implementazione di questa interfaccia deve le informazioni del parser per restituire le informazioni sul colore appropriato.

  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> restituzione del metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia. Viene creata un'istanza di colorizzatore separato per ogni buffer di testo, pertanto è consigliabile implementare la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia separatamente. Per altre informazioni, vedere [colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

- Finestra del codice

  Implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaccia per abilitare il servizio di linguaggio ricevere una notifica quando viene creata una nuova finestra del codice.

  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> restituzione del metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaccia. Il servizio di linguaggio possa quindi aggiungere l'interfaccia utente speciali alla finestra del codice in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>. Il servizio di linguaggio può anche eseguire qualsiasi elaborazione speciale, ad esempio l'aggiunta di un filtro di visualizzazione di testo in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.

- Filtro di visualizzazione testo

  Per garantire il completamento delle istruzioni in un servizio di linguaggio, è necessario intercettare alcuni dei comandi che in caso contrario, è necessario gestire la visualizzazione di testo. Per intercettare questi comandi, completare i passaggi seguenti:

  - Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> partecipare i comandi dell'editor catena e handle di comando.

  - Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo e passare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementazione.

  - Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> metodo quando si scollega dalla vista in modo che questi comandi non vengono passati all'utente.

  I comandi che devono essere gestiti dipendono dai servizi forniti. Per altre informazioni, vedere [comandi importanti per il linguaggio di servizio filtri](../../extensibility/internals/important-commands-for-language-service-filters.md).

  > [!NOTE]
  > Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interfaccia deve essere implementata nell'oggetto stesso come il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia.

- Completamento istruzioni

  Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

  Supporta il comando di completamento istruzione (vale a dire <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) e chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia, il passaggio del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaccia. Per altre informazioni, vedere [completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Suggerimenti di metodo

  Implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaccia che fornisce dati per la finestra di suggerimento di metodo.

  Installare il filtro di visualizzazione di testo per gestire i comandi in modo appropriato, in modo da sapere quando visualizzare una finestra del suggerimento dati (metodo). Per altre informazioni, vedere [informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).

- Indicatori di errore

  Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

  Creare l'errore oggetti marcatore che implementano il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia e chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> , passando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia dell'oggetto marcatore errori.

  Ogni indicatore di errore in genere gestisce un elemento nella finestra Elenco attività.

- Elementi dell'elenco attività

  Implementare una classe elemento di attività offrendo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> interfaccia.

  Implementare una classe di provider attività fornendo le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> interfaccia e <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> interfaccia.

  Implementare una classe enumerator di attività offrendo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interfaccia.

  Registrare il provider di attività con l'elenco di attività <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> (metodo).

  Ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfaccia chiamando provider di servizi del servizio di linguaggio con il GUID del servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.

  Creare gli oggetti elemento di attività e chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> metodo nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfaccia quando sono disponibili nuove o aggiornate le attività.

- Elementi di attività di commento

  Usare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfaccia e <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfaccia per ottenere token di attività di commento.

  Ottenere un <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> dell'interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> servizio.

  Ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> dell'interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> (metodo).

  Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> interfaccia per l'ascolto delle modifiche nell'elenco dei token.

- struttura

  Sono disponibili diverse opzioni per il supporto della struttura. Ad esempio, è possibile supportare le **Comprimi alle definizioni** comando, forniscono aree della struttura controllata dall'editor o supportare le aree di gestito dal client. Per altre informazioni, vedere [Procedura: Fornire supporto per la struttura espanso in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).

- Registrazione del servizio di linguaggio

  Per altre informazioni su come registrare un servizio di linguaggio, vedere [registrare un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service2.md) e [gestire i pacchetti VSPackage](../../extensibility/managing-vspackages.md).

- Guida sensibile al contesto

  Fornire contesto all'editor in uno dei modi seguenti:

  - Fornire il contesto per marcatori di testo mediante l'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaccia.

  - Fornire tutto il contesto utente, implementando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaccia.

## <a name="see-also"></a>Vedere anche
- [Sviluppare un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
