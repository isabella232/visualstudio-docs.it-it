---
title: Specifica di una finestra Proprietà personalizzate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: a244463832ff5620efa74a2c7fd20d6d47d79e76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62810702"
---
# <a name="providing-a-custom-properties-window"></a>Specifica di una finestra Proprietà personalizzate
È possibile fornire la finestra **Proprietà** personalizzata per un determinato sistema di progetto, anziché estendere la finestra **proprietà** fornita dal [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Integrated Development Environment (IDE). Lo scenario riscontrato più spesso è quando si implementa l'oggetto sito nella cornice della finestra.  
  
 Nel caso in cui l'oggetto non venga implementato nella cornice della finestra, ma è ancora possibile accedervi con altri metodi, è possibile accedere all' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaccia come indicato nell'ultima procedura in questa pagina.  
  
### <a name="to-provide-your-properties-window"></a>Per fornire il Finestra Proprietà  
  
1. Definire un GUID che rappresenta l'implementazione della finestra delle **Proprietà** .  
  
2. Nell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementazione di usare il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> servizio per dichiarare la finestra **Proprietà** come servizio all'ambiente di Visual Studio.  
  
### <a name="to-call-your-properties-window"></a>Per chiamare la finestra Proprietà  
  
1. Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> .  
  
2. `QueryService` per <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> dal <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> passato al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> metodo.  
  
3. Ottenere <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> servizio.  
  
4. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> con il primo parametro impostato su `SEID_PropertyBrowserSID` (tratto dall' <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> enumerazione) e il terzo parametro, `varValue` , che rappresenta un formato stringa del GUID che rappresenta la finestra delle **Proprietà** . Eseguire questa chiamata una sola volta alla prima creazione della finestra del documento della finestra delle **Proprietà** . Dopo che la chiamata a questa finestra **Proprietà** è associata alla cornice della finestra.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>Per ottenere l'oggetto frame della finestra quando l'utente non è l'implementatore  
  
- `QueryService`Per <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> il servizio da è possibile usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> il parametro `propid` impostato su <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> .  
  
- È possibile ottenere la finestra del documento attivo chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> tramite il servizio SVsMonitorSelection. Impostare il parametro `elementid` su `SEID_WindowFrame` , ricavato dall' <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> enumerazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../extensibility/internals/extending-properties.md)   
 [Campi e interfacce della finestra Proprietà](../extensibility/internals/properties-window-fields-and-interfaces.md)