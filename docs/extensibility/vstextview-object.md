---
title: Oggetto VSTextView | Microsoft Docs
description: L'oggetto VSTextView è una finestra che consente agli utenti di visualizzare e modificare il testo Unicode del buffer di testo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8bfce06cdb6e98b6090933b83f53d43bed3f9b44317c60658d8d1eba4997ddec
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413518"
---
# <a name="vstextview-object"></a>Oggetto VSTextView

La visualizzazione testo è una finestra che consente agli utenti di visualizzare e modificare il testo Unicode del buffer di testo. In sostanza, la visualizzazione è ciò a cui la maggior parte degli utenti fa riferimento come editor. Poiché la visualizzazione è separata dal buffer da vari livelli di testo (ritorno a capo automatico, struttura del testo e così via), non è garantito che la visualizzazione sia una rappresentazione esatta del testo nel buffer. Per altre informazioni sulla visualizzazione testo, vedere [Accesso alla visualizzazione Testo tramite l'API legacy.](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

Nella tabella seguente vengono illustrate le interfacce <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> nell'oggetto .

|Interfaccia|Descrizione|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione di azioni composte, ovvero azioni raggruppate in una singola unità di annullamento/ripeti.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fornisce i metodi di base per la gestione e l'accesso alla visualizzazione. `IVsTextView` non è thread-safe.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea e gestisce un riquadro della finestra.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagisce con i livelli di testo.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Esegue operazioni sulla visualizzazione da un thread diverso.|

## <a name="see-also"></a>Vedi anche

- [Modifica delle figure](https://www.microsoft.com/download/details.aspx?id=55984)
- [Oggetto VSTextBuffer](../extensibility/vstextbuffer-object.md)