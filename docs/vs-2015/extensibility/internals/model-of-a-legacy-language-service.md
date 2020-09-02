---
title: Modello di un servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27d51df6dd11509b86e6648d59978b87d9cd8a02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157663"
---
# <a name="model-of-a-legacy-language-service"></a>Modello di un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un servizio di linguaggio definisce gli elementi e le funzionalità per una lingua specifica e viene usato per fornire all'editor le informazioni specifiche di tale lingua. È ad esempio necessario che l'editor conosca gli elementi e le parole chiave del linguaggio per supportare la colorazione della sintassi.  
  
 Il servizio di linguaggio opera a stretto contatto con il buffer di testo gestito dall'editor e con la visualizzazione che contiene l'editor. L'opzione Microsoft IntelliSense **Quick Info** è un esempio di funzionalità fornita da un servizio di linguaggio.  
  
## <a name="a-minimal-language-service"></a>Un servizio di linguaggio minimo  
 Il servizio di linguaggio più semplice contiene i due oggetti seguenti:  
  
- Il *servizio di linguaggio* implementa l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia. Un servizio di linguaggio dispone di informazioni sulla lingua, tra cui il nome, le estensioni di file, il gestore della finestra del codice e il colorante.  
  
- Il *coloratore* implementa l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia.  
  
  Il disegno concettuale seguente mostra un modello di servizio di linguaggio di base.  
  
  ![Rappresentazione grafica di Language Service Model](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
  Modello di servizio del linguaggio di base  
  
  La finestra del documento ospita la *visualizzazione documento* dell'editor, in questo caso l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor principale. La visualizzazione del documento e il buffer di testo sono di proprietà dell'editor. Questi oggetti funzionano con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tramite una finestra di documento specializzata denominata *finestra del codice*. La finestra del codice è contenuta in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto creato e controllato dall'IDE.  
  
  Quando viene caricato un file con una determinata estensione, l'editor individua il servizio di linguaggio associato all'estensione e lo passa alla finestra del codice chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metodo. Il servizio di linguaggio restituisce una *Gestione finestre di codice*, che implementa l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaccia.  
  
  Nella tabella seguente viene fornita una panoramica degli oggetti nel modello.  
  
|Componente|Oggetto|Funzione|  
|---------------|------------|--------------|  
|Buffer di testo|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Flusso di testo in lettura/scrittura Unicode. È possibile che il testo usi altre codifiche.|  
|Finestra del codice|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Finestra del documento che contiene una o più visualizzazioni di testo. Quando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è in modalità interfaccia a documenti multipli (MDI), la finestra del codice è un elemento figlio MDI.|  
|Visualizzazione testo|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Finestra che consente all'utente di spostarsi e visualizzare il testo utilizzando la tastiera e il mouse. Una visualizzazione di testo viene visualizzata all'utente come editor. È possibile utilizzare le visualizzazioni di testo nelle finestre dell'editor normali, nella finestra di output e nella finestra di controllo immediato. Inoltre, è possibile configurare una o più visualizzazioni di testo all'interno di una finestra del codice.|  
|Gestione testo|Gestito dal <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> servizio, da cui si ottiene un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> puntatore|Componente che mantiene le informazioni comuni condivise da tutti i componenti descritti in precedenza.|  
|Servizio di linguaggio|Dipendente dall'implementazione; implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Oggetto che fornisce all'editor le informazioni specifiche della lingua, ad esempio l'evidenziazione della sintassi, il completamento delle istruzioni e la corrispondenza delle parentesi graffe.|  
  
## <a name="see-also"></a>Vedere anche  
 [Dati documento e visualizzazione documento negli editor personalizzati](../../extensibility/document-data-and-document-view-in-custom-editors.md)
