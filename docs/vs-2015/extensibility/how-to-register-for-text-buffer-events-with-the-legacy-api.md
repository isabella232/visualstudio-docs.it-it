---
title: "Procedura: registrarsi per gli eventi nel Buffer di testo con l'API Legacy | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76b782e688c567eb3888b2dbc890a360d22e3014
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232245"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Procedura: registrarsi per gli eventi nel Buffer di testo con l'API Legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si accede al buffer di testo usando l'API legacy, è necessario registrarsi per gli eventi nel buffer di testo come illustrato nella procedura seguente.  
  
### <a name="to-advise-text-buffer-events"></a>Per indicare gli eventi nel buffer di testo  
  
1.  Da un puntatore a una delle interfacce <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, chiamare `QueryInterface` per un puntatore a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> (metodo) e passare l'ID di interfaccia degli eventi per cui si vuole registrare.  
  
     Ad esempio, se si desidera registrare per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, poi passare a una ID di IID_IVsTextLinesEvents interfaccia.  
  
     Il buffer di testo restituisce un puntatore al <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia per l'oggetto punto di connessione appropriata.  
  
3.  Tramite questo puntatore, chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> , passando un puntatore all'implementazione dell'interfaccia degli eventi per il quale si desidera registrare, ad esempio, il `IVsTextLinesEvents` interfaccia.  
  
     L'ambiente restituisce un cookie che è quindi possibile utilizzare per interrompere l'ascolto di eventi chiamando il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi del buffer di testo nell'API legacy](../extensibility/text-buffer-events-in-the-legacy-api.md)

