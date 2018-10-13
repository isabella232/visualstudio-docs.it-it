---
title: 'Procedura: utilizzare marcatori di testo | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c23bcddceaf3d019add25c5d60ed843912348cc7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243412"
---
# <a name="how-to-use-text-markers"></a>Procedura: utilizzare marcatori di testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Marcatori di testo possono essere applicati per modificare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> oggetto.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-apply-text-markers"></a>Per applicare di marcatori di testo  
  
1.  Ottiene un'istanza di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> classe.  
  
    > [!NOTE]
    >  L'editor principale applica automaticamente i marcatori di testo standard per qualsiasi documento che sta modificando e non dovrebbe essere necessario applicare di marcatori di testo standard in modo esplicito.  
  
2.  Ottengano un ID di tipo marcatore del marcatore desiderati chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metodo con il `GUID` del marcatore di testo che si desidera utilizzare.  
  
    > [!NOTE]
    >  Non usare il `GUID` del pacchetto VSPackage o del servizio che fornisce il marcatore di testo.  
  
3.  Usare l'ID del tipo di marcatore ottenuta chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metodo come parametro per chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodo o il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodo per applicare un marcatore di testo a una determinata area di testo.  
  
#### <a name="to-add-features-to-text-markers"></a>Per aggiungere funzionalità a marcatori di testo  
  
1.  Potrebbe essere preferibile aggiungere ulteriori funzionalità a un marcatore di testo, ad esempio le descrizioni comandi, menu di scelta rapida speciali o gestore circostanze speciali. A tale scopo:  
  
2.  Creare un oggetto che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia.  
  
3.  Se si desidera usare funzionalità aggiuntive, implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>e il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> interfacce sullo stesso oggetto che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia.  
  
4.  Passare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia creati dall'utente, la chiamata ai <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodo o il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodo usato per applicare il marcatore di testo a una determinata area di testo.  
  
5.  Quando si aggiunge il supporto di menu di scelta rapida a un'area del marcatore di testo è necessario creare il menu di scelta.  
  
     Per altre informazioni su come creare un contesto menu, vedere [menu di scelta rapida](../extensibility/context-menus.md).  
  
6.  Il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente chiama i metodi delle interfacce fornite, ad esempio il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> metodo, o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> metodo in base alle esigenze.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di marcatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: aggiungere i marcatori di testo Standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Procedura: creare i marcatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)   
 [Procedura: Implementare marcatori di errore](../extensibility/how-to-implement-error-markers.md)

