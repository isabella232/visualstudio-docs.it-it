---
title: "Procedura: registrare gli eventi del buffer di testo con l'API legacy | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f36e8dd780788d241e3c286b1bbbe581311b143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204087"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Procedura: eseguire la registrazione per gli eventi del buffer di testo con l'API legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si accede al buffer di testo tramite l'API legacy, è necessario registrarsi per gli eventi del buffer di testo, come illustrato nella procedura seguente.  
  
### <a name="to-advise-text-buffer-events"></a>Per consigliare gli eventi del buffer di testo  
  
1. Da un puntatore a una delle interfacce in <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> , chiamare `QueryInterface` per un puntatore a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .  
  
2. Chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> metodo e passare l'ID di interfaccia degli eventi per i quali si desidera eseguire la registrazione.  
  
     Se ad esempio si vuole eseguire la registrazione per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> , passare un ID di interfaccia di IID_IVsTextLinesEvents.  
  
     Il buffer di testo restituisce un puntatore all' <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia per l'oggetto punto di connessione appropriato.  
  
3. Utilizzando questo puntatore, chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> metodo, passando un puntatore all'implementazione dell'interfaccia degli eventi per la quale si desidera eseguire la registrazione, ad esempio l' `IVsTextLinesEvents` interfaccia.  
  
     L'ambiente restituisce un cookie che è possibile usare per arrestare l'ascolto degli eventi chiamando il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi del buffer di testo nell'API legacy](../extensibility/text-buffer-events-in-the-legacy-api.md)
