---
title: Proprietà VSTextBuffer . Documenti Microsoft
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ea44d2b22c96d49f334f2ea33f9db8d69b5eb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697719"
---
# <a name="vstextbuffer-object"></a>Oggetto VSTextBuffer
L'oggetto buffer di testo rappresenta un flusso di testo Unicode, che è generalmente associato a un file. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto può essere utilizzato all'esterno del contesto dell'editor principale, come in, una procedura guidata.

 Nella tabella seguente vengono `VSTextBuffer`illustrate le interfacce di .

|Metodo|Descrizione|
|------------|-----------------|
|[Iolecommandtarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interfaccia OLE standard. Utilizzato per la gestione di annullamento/ripetizione nel buffer.|
|[Ipersistfile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Interfaccia OLE standard.|
|[Ipersiststream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione di azioni di composti, ovvero azioni raggruppate in una singola unità di annullamento/ripetizione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Consente la persistenza dei dati del documento gestiti dal buffer di testo.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornisce servizi di base; utilizzato da molti client.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Utilizzato per cercare un buffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fornisce funzionalità di lettura e scrittura utilizzando coordinate bidimensionali. Eredita dall'oggetto `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fornisce funzionalità di lettura e scrittura utilizzando coordinate unidimensionali. Eredita dall'oggetto `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Fornisce un accesso rapido, orientato al flusso e sequenziale, al testo nel buffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornisce l'accesso a una raccolta generica di proprietà. La proprietà più importante è il nome, o moniker, del buffer. È possibile archiviare i propri dati casuali nel buffer con questa interfaccia creando un GUID e utilizzandolo come chiave.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Supporta i punti di connessione per gli eventi.|

## <a name="remarks"></a>Osservazioni
 Il `VSTextBuffer` si trova `QueryInterface` di `IVsTextBuffer`solito da una chiamata su . Per ulteriori informazioni, consultate Buffer di [testo.](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015)

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Modifica delle figure](https://www.microsoft.com/download/details.aspx?id=55984)
