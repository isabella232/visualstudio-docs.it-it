---
title: Accesso al buffer di testo tramite l'API legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f2cfbd84bc4f9298358a2a2d1ba87f76d6e5303c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184991"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Accesso al buffer di testo tramite l'API legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il testo è responsabile della gestione dei flussi di testo e della persistenza dei file. Sebbene il buffer possa leggere o scrivere altri formati, tutte le comunicazioni ordinarie con il buffer vengono eseguite utilizzando Unicode. Nelle API legacy il buffer di testo può usare un sistema di coordinate uno o due dimensioni per identificare le posizioni dei caratteri nel buffer.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Sistemi di coordinate a una e due dimensioni  
 Una posizione di coordinate unidimensionale è basata sulla posizione di un carattere dal primo carattere del buffer, ad esempio 147. Usare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfaccia per accedere a una posizione unidimensionale nel buffer. Un sistema di coordinate bidimensionali si basa sulle coppie linea e indice. Ad esempio, un carattere nel buffer a 43, 5 sarà alla riga 43, a cinque caratteri a destra del primo carattere della riga. È possibile accedere a una posizione bidimensionale nel buffer usando l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfaccia. Entrambe le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfacce e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> vengono implementate dall'oggetto buffer di testo ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ) ed è possibile accedervi l'una dall'altra usando `QueryInterface` . Nel diagramma seguente vengono illustrate queste e altre interfacce chiave in <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 ![Oggetto TextBuffer](../extensibility/media/vstextbuffer.gif "Oggetto VsTextBuffer")  
Oggetto buffer di testo  
  
 Sebbene il sistema di coordinate funzioni nel buffer di testo, è ottimizzato per l'utilizzo di coordinate bidimensionali. Un sistema di coordinate unidimensionale può creare un sovraccarico delle prestazioni. Pertanto, quando possibile, utilizzare il sistema di coordinate bidimensionali.  
  
 La seconda responsabilità del buffer di testo è la persistenza dei file. A tale scopo, l'oggetto buffer di testo implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> e funge da componente oggetto dati documento per gli elementi di progetto e altri componenti dell'ambiente interessati dalla persistenza. Per ulteriori informazioni, vedere [apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Modifica delle impostazioni di visualizzazione tramite l'API legacy](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Viene illustrato come modificare le impostazioni di visualizzazione tramite l'API legacy.  
  
 [Uso della gestione testi per monitorare le impostazioni globali](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Viene illustrato come utilizzare Gestione testo per monitorare le impostazioni globali.  
  
## <a name="see-also"></a>Vedere anche  
 [Analisi dell'editor principale](../extensibility/inside-the-core-editor.md)
