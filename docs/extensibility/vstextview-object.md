---
title: Oggetto oggetto VsTextView | Microsoft Docs
description: L'oggetto oggetto VsTextView è una finestra che consente agli utenti di visualizzare e modificare il testo Unicode del buffer di testo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d7309e05c3763794deb344a978dd188dbfddd79
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863817"
---
# <a name="vstextview-object"></a>Oggetto oggetto VsTextView

La visualizzazione di testo è una finestra che consente agli utenti di visualizzare e modificare il testo Unicode del buffer di testo. In pratica, la visualizzazione è la maggior parte degli utenti che fanno riferimento all'editor. Poiché la vista è separata dal buffer da vari livelli di testo (ritorno a capo automatico, testo della struttura e così via), la vista non è garantita come rappresentazione esatta del testo nel buffer. Per altre informazioni sulla visualizzazione di testo, vedere [accesso a TheText View con l'API legacy](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

Nella tabella seguente vengono illustrate le interfacce dell' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oggetto.

|Interfaccia|Descrizione|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione di azioni composte, ovvero azioni raggruppate in una singola unità di annullamento/ripristino.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fornisce i metodi di base per la gestione e l'accesso alla vista. `IVsTextView` non è thread-safe.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea e gestisce un riquadro della finestra.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagisce con i livelli di testo.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Esegue operazioni sulla vista da un thread diverso.|

## <a name="see-also"></a>Vedi anche

- [Modifica figure](https://www.microsoft.com/download/details.aspx?id=55984)
- [Oggetto oggetto VsTextBuffer](../extensibility/vstextbuffer-object.md)