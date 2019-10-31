---
title: Oggetto oggetto VsTextBuffer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1895efa9ef10e1e554b98844619507224f09126
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189018"
---
# <a name="vstextbuffer-object"></a>Oggetto oggetto VsTextBuffer
L'oggetto buffer di testo rappresenta un flusso di testo Unicode, che in genere è associato a un file. Un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> può essere utilizzato all'esterno del contesto dell'editor principale, come in, una procedura guidata.

 Nella tabella seguente vengono illustrate le interfacce di `VSTextBuffer`.

|Metodo|Descrizione|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interfaccia OLE standard. Utilizzato per la gestione delle operazioni di annullamento/ripristino nel buffer.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Interfaccia OLE standard.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione di azioni di compound, ovvero azioni raggruppate in una singola unità di annullamento/ripristino.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Abilita la persistenza dei dati del documento gestiti dal buffer di testo.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornisce servizi di base; utilizzato da molti client.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Utilizzato per la ricerca in un buffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fornisce funzionalità di lettura e scrittura con coordinate bidimensionali. Eredita da `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fornisce funzionalità di lettura e scrittura usando coordinate unidimensionali. Eredita da `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Fornisce accesso sequenziale veloce e orientato al flusso al testo nel buffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornisce l'accesso a una raccolta generica di proprietà. La proprietà più importante è il nome, o moniker, del buffer. È possibile archiviare i dati casuali nel buffer con questa interfaccia creando un GUID e usandolo come chiave.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Supporta i punti di connessione per gli eventi.|

## <a name="remarks"></a>Note
 Il `VSTextBuffer` viene in genere trovato da una chiamata `QueryInterface` su `IVsTextBuffer`. Per ulteriori informazioni, vedere [buffer di testo](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Modifica figure](https://www.microsoft.com/download/details.aspx?id=55984)