---
title: 'Procedura: utilizzare marcatori di testo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c3c4f3a3d9a253b9ec671892d0d44ccf9ca3ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839616"
---
# <a name="how-to-use-text-markers"></a>Procedura: Usare i marcatori di testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile applicare i marcatori di testo per modificare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> oggetto.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-apply-text-markers"></a>Per applicare i marcatori di testo  
  
1. Ottenere un'istanza della <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> classe.  
  
    > [!NOTE]
    > L'editor principale applica automaticamente i marcatori di testo standard a qualsiasi documento che sta modificando e non dovrebbe essere necessario applicare in modo esplicito i marcatori di testo standard.  
  
2. Ottenere un ID del tipo di marcatore del marcatore a cui si è interessati chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metodo con l'oggetto `GUID` del marcatore di testo che si desidera utilizzare.  
  
    > [!NOTE]
    > Non usare l'oggetto `GUID` del VSPackage o del servizio che fornisce il marcatore di testo.  
  
3. Usare l'ID del tipo di marcatore ottenuto chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metodo come parametro per chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodo o il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodo per applicare un marcatore di testo a una determinata area di testo.  
  
#### <a name="to-add-features-to-text-markers"></a>Per aggiungere funzionalità ai marcatori di testo  
  
1. Potrebbe essere auspicabile aggiungere altre funzionalità a un marcatore di testo, ad esempio le descrizioni comandi, un menu di scelta rapida speciale o un gestore per circostanze particolari. A tale scopo, procedere nel seguente modo:  
  
2. Creare un oggetto che implementa l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia.  
  
3. Se è necessaria una funzionalità aggiuntiva, implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> e le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> interfacce nello stesso oggetto che implementa l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia.  
  
4. Passare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia creata, alla chiamata al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodo o al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodo usato per applicare il marcatore di testo a una determinata area di testo.  
  
5. Quando si aggiunge il supporto del menu di scelta rapida a un'area del marcatore di testo, è necessario creare il menu.  
  
     Per ulteriori informazioni sulla creazione di un menu di scelta rapida, vedere [menu di scelta rapida](../extensibility/context-menus.md).  
  
6. L' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente chiama i metodi delle interfacce fornite, ad esempio il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> metodo, o il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> metodo in base alle esigenze.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: aggiungere marcatori di testo standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Procedura: creare marcatori di testo personalizzati](../extensibility/how-to-create-custom-text-markers.md)   
 [Procedura: Implementare marcatori di errore](../extensibility/how-to-implement-error-markers.md)
