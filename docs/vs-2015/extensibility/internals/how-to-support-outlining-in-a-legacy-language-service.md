---
title: 'Procedura: supportare la struttura in un servizio di linguaggio legacy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d92baa824dbb70dd591cadef99775f943c651aef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840300"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Procedura: Fornire il supporto per la struttura in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La struttura viene utilizzata per espandere o comprimere aree diverse del testo. Il modo in cui viene utilizzata la struttura può essere definito in modo diverso da linguaggi diversi. Per altre informazioni, vedere [Struttura](../../ide/outlining.md).  
  
 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni sul nuovo metodo di implementazione della struttura, vedere [procedura dettagliata: struttura](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.  
  
 Di seguito viene illustrato come supportare questo comando per il servizio di linguaggio.  
  
### <a name="to-support-outlining"></a>Per supportare la struttura  
  
1. Implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> nell'oggetto servizio di linguaggio.  
  
2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> sull'oggetto sessione della struttura corrente per aggiungere nuove aree della struttura.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Quando un utente seleziona **Comprimi a definizioni** nel menu **struttura** , l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> servizio di linguaggio.  
  
 Quando viene chiamato questo metodo, l'IDE passa un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> puntatore (un puntatore a un buffer di testo) e un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (un puntatore alla sessione di struttura corrente).  
  
 È possibile chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> metodo per più aree della struttura specificando queste aree nel `rgOutlnReg` parametro. Il `rgOutlnReg` parametro è una <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> struttura. Questo processo consente di specificare caratteristiche diverse dell'area nascosta, ad esempio se un'area specifica viene espansa o compressa.  
  
> [!NOTE]
> Prestare attenzione a nascondere i caratteri di nuova riga. Il testo nascosto deve estendersi dall'inizio della prima riga fino all'ultimo carattere dell'ultima riga di una sezione, lasciando visibile il carattere di nuova riga finale.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: fornire il supporto per testo nascosto in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Procedura: Fornire il supporto per la struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
