---
title: L'accesso ai livelli di testo usando l'API Legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47085216c6f20ca1add535a76ce4f5fb4043a6dd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945938"
---
# <a name="access-text-layers-by-using-the-legacy-api"></a>Livelli di accesso testo usando l'API legacy
Un livello di testo sono incluse in genere alcuni aspetti del layout del testo. Ad esempio, un livello "una funzione-tempo" nasconde il testo prima e dopo una funzione che contiene il punto di inserimento (il punto di inserimento di testo).  
  
 Un livello di testo si trova tra un buffer e una visualizzazione e modifica il modo in cui che la vista visualizza i contenuti del buffer.  
  
## <a name="text-layer-information"></a>Informazioni sul livello di testo  
 Nell'elenco seguente viene descritto il funzionano di livelli di testo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Il testo in un livello di testo può essere decorato con marcatori e la colorazione della sintassi.  
  
-   Attualmente non è possibile implementare i proprio livelli.  
  
-   Un livello espone <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, che deriva da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. Lo stesso buffer di testo viene anche implementato come un livello, che consente una visualizzazione gestire in modo polimorfico livelli sottostanti.  
  
-   Un numero qualsiasi di livelli può essere compreso tra la visualizzazione e il buffer. Ogni livello si occupa solo al livello sottostante e la visualizzazione si occupa principalmente di livello superiore. (La visualizzazione avere alcune informazioni sui buffer).  
  
-   Un livello può influire sulle solo i livelli sottostanti. Tale operazione non influisce sui livelli sopra di esso, oltre che hanno origine gli eventi standard.  
  
-   Nell'editor di testo nascosto e sintetica di testo a capo vengono implementati come livelli. È possibile implementare il testo nascosto e sintetico senza interagire direttamente con i livelli. Per altre informazioni, vedere [struttura in un servizio di linguaggio legacy](../extensibility/internals/outlining-in-a-legacy-language-service.md) e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Ogni livello di testo ha un proprio sistema di coordinate locale che viene esposta tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interfaccia. Il livello di riga a capo automatico, ad esempio, potrebbe contenere due righe anche se il buffer di testo sottostante può contenere solo una riga.  
  
-   La vista comunica ai livelli tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interfaccia. Utilizzare questa interfaccia per risolvere le differenze tra le coordinate di visualizzazione con le coordinate del buffer.  
  
-   Uno dei livelli, ad esempio livello sintetica di testo che genera il testo deve fornire un'implementazione locale di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Altre origini oltre a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, deve implementare un livello di testo <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> e genera gli eventi nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Colorazione della sintassi negli editor personalizzati](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Usare marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personalizzare menu e controlli di editor usando l'API legacy](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)