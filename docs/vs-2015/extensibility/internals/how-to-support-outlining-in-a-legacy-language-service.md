---
title: 'Procedura: supportare la struttura in un servizio di linguaggio Legacy | Microsoft Docs'
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
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb596c8fbc7ab3c354b5b8d3e2a116ee752f06a4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724125"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Procedura: supportare la struttura in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La struttura consente di espandere o comprimere aree diverse del testo. La struttura viene utilizzata possono essere definiti in modo diverso in lingue diverse. Per altre informazioni, vedere [Struttura](../../ide/outlining.md).  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni sul nuovo modo per implementare la struttura, vedere [procedura dettagliata: struttura](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
 Di seguito viene illustrato come supportare questo comando per il servizio di linguaggio.  
  
### <a name="to-support-outlining"></a>Per supportare la struttura  
  
1.  Implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> nell'oggetto del servizio di linguaggio.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> sull'oggetto sessione per aggiungere nuove aree della struttura corrente della struttura.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Quando un utente seleziona **Comprimi alle definizioni** nel **struttura** dal menu, le chiamate IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> sul servizio di linguaggio.  
  
 Quando questo metodo viene chiamato, l'IDE passa in un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> puntatore (un puntatore a un buffer di testo) e un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (un puntatore alla sessione della struttura corrente).  
  
 È possibile chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> metodo per più aree di struttura specificando in queste aree il `rgOutlnReg` parametro. Il `rgOutlnReg` parametro è un <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> struttura. Questo processo consente di specificare diverse caratteristiche dell'area nascosta, ad esempio se una determinata area è espanso o compresso.  
  
> [!NOTE]
>  Prestare attenzione se si nasconde caratteri di nuova riga. Testo nascosto deve estendere dall'inizio della prima riga all'ultimo carattere dell'ultima riga in una sezione, lasciando visibili il carattere di nuova riga finale.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: fornire il supporto di testo nascosto in un servizio di linguaggio Legacy](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Procedura: Fornire il supporto per la struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

