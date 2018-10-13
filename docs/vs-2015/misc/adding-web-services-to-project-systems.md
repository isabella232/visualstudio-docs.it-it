---
title: Aggiunta di servizi Web per sistemi di progetto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 88966ee17567970d0807792c57c2483cadb22f63
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280319"
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