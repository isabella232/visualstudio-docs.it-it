---
title: Oggetto VSTextView | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab54fce0271438f89ec66b4fc5d8db1ebe21634f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953088"
---
# <a name="vstextview-object"></a>Oggetto VSTextView
La visualizzazione di testo è una finestra che consente agli utenti di visualizzare e modificare il testo Unicode del buffer di testo. In pratica, la visualizzazione è fare riferimento alla maggior parte degli utenti dell'editor. Poiché la vista è separata dal buffer da vari livelli di testo (ritorno a capo automatico, il testo della struttura e così via), la vista non è garantita a essere una rappresentazione esatta del testo nel buffer. Per altre informazioni sulla visualizzazione di testo, vedere [accesso theText visualizzazione tramite l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

 Nella tabella seguente mostra le interfacce nel <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oggetto.

|Interfaccia|Descrizione|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione delle azioni composte (vale a dire, azioni che vengono raggruppate in un'unità di annullamento/ripristino singolo).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fornisce i metodi di base per la gestione e l'accesso a vista. `IVsTextView` non è thread-safe.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea e gestisce un riquadro della finestra.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagisce con livelli di testo.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Esegue operazioni per la vista da un thread diverso.|

## <a name="see-also"></a>Vedere anche
- [Modifica di figure](https://www.microsoft.com/download/details.aspx?id=55984)
- [Oggetto VSTextBuffer](../extensibility/vstextbuffer-object.md)
- [Accesso alla visualizzazione theText usando l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)