---
title: Oggetto VSTextView . Documenti Microsoft
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
ms.openlocfilehash: 81d5e02d6ec18f8561a83b414532a4b78def5c09
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697704"
---
# <a name="vstextview-object"></a>Oggetto VSTextView

La visualizzazione di testo è una finestra che consente agli utenti di visualizzare e modificare il testo Unicode del buffer di testo. Essenzialmente, la visualizzazione è ciò che la maggior parte degli utenti si riferiscono a come l'editor. Poiché la visualizzazione è separata dal buffer da vari livelli di testo (a capo automatico, struttura del testo e così via), non è garantito che la visualizzazione sia una rappresentazione esatta del testo nel buffer. Per ulteriori informazioni sulla visualizzazione di testo, vedere [Accesso alla visualizzazione Testo tramite l'API legacy](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015).

Nella tabella seguente vengono illustrate <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> le interfacce nell'oggetto.

|Interfaccia|Descrizione|
|---------------|-----------------|
|[IDropSource (informazioni in cui è iDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione di azioni composte, ovvero azioni raggruppate in una singola unità di annullamento/ripetizione.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fornisce i metodi di base per la gestione e l'accesso alla visualizzazione. `IVsTextView`non è filettato sicuro.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea e gestisce un riquadro della finestra.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagisce con i livelli di testo.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Esegue operazioni sulla visualizzazione da un thread diverso.|

## <a name="see-also"></a>Vedere anche

- [Modifica delle figure](https://www.microsoft.com/download/details.aspx?id=55984)
- [Oggetto VSTextBuffer](../extensibility/vstextbuffer-object.md)
