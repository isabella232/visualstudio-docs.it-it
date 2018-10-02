---
title: Aggiornamento dei valori di proprietà nella finestra proprietà | Microsoft Docs
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
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 0272ba348e29fb1a2a118a0ff4b0989a2aa1683f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526408"
---
# <a name="updating-property-values-in-the-properties-window"></a>Aggiornamento dei valori della proprietà nella finestra Proprietà
Esistono due modi per mantenere sincronizzata la finestra **Proprietà** con le modifiche dei valori della proprietà. Il primo consiste nel chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia, che fornisce l'accesso alle funzionalità windowing di base, inclusi l'accesso e creazione di finestre dei documenti e finestre fornita dall'ambiente. I passaggi seguenti descrivono il processo di sincronizzazione.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Aggiornamento dei valori di proprietà tramite IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Per aggiornare i valori di proprietà tramite l'interfaccia IVsUIShell  
  
1.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (tramite <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> servizio) ogni volta che VSPackage, progetti o editor devono creare o enumerare finestre degli strumenti o documento.  
  
2.  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> per mantenere il **delle proprietà** finestra sincronizzato con le modifiche alle proprietà per un progetto (o qualsiasi altro oggetto selezionato visualizzato tramite il **proprietà** finestra) senza implementare <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> e la generazione di <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> gli eventi.  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> per stabilire e disabilitare, rispettivamente, la notifica client degli eventi della gerarchia senza richiedere la gerarchia per implementare <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
## <a name="updating-property-values-using-iconnection"></a>Aggiornamento dei valori di proprietà tramite IConnection  
 Il secondo modo per mantenere sincronizzata la finestra **Proprietà** con le modifiche dei valori della proprietà consiste nell'implementare `IConnection` sull'oggetto collegabile per indicare l'esistenza delle interfacce in uscita. Se si vuole localizzare il nome della proprietà, derivare l'oggetto da <xref:System.ComponentModel.ICustomTypeDescriptor>. Il <xref:System.ComponentModel.ICustomTypeDescriptor> implementazione può modificare i descrittori di proprietà restituisce e cambiare il nome di una proprietà. Per localizzare la descrizione, creare un attributo che deriva da <xref:System.ComponentModel.DescriptionAttribute> ed eseguire l'override della proprietà Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Considerazioni relative all'implementazione dell'interfaccia IConnection  
  
1.  `IConnection` fornisce l'accesso a un oggetto secondario enumeratore con il <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfaccia. Fornisce inoltre l'accesso a tutti di oggetti punto di connessione secondaria, ciascuno dei quali implementa il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia.  
  
2.  Qualsiasi oggetto è responsabile dell'implementazione un' <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> evento. Nella finestra **Proprietà** verrà indicato l'evento impostato tramite `IConnection`.  
  
3.  Un punto di connessione controlla il numero di connessioni (uno o più) consente nella propria implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un punto di connessione che consente una sola interfaccia può restituire <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> dal <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> (metodo).  
  
4.  Un client può chiamare le `IConnection` interfaccia per ottenere l'accesso a un oggetto secondario enumeratore con il <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfaccia. Il <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfaccia è quindi possibile chiamare per enumerare i punti di connessione per ogni ID (IID) dell'interfaccia in uscita.  
  
5.  `IConnection` può anche essere chiamato per ottenere l'accesso agli oggetti secondari di punto di connessione con il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia per ogni IID in uscita. Tramite il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia, un client avvia o termina un ciclo consultivo con l'oggetto collegabile e la sincronizzazione del client. Il client può anche chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia per ottenere un oggetto enumeratore con il <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interfaccia per enumerare le connessioni note.  
  
## <a name="see-also"></a>Vedere anche  
 [Annuncio della selezione della finestra proprietà di rilevamento](../misc/announcing-property-window-selection-tracking.md)   
 [Estensione delle proprietà](../extensibility/internals/extending-properties.md)