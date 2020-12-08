---
title: Fornire supporto per testo nascosto nel servizio di linguaggio legacy
description: Informazioni su come fornire supporto per testo nascosto in un servizio di linguaggio legacy aggiungendo aree di testo nascoste controllate dall'editor o dal client.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1f51f8e0c5ca268c1171804f663e5d01bd7c2530
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761309"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Procedura: fornire il supporto per testo nascosto in un servizio di linguaggio legacy
Oltre alle aree della struttura, è possibile creare aree di testo nascoste. Le aree del testo nascosto possono essere controllate dal client o dall'editor e vengono usate per nascondere completamente un'area di testo. L'editor visualizza un'area nascosta come linee orizzontali. Un esempio è la visualizzazione **solo script** nell'editor HTML.

## <a name="to-implement-a-hidden-text-region"></a>Per implementare un'area di testo nascosta

1. Chiamare `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .

     Viene restituito un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , passando un puntatore per un buffer di testo specificato. Determina se una sessione di testo nascosto esiste già per il buffer.

3. Se ne esiste già uno, non è necessario crearne uno e viene restituito un puntatore all' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> oggetto esistente. Utilizzare questo puntatore per enumerare e creare aree del testo nascosto. In caso contrario, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> per creare una sessione di testo nascosta per il buffer.

     Viene restituito un puntatore all' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> oggetto.

    > [!NOTE]
    > Quando si chiama `CreateHiddenTextSession` , è possibile specificare un client di testo nascosto, ovvero <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> . Il client di testo nascosto invia una notifica quando il testo nascosto o la struttura viene espansa o compressa dall'utente.

4. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> per aggiungere una o più nuove aree della struttura alla volta, specificando le informazioni seguenti nel `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> parametro ():

    1. Specificare il valore `hrtConcealed` nel `iType` membro della <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura per indicare che si sta creando un'area nascosta, anziché un'area del contorno.

        > [!NOTE]
        > Quando le aree nascoste sono nascoste, nell'editor vengono visualizzate automaticamente le linee intorno alle aree nascoste per indicare la loro presenza.

    2. Consente di specificare se l'area è controllata dal client o dall'editor nei `dwBehavior` membri della <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura. L'implementazione intelligente della struttura può contenere una combinazione di aree di testo nascosto e di editor e controllo client.
