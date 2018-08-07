---
title: Oggetto VSTextBuffer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e763b8006dd2c01f8e2ee4beeffa7c78100b15b3
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586306"
---
# <a name="vstextbuffer-object"></a>Oggetto VSTextBuffer
Oggetto del buffer di testo rappresenta un flusso di testo Unicode, ovvero in genere associato a un file. Oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto può essere usato all'esterno del contesto dell'editor di base, come illustrato, una procedura guidata.  
  
 Nella tabella seguente mostra le interfacce di `VSTextBuffer`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Interfaccia OLE standard. Utilizzato per la gestione del buffer di annullamento/ripristino.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Interfaccia OLE standard.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione di azioni composti (vale a dire, azioni che vengono raggruppate in un'unità di annullamento/ripristino singolo).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Abilita il salvataggio permanente dei dati del documento gestiti dal buffer di testo.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornisce servizi di base; utilizzato da molti clienti.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Usato per cercare un buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Offre lettura e scrittura funzionalità usando le coordinate bidimensionali. Eredita da `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Offre lettura e scrittura utilizzando coordinate unidimensionali di funzionalità. Eredita da `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Consente di veloci e orientato al flusso e sequenziale al testo nel buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornisce l'accesso a una raccolta generica di proprietà. La proprietà più importante è il nome o moniker, del buffer. È possibile archiviare i propri dati casuali nel buffer con questa interfaccia mediante la creazione di un GUID e usarlo come chiave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Supporta punti di connessione per gli eventi.|  
  
## <a name="remarks"></a>Note  
 Il `VSTextBuffer` è disponibile in genere da un `QueryInterface` chiamare su `IVsTextBuffer`. Per altre informazioni, vedere [TextBuffer](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Modifica di figure](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)