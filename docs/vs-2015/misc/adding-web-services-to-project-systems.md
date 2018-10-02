---
title: Aggiunta di servizi Web per sistemi di progetto | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: 80de75b1b10a761e88b86c0982c0dc925c6eeeb4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526266"
---
# <a name="adding-web-services-to-project-systems"></a>Aggiunta di servizi Web ai sistemi del progetto
Servizi Web XML sono in genere, le risorse indirizzabili tramite URL che restituiscono informazioni a livello di codice per il sistema di progetto utilizzando il protocollo SOAP (Simple Object Access Protocol). È possibile integrare servizi Web per il sistema di progetto VSPackage usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> interfaccia.  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>Per aggiungere un servizio Web per il sistema di progetto  
  
1.  Chiamare `QueryService` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> interfacciarsi tramite <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> servizio.  
  
2.  Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A>. Se viene passato `pDiscoverySession` come parametro `NULL`, viene creata automaticamente una sessione di individuazione e la sessione viene memorizzato nella cache in modo che sia disponibile per l'utilizzo successivo dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> interfaccia. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> metodo restituisce un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>.  
  
3.  Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A>. Passare l'oggetto di automazione per la cartella Riferimenti del servizio Web come il `pUnkWebReferenceFolder` parametro. L'ambiente di Visual Studio verifica quindi se il servizio Web è già presente. Se il servizio Web non è presente, l'ambiente Scarica e aggiunge il servizio Web a una cartella e file aggiuntivi (ad esempio i file. WSDL) per i nodi figlio della cartella.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>