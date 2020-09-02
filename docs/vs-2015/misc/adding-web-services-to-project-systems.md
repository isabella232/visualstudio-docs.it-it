---
title: Aggiunta di servizi Web ai sistemi del progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: f5b192be8e5f68ad9314fe08fff963c032013cb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002660"
---
# <a name="adding-web-services-to-project-systems"></a>Aggiunta di servizi Web ai sistemi del progetto
I servizi Web XML sono, in generale, risorse indirizzabili tramite URL che restituiscono informazioni programmatiche al sistema del progetto utilizzando il protocollo SOAP (Simple Object Access Protocol). È possibile integrare i servizi Web per il sistema di progetto VSPackage usando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> interfaccia.  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>Per aggiungere un servizio Web al sistema del progetto  
  
1. Chiamare `QueryService` per l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> interfaccia tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> servizio.  
  
2. Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> . Se si passa `pDiscoverySession` il parametro come `NULL` , viene creata automaticamente una sessione di individuazione e la sessione viene memorizzata nella cache in modo che sia disponibile per l'utilizzo successivo da parte dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> interfaccia. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> il metodo restituisce un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2> .  
  
3. Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> . Passare l'oggetto di automazione per la cartella riferimenti al servizio Web come `pUnkWebReferenceFolder` parametro. L'ambiente di Visual Studio controlla quindi se il servizio Web è già presente. Se il servizio Web non è presente, l'ambiente Scarica e aggiunge il servizio Web a una cartella e a eventuali file aggiuntivi, ad esempio file con estensione WSDL, nei nodi figlio della cartella.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>