---
title: Oggetto oggetto VsTextBuffer | Microsoft Docs
description: L'oggetto oggetto VsTextBuffer rappresenta un flusso di testo Unicode, che in genere è associato a un file. Questo articolo elenca le interfacce di oggetto VsTextBuffer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9207018ae4f2845e49c541695052ecc30de8914b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905685"
---
# <a name="vstextbuffer-object"></a>Oggetto oggetto VsTextBuffer
L'oggetto buffer di testo rappresenta un flusso di testo Unicode, che in genere è associato a un file. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto può essere usato all'esterno del contesto dell'editor principale, come in, una procedura guidata.

 Nella tabella seguente vengono illustrate le interfacce di `VSTextBuffer` .

|Metodo|Descrizione|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interfaccia OLE standard. Utilizzato per la gestione delle operazioni di annullamento/ripristino nel buffer.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Interfaccia OLE standard.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione di azioni di compound, ovvero azioni raggruppate in una singola unità di annullamento/ripristino.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Abilita la persistenza dei dati del documento gestiti dal buffer di testo.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornisce servizi di base; utilizzato da molti client.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Utilizzato per la ricerca in un buffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fornisce funzionalità di lettura e scrittura con coordinate bidimensionali. Eredita dall'oggetto `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fornisce funzionalità di lettura e scrittura usando coordinate unidimensionali. Eredita dall'oggetto `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Fornisce accesso sequenziale veloce e orientato al flusso al testo nel buffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornisce l'accesso a una raccolta generica di proprietà. La proprietà più importante è il nome, o moniker, del buffer. È possibile archiviare i dati casuali nel buffer con questa interfaccia creando un GUID e usandolo come chiave.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Supporta i punti di connessione per gli eventi.|

## <a name="remarks"></a>Commenti
 `VSTextBuffer`Viene in genere trovato da una `QueryInterface` chiamata a `IVsTextBuffer` . Per ulteriori informazioni, vedere [buffer di testo](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Modifica figure](https://www.microsoft.com/download/details.aspx?id=55984)