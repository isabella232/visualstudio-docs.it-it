---
title: Creazione di un'istanza dell'editor principale usando l'API legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29306a16390039c8ee6e424b81a5ff617e533ab4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203917"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Creazione di un'istanza dell'editor principale tramite l'API legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'editor è responsabile delle funzioni di modifica del testo, ad esempio inserimento, eliminazione, copia e incolla. Combina queste funzioni con quelle fornite dai servizi di linguaggio, ad esempio la colorazione del testo, il rientro e il completamento delle istruzioni IntelliSense.  
  
 È possibile creare un'istanza dell'editor principale in uno dei tre modi seguenti:  
  
- Creare in modo esplicito un'istanza dell'editor principale in una finestra.  
  
- Fornire una factory dell'editor che restituisce un'istanza dell'editor principale  
  
- Aprire un file dalla gerarchia del progetto.  
  
  Le sezioni seguenti illustrano come usare l'API legacy per creare un'istanza dell'editor.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Apertura esplicita di un'istanza dell'editor principale  
 Quando si ottiene in modo esplicito un'istanza dell'editor principale:  
  
- Ottenere un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> oggetto che contenga l'oggetto dati del documento in corso di modifica.  
  
- Creare una rappresentazione orientata alla riga dell'oggetto dati del documento creando un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfaccia dall' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaccia.  
  
- Viene impostato <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> come oggetto dati del documento per un'istanza dell'implementazione predefinita dell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> interfaccia utilizzando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> metodo.  
  
   Ospitare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> istanza di in un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaccia utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> metodo.  
  
  A questo punto, la visualizzazione dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaccia fornisce una finestra contenente un'istanza dell'editor principale.  
  
  Tuttavia, non si tratta di un'istanza molto utile, perché non dispone di tasti di scelta rapida o di accesso alle funzionalità avanzate. Per ottenere l'accesso ai tasti di scelta rapida e alle funzionalità avanzate:  
  
- Utilizzare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodo per associare un servizio di linguaggio e l'oggetto dati del documento utilizzato dall'editor.  
  
- Creare tasti di scelta rapida personalizzati o usare l'impostazione predefinita del sistema impostando le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> proprietà di visualizzazione degli oggetti. A tale scopo, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> metodo con la <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> Proprietà.  
  
   Per ottenere e usare i tasti di scelta rapida non standard, generarli usando il file con estensione vsct. Per altre informazioni, vedere [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Come usare una factory dell'editor per ottenere l'editor principale  
 Quando si implementa un editor principale con una factory dell'editor usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo, seguire tutti i passaggi descritti nella sezione precedente per ospitare in modo esplicito un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> oggetto usando un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> oggetto dati del documento, in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto.  
  
 Per visualizzare il testo, ottenere un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia dall' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> oggetto e chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo.  
  
 Per fornire un servizio di linguaggio all'editor, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodo all'interno del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo.  
  
 Per ottenere i tasti di scelta rapida predefiniti, a differenza della sezione precedente, si usa il contesto del comando restituito dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo quando si ottiene l'editor principale dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo.  
  
 Se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo restituisce lo stesso GUID del comando dell'editor di testo, l'istanza dell'editor principale ottiene automaticamente i tasti di scelta rapida predefiniti.  
  
 Per informazioni generali, vedere [procedura dettagliata: creazione di un editor principale e registrazione di un tipo di file dell'editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Vedere anche  
 [All'interno dell'editor principale](../extensibility/inside-the-core-editor.md)   
 [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura dettagliata: Creazione di un editor principale e registrazione di un tipo di file dell'editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
