---
title: "Procedura: Registrarsi per gli eventi nel Buffer di testo con l'API Legacy | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10f1dbbc50535c1b0fd297f99c359ea8b0511c68
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321452"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Procedura: Eseguire la registrazione per gli eventi nel buffer di testo con l'API legacy
Se si accede al buffer di testo usando l'API legacy, è necessario registrarsi per gli eventi nel buffer di testo come illustrato nella procedura seguente.

## <a name="to-advise-text-buffer-events"></a>Per indicare gli eventi nel buffer di testo

1. Da un puntatore a una delle interfacce <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, chiamare `QueryInterface` per un puntatore a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.

2. Chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> (metodo) e passare l'ID di interfaccia degli eventi per cui si vuole registrare.

     Ad esempio, se si desidera registrare per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, poi passare a una ID di IID_IVsTextLinesEvents interfaccia.

     Il buffer di testo restituisce un puntatore al <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia per l'oggetto punto di connessione appropriata.

3. Tramite questo puntatore, chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> , passando un puntatore all'implementazione dell'interfaccia degli eventi per il quale si desidera registrare, ad esempio, il `IVsTextLinesEvents` interfaccia.

     L'ambiente restituisce un cookie che è quindi possibile utilizzare per interrompere l'ascolto di eventi chiamando il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> (metodo).

## <a name="see-also"></a>Vedere anche
- [Eventi nel buffer di testo nell'API legacy](../extensibility/text-buffer-events-in-the-legacy-api.md)