---
title: Creare un'istanza di Editor principale con l'API Legacy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 59642b934f82990ce50f6dabaa38a97f34575997
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941566"
---
# <a name="instantiate-the-core-editor-by-using-the-legacy-api"></a>Creare un'istanza di editor principale con l'API legacy
L'editor è responsabile per la modifica funzioni, ad esempio inserimento, eliminazione, copia e Incolla di testo. Combina queste funzioni con le funzioni fornite da servizi di linguaggio, ad esempio di colorazione del testo, il rientro e il completamento delle istruzioni IntelliSense.  
  
 È possibile creare un'istanza di un'istanza di editor principale in uno dei tre modi:  
  
- Creare in modo esplicito un'istanza di base dell'editor in una finestra.  
  
- Fornire una factory dell'editor che restituisce un'istanza dell'editor di base  
  
- Aprire un file dalla gerarchia di progetto.  
  
  Le sezioni seguenti illustrano come usare l'API legacy per creare un'istanza di editor.  
  
## <a name="explicitly-open-a-core-editor-instance"></a>Aprire in modo esplicito un'istanza di editor core  
 Quando si ottiene in modo esplicito un'istanza di editor principale:  
  
- Ottenere un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> per contenere l'oggetto dati del documento in fase di modifica.  
  
- Creare una rappresentazione orientato alla riga dell'oggetto dati del documento tramite la creazione di un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> dell'interfaccia dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaccia.  
  
- Impostare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> come oggetto dati del documento per un'istanza dell'implementazione predefinita del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> dell'interfaccia, usando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> (metodo).  
  
   Host di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> dell'istanza in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaccia utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> (metodo).  
  
  A questo punto, la visualizzazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaccia fornisce una finestra che contiene un'istanza dell'editor principale.  
  
  Tuttavia, ciò non è un'istanza molto utile, perché non dispone di tasti di scelta rapida o accedere alle funzionalità avanzate. Per ottenere accesso alle funzionalità avanzate e tasti di scelta rapida:  
  
- Usare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodo per associare un servizio di linguaggio e l'oggetto dati del documento che usa l'editor.  
  
- Creare i proprio tasti di scelta rapida oppure usare l'impostazione predefinita impostando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetti vengono visualizzati le proprietà. A tale scopo, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> metodo con il <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> proprietà.  
  
   Per ottenere e utilizzare i tasti di scelta rapida non standard, crearli utilizzando il *vsct* file. Per altre informazioni, vedere [file table (vsct) di Visual Studio comando](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Come usare una factory dell'editor per ottenere l'editor principale di  
 Quando si implementa un editor principale con una factory editor usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo, seguire tutti i passaggi descritti nella sezione precedente per ospitare in modo esplicito un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> usando un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> dell'oggetto dati del documento, in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto.  
  
 Per visualizzare il testo, ottenere un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> dell'interfaccia dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> oggetto e chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (metodo).  
  
 Per fornire un servizio di linguaggio all'editor, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodo all'interno di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (metodo).  
  
 Per ottenere predefinito tasti di scelta rapida, a differenza della sezione precedente, utilizzare il contesto del comando restituito dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo durante il recupero dall'editor principale di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (metodo).  
  
 Se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo restituisce lo stesso GUID di comando dell'editor di testo, l'istanza dell'editor principale ottiene automaticamente il valore predefinito tasti di scelta rapida.  
  
 Per informazioni generali, vedere [procedura dettagliata: creazione di un core editor e la registrazione di un tipo di file editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Vedere anche  
 [All'interno dell'editor di base](../extensibility/inside-the-core-editor.md)   
 [Aprire e salvare elementi del progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura dettagliata: Creare un editor principale e la registrazione di un tipo di file editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)