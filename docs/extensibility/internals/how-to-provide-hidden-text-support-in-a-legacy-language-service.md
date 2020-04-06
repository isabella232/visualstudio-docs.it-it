---
title: Fornire supporto per il testo nascosto nel servizio di linguaggio legacyProvide hidden text support in legacy language service
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9d5fe85932f87eb68b6b5a0f5868ebbf8f2b5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707934"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Procedura: fornire supporto per testo nascosto in un servizio di linguaggio legacyHow to: Provide hidden text support in a legacy language service
È possibile creare aree di testo nascoste oltre alle aree della struttura. Le aree di testo nascoste possono essere controllate dal client o dall'editor e vengono utilizzate per nascondere completamente un'area di testo. L'editor visualizza un'area nascosta come linee orizzontali. Un esempio è la visualizzazione **Solo script** nell'editor HTML.

## <a name="to-implement-a-hidden-text-region"></a>Per implementare un'area di testo nascostaTo implement a hidden text region

1. Chiamare `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>per .

     Restituisce un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>puntatore a .

2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando un puntatore per un buffer di testo specificato. Questo determina se esiste già una sessione di testo nascosto per il buffer.

3. Se ne esiste già uno, non è necessario crearne <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> uno e viene restituito un puntatore all'oggetto esistente. Utilizzare questo puntatore per enumerare e creare aree di testo nascoste. In caso <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> contrario, chiamare per creare una sessione di testo nascosto per il buffer.

     Viene restituito <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> un puntatore all'oggetto.

    > [!NOTE]
    > Quando si `CreateHiddenTextSession`chiama , è possibile specificare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>un client di testo nascosto, ovvero . Il client di testo nascosto invia una notifica quando il testo nascosto o la struttura viene espansa o compressa dall'utente.

4. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> per aggiungere una o più nuove aree di struttura `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>alla volta, specificando le seguenti informazioni nel parametro ( ):

    1. Specificare un `hrtConcealed` valore `iType` di <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> nel membro della struttura per indicare che si sta creando un'area nascosta, anziché un'area della struttura.

        > [!NOTE]
        > Quando le aree nascoste sono nascoste, l'editor visualizza automaticamente le linee intorno alle aree nascoste per indicarne la presenza.

    2. Specificare se l'area è controllata `dwBehavior` dal client <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> o dall'editor nei membri della struttura. L'implementazione della struttura intelligente può contenere una combinazione di aree di struttura e testo nascosto controllate dall'editor e dal client.
