---
title: 'Procedura: Fornire il supporto di testo nascosto in un servizio di linguaggio Legacy | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a1906e101e5a50489f42558869c57cb0f175ebc4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965994"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Procedura: Fornisce il supporto di testo nascosto in un servizio di linguaggio legacy
È possibile creare aree di testo nascosto oltre alle aree della struttura. Aree di testo nascosto possono essere controllato dal client o dall'editor e vengono utilizzati per nascondere completamente un'area di testo. L'editor visualizza un'area nascosta come linee orizzontali. Un esempio di questo è il **solo Script** visualizzazione nell'editor HTML.  
  
  
## <a name="to-implement-a-hidden-text-region"></a>Per implementare un'area di testo nascosto  
  
1.  Chiamare `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Restituisce un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando un puntatore per un buffer di testo specificato. Determina se esiste già una sessione di testo nascosto per il buffer.  
  
3.  Se ne esiste già, quindi non è necessaria creare uno e un puntatore esistente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> viene restituito l'oggetto. Utilizzare questo puntatore per enumerare e creare aree di testo nascosto. In caso contrario, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> per creare una sessione di testo nascosto per il buffer.  
  
     Un puntatore al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> viene restituito l'oggetto.  
  
    > [!NOTE]
    >  Quando si chiama `CreateHiddenTextSession`, è possibile specificare un client di testo nascosto (vale a dire <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Il client di testo nascosto si invia una notifica quando la struttura o il testo nascosto viene espanso o compresso dall'utente.  
  
4.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> per aggiungere uno o più nuovi descrive le aree contemporaneamente, che specifica le informazioni seguenti nel `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) parametro:  
  
    1.  Specificare il valore `hrtConcealed` nella `iType` membro del <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura per indicare che si sta creando un'area nascosta, anziché un'area della struttura.  
  
        > [!NOTE]
        >  Quando sono nascosti aree nascosto, l'editor visualizza automaticamente le righe per le aree nascoste per indicare la presenza.  
  
    2.  Specificare se l'area è controllato dal client o dall'editor nel `dwBehavior` i membri del <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura. L'implementazione della struttura intelligente può contenere una combinazione di struttura editor - e controllato dal client e le aree di testo nascosto.