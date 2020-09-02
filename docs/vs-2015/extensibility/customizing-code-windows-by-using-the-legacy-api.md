---
title: Personalizzazione delle finestre di codice tramite l'API legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15c649b8d857d2e920bb957e5975d296749cb86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62556133"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Personalizzazione delle finestre di codice tramite l'API legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una finestra del codice è un oggetto finestra del documento che supporta una o più visualizzazioni di testo. Le funzionalità esatte di una finestra del codice dipendono dal servizio di linguaggio associato. In modalità interfaccia a documenti multipli (MDI) la finestra del codice è il frame figlio MDI.  
  
 Le finestre del codice sono controllate dai servizi di linguaggio e ogni servizio di linguaggio può fornire la propria gestione delle finestre di codice. Ciò consente al servizio di linguaggio di aggiungere le proprie aree di modifica alla finestra del codice, ad esempio controllo ortografia durante, colorazione e altro ancora. Per altre informazioni su come creare una finestra principale, vedere [creazione di un'istanza dell'editor principale usando l'API legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Una finestra del codice è un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto che dispone di una visualizzazione di testo e di tutte le aree di visualizzazione presenti nell'oggetto. Quando si crea la finestra del codice durante la creazione di un'istanza dell'editor principale, il servizio di linguaggio può alleghiare un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> alla finestra del codice, come illustrato nella figura seguente.  
  
 ![Immagine di CodeWindow](../extensibility/media/vscodewindow.gif "oggetto VsCodeWindow.")  
Finestra del codice  
  
 Il servizio di linguaggio implementa gestione finestre del codice ed è responsabile della gestione delle aree di controllo, ad esempio una barra a discesa. La finestra del codice chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metodo durante l'inizializzazione della finestra del codice. Quando viene effettuata la chiamata, il servizio di linguaggio può aggiungere una barra a discesa o una barra dei pulsanti ( <xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient> ) alla finestra del codice.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 `Customizing Code Windows by Using the Legacy API`  
 Viene illustrato come personalizzare le finestre del codice usando l'API legacy.  
  
 [Procedura: Ospitare un editor in un altro editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Viene illustrato come ospitare un secondo editor all'interno di una finestra dell'editor.  
  
 [Procedura: Generare eventi quando l'editor perde lo stato attivo](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Viene illustrato come aggiungere una visualizzazione documento a un oggetto dati del documento.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Creazione di un'istanza dell'editor principale usando l'API legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Accesso alla visualizzazione testo tramite l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
