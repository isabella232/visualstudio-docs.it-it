---
title: Oggetto oggetto VsTextBuffer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b68d443e542b6bd707aacc2b22d0efc1064152c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690635"
---
# <a name="vstextbuffer-object"></a>Oggetto VSTextBuffer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'oggetto buffer di testo rappresenta un flusso di testo Unicode, che in genere è associato a un file. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto può essere usato all'esterno del contesto dell'editor principale, come nel caso di una procedura guidata.  
  
 Nella tabella seguente vengono illustrate le interfacce di `VSTextBuffer` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interfaccia OLE standard. Utilizzato principalmente per la gestione delle operazioni di annullamento/ripristino nel buffer.|  
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
  
## <a name="remarks"></a>Osservazioni  
 `VSTextBuffer`Viene in genere trovato da una `QueryInterface` chiamata a `IVsTextBuffer` . Per ulteriori informazioni, vedere [buffer di testo](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Modifica figure](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
