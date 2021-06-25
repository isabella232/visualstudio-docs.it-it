---
title: Oggetto VSTextBuffer | Microsoft Docs
description: L'oggetto VSTextBuffer rappresenta un flusso di testo Unicode, generalmente associato a un file. Questo articolo elenca le interfacce di VSTextBuffer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3660a8dbb4a0a1280d5a3f428f73f3498244af7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905176"
---
# <a name="vstextbuffer-object"></a>Oggetto VSTextBuffer
L'oggetto buffer di testo rappresenta un flusso di testo Unicode, generalmente associato a un file. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto può essere usato all'esterno del contesto dell'editor principale, come in una procedura guidata.

 Nella tabella seguente vengono illustrate le interfacce di `VSTextBuffer` .

|Metodo|Descrizione|
|------------|-----------------|
|[Iolecommandtarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interfaccia OLE standard. Utilizzato per la gestione dell'annullamento o del ripetibilità nel buffer.|
|[Ipersistfile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Interfaccia OLE standard.|
|[Ipersiststream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Interfaccia OLE standard.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Abilita la creazione di azioni composte, ovvero azioni raggruppate in una singola unità di annullamento/ripeti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Abilita la persistenza dei dati del documento gestiti dal buffer di testo.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornisce servizi di base. usato da molti client.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Usato per cercare un buffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fornisce funzionalità di lettura e scrittura usando coordinate bidimensionali. Eredita dall'oggetto `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fornisce funzionalità di lettura e scrittura usando coordinate unidimensionali. Eredita dall'oggetto `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Fornisce un accesso rapido, orientato al flusso e sequenziale al testo nel buffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornisce l'accesso a una raccolta generica di proprietà. La proprietà più importante è il nome, o moniker, del buffer. È possibile archiviare i propri dati casuali nel buffer con questa interfaccia creando un GUID e usandolo come chiave.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Supporta i punti di connessione per gli eventi.|

## <a name="remarks"></a>Commenti
 `VSTextBuffer`L'oggetto viene in genere trovato da una chiamata a `QueryInterface` `IVsTextBuffer` . Per altre informazioni, vedere [Buffer di testo](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Modifica delle figure](https://www.microsoft.com/download/details.aspx?id=55984)