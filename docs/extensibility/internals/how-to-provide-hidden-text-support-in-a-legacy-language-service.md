---
title: Fornire supporto per il testo nascosto nel servizio di linguaggio legacy
description: Informazioni su come fornire il supporto del testo nascosto in un servizio di linguaggio legacy aggiungendo aree di testo nascosto controllate dall'editor o dal client.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 31c62f50cfff8662c543d24dceabdb429a9b9b05
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901786"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Procedura: Fornire supporto per il testo nascosto in un servizio di linguaggio legacy
Oltre alle aree del contorno, è possibile creare aree di testo nascoste. Le aree di testo nascoste possono essere controllate dal client o dall'editor e vengono usate per nascondere completamente un'area di testo. L'editor visualizza un'area nascosta sotto forma di linee orizzontali. Un esempio è la visualizzazione **Solo** script nell'editor HTML.

## <a name="to-implement-a-hidden-text-region"></a>Per implementare un'area di testo nascosto

1. Chiamare `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .

     Viene restituito un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , passando un puntatore per un buffer di testo specificato. Determina se esiste già una sessione di testo nascosto per il buffer.

3. Se ne esiste già uno, non è necessario crearne uno e viene restituito un puntatore <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> all'oggetto esistente. Usare questo puntatore per enumerare e creare aree di testo nascoste. In caso contrario, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> chiamare per creare una sessione di testo nascosto per il buffer.

     Viene restituito un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> puntatore all'oggetto .

    > [!NOTE]
    > Quando si chiama `CreateHiddenTextSession` , è possibile specificare un client di testo nascosto, ovvero <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> . Il client di testo nascosto invia una notifica quando il testo nascosto o la struttura viene espansa o compressa dall'utente.

4. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> per aggiungere una o più nuove aree della struttura alla volta, specificando le informazioni seguenti nel parametro ( `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> ):

    1. Specificare il valore nel membro della struttura per indicare che si sta creando un'area `hrtConcealed` `iType` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> nascosta, anziché un'area della struttura.

        > [!NOTE]
        > Quando le aree nascoste sono nascoste, l'editor visualizza automaticamente le righe intorno alle aree nascoste per indicarne la presenza.

    2. Specificare se l'area è controllata dal client o dall'editor nei `dwBehavior` membri della <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura . L'implementazione intelligente della struttura può contenere una combinazione di aree di testo nascoste e struttura controllate dall'editor e dal client.
