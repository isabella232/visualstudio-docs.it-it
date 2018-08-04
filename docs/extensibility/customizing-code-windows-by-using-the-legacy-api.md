---
title: Personalizzazione di Windows di codice usando l'API Legacy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 454d58a48abafe9b23f8a812e5d40b9fc6477b50
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499354"
---
# <a name="customize-code-windows-by-using-the-legacy-api"></a>Personalizzare le finestre di codice usando l'API legacy
Una finestra del codice è un oggetto finestra di documento che supporta uno o più visualizzazioni di testo. Esattamente le stesse funzionalità di una finestra del codice dipendono dal servizio di linguaggio associato. In modalità interfaccia a documenti multipli (MDI), la finestra del codice è la cornice figlio MDI.  
  
 Finestre del codice sono controllate da servizi di linguaggio e ogni servizio di linguaggio può fornire un proprio gestore di finestra di codice. In questo modo il servizio di linguaggio aggiungere le proprie aree di controllo alla finestra del codice, ad esempio linee a zigzag, la colorazione e altro ancora. Per altre informazioni su come creare una finestra di core, vedere [creare un'istanza di editor principale con l'API legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Una finestra del codice è un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto con una visualizzazione di testo e tutte le aree di controllo ospitati nell'oggetto. Quando si crea la finestra del codice durante la creazione di un'istanza di una core editor, il servizio di linguaggio è possibile collegare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> alla finestra del codice, come è illustrato nella figura seguente.  
  
 ![Immagine di CodeWindow](../extensibility/media/vscodewindow.gif "oggetto vscodewindow")  
Finestra del codice  
  
 Il servizio di linguaggio implementa la gestione di finestre di codice ed è responsabile della gestione delle aree di controllo, ad esempio una barra di riepilogo a discesa. La finestra di codice chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metodo durante l'inizializzazione finestra del codice. Quando viene effettuata la chiamata, il servizio di linguaggio è possibile aggiungere una barra di riepilogo a discesa o una barra dei pulsanti (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) alla finestra del codice.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 `Customizing Code Windows by Using the Legacy API`  
 Viene illustrato come personalizzare le finestre di codice usando l'API legacy.  
  
 [Procedura: ospitare un editor in un altro editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Viene illustrato come ospitare un editor secondo all'interno di una finestra dell'editor.  
  
 [Procedura: generare eventi quando l'editor perde lo stato attivo](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Spiega come collegare una visualizzazione del documento a un oggetto dati del documento.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Creare un'istanza di editor principale con l'API legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Visualizzazione di theText accesso usando l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)