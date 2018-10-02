---
title: 'Procedura: fornire il supporto di testo nascosto in un servizio di linguaggio Legacy | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b689bdfff45f12bc85f79b3cba8581e728c89728
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526096"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Procedura: fornire il supporto di testo nascosto in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: fornire supporto testo nascosto in un servizio di linguaggio Legacy](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service).  
  
È possibile creare aree di testo nascosto oltre alle aree della struttura. Aree di testo nascosto possono essere controllato dal client o dall'editor e vengono utilizzati per nascondere completamente un'area di testo. L'editor visualizza un'area nascosta come linee orizzontali. Un esempio è la visualizzazione solo Script nell'editor HTML.  
  
## <a name="procedure"></a>Routine  
  
#### <a name="to-implement-a-hidden-text-region"></a>Per implementare un'area di testo nascosto  
  
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

