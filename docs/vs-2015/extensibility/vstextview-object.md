---
title: Oggetto VSTextView | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a09a4911eca71565b39ffdfab3cc31ec92233e06
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526065"
---
# <a name="vstextview-object"></a>Oggetto VSTextView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [oggetto VSTextView](https://docs.microsoft.com/visualstudio/extensibility/vstextview-object).  
  
La visualizzazione di testo è una finestra che consente agli utenti di visualizzare e modificare il testo Unicode del buffer di testo. In pratica, la visualizzazione è fare riferimento alla maggior parte degli utenti dell'editor. Poiché la vista è separata dal buffer da vari livelli di testo (ritorno a capo automatico, il testo della struttura e così via), la vista non è garantita a essere una rappresentazione esatta del testo nel buffer. Per altre informazioni sulla visualizzazione di testo, vedere [accesso theText visualizzazione tramite l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
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
 [Accesso alla visualizzazione testo tramite l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

