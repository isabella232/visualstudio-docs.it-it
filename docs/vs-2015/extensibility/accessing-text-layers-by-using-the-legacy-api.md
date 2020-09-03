---
title: Accesso ai livelli di testo tramite l'API legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 975e8624a6ffbfe0c5ae7544f2b978487465e34e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148015"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Accesso ai livelli di testo tramite l'API legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un livello di testo incapsula in genere alcuni aspetti del layout del testo. Ad esempio, un livello "funzione alla volta" nasconde il testo prima e dopo una funzione che contiene il cursore (punto di inserimento del testo).  
  
 Un livello di testo risiede tra un buffer e una visualizzazione e modifica il modo in cui la visualizzazione Visualizza il contenuto del buffer.  
  
## <a name="text-layer-information"></a>Informazioni sul livello di testo  
 Nell'elenco seguente viene descritto il funzionamento dei livelli di testo in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :  
  
- Il testo in un livello di testo può essere decorato con la colorazione della sintassi e i marcatori.  
  
- Attualmente non è possibile implementare livelli personalizzati.  
  
- Un livello espone <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> , che è derivato da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> . Il buffer di testo stesso viene inoltre implementato come un livello, che consente a una visualizzazione di gestire in modo polimorfico con i livelli sottostanti.  
  
- Un numero qualsiasi di livelli può trovarsi tra la visualizzazione e il buffer. Ogni livello si occupa solo del livello sottostante e la visualizzazione si occupa in gran parte del livello superiore. La vista contiene alcune informazioni sul buffer.  
  
- Un livello può influire solo sui livelli sottostanti. Non può influire sui livelli sopra di esso oltre gli eventi standard di origine.  
  
- Nell'editor, testo nascosto, testo sintetico e ritorno a capo automatico sono implementati come livelli. È possibile implementare testo nascosto e sintetico senza interagire direttamente con i livelli. Per ulteriori informazioni, vedere [la pagina relativa alla struttura in un servizio di linguaggio legacy](../extensibility/internals/outlining-in-a-legacy-language-service.md) e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession> .  
  
- Ogni livello di testo dispone di un sistema di coordinate locale che viene esposto tramite l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interfaccia. Il livello di incapsulamento della riga, ad esempio, potrebbe contenere due righe mentre il buffer di testo sottostante potrebbe contenere solo una riga.  
  
- La visualizzazione comunica con i livelli tramite l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interfaccia. Utilizzare questa interfaccia per risolvere le differenze tra le coordinate di visualizzazione e le coordinate del buffer.  
  
- Qualsiasi livello, ad esempio il livello di testo sintetico che origina il testo, deve fornire un'implementazione locale di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A> .  
  
- Inoltre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> , un livello di testo deve implementare <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> e generare gli eventi nell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Colorazione della sintassi negli editor personalizzati](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Uso di marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personalizzazione dei controlli e dei menu dell'editor tramite l'API legacy](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
