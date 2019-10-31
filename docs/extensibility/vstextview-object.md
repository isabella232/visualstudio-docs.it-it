---
title: Oggetto oggetto VsTextView | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 927bbee8bde62ff24396ea7b50e55e901b8cff06
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189016"
---
# <a name="vstextview-object"></a>Oggetto oggetto VsTextView

La visualizzazione di testo è una finestra che consente agli utenti di visualizzare e modificare il testo Unicode del buffer di testo. In pratica, la visualizzazione è la maggior parte degli utenti che fanno riferimento all'editor. Poiché la vista è separata dal buffer da vari livelli di testo (ritorno a capo automatico, testo della struttura e così via), la vista non è garantita come rappresentazione esatta del testo nel buffer. Per altre informazioni sulla visualizzazione di testo, vedere [accesso a TheText View con l'API legacy](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015).

Nella tabella seguente vengono illustrate le interfacce nell'oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

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

## <a name="see-also"></a>Vedere anche

- [Modifica figure](https://www.microsoft.com/download/details.aspx?id=55984)
- [Oggetto oggetto VsTextBuffer](../extensibility/vstextbuffer-object.md)