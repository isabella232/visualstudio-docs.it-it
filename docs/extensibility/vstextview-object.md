---
title: Oggetto VSTextView | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cc6691e1b9cd4bd778f70e9b8f4acee3d16601c0
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586847"
---
# <a name="vstextview-object"></a>Oggetto VSTextView
La visualizzazione di testo è una finestra che consente agli utenti di visualizzare e modificare il testo Unicode del buffer di testo. In pratica, la visualizzazione è fare riferimento alla maggior parte degli utenti dell'editor. Poiché la vista è separata dal buffer da vari livelli di testo (ritorno a capo automatico, il testo della struttura e così via), la vista non è garantita a essere una rappresentazione esatta del testo nel buffer. Per altre informazioni sulla visualizzazione di testo, vedere [accesso theText visualizzazione tramite l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 Nella tabella seguente mostra le interfacce nel <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oggetto.  
  
|Interfaccia|Descrizione|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione delle azioni composte (vale a dire, azioni che vengono raggruppate in un'unità di annullamento/ripristino singolo).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fornisce i metodi di base per la gestione e l'accesso a vista. `IVsTextView` non è thread-safe.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea e gestisce un riquadro della finestra.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagisce con livelli di testo.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Esegue operazioni per la vista da un thread diverso.|  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica di figure](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Oggetto VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Accesso alla visualizzazione theText usando l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)