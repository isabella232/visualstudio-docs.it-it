---
title: Aggiornamento dell'interfaccia utente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f492a7d5c42fc18ac2a5516d4549a024d37b7d1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981831"
---
# <a name="updating-the-user-interface"></a>Aggiornamento dell'interfaccia utente
Dopo aver implementato un comando, è possibile aggiungere codice per aggiornare l'interfaccia utente con lo stato dei nuovi comandi.  
  
 In una tipica applicazione Win32, il set di comandi possa eseguire il polling in modo continuo e lo stato dei singoli comandi può essere modificato perché l'utente visualizza li. Tuttavia, poiché il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell può ospitare un numero illimitato di pacchetti VSPackage, polling complete potrebbe ridurre la velocità di risposta, in particolare il polling in assembly di interoperabilità tra codice gestito e COM.  
  
### <a name="to-update-the-ui"></a>Per aggiornare l'interfaccia utente  
  
1.  Effettuare uno dei passaggi indicati di seguito.  
  
    -   Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.  
  
         Un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia può essere ottenuta dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service, come indicato di seguito.  
  
        ```csharp  
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)  
        {  
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));  
            if (vsShell != null)  
            {  
                int hr = vsShell.UpdateCommandUI(0);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
            }  
        }  
  
        ```  
  
         Se il parametro del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> è diverso da zero (`TRUE`), quindi l'aggiornamento viene eseguito in modo sincrono e immediatamente. È consigliabile passare zero (`FALSE`) per questo parametro garantire prestazioni ottimali. Se si desidera evitare la memorizzazione nella cache, applicare il `DontCache` flag quando si crea il comando nel file con estensione vsct. Tuttavia, usare il flag con cautela o può ridurre le prestazioni. Per altre informazioni sui flag di comando, vedere la [elemento Commandflag](../extensibility/command-flag-element.md) documentazione.  
  
    -   Nei pacchetti VSPackage che ospitano un controllo ActiveX utilizzando il modello di attivazione sul posto in una finestra, potrebbe essere più opportuno usare il <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> (metodo). Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> metodo nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia e il <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metodo nella <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaccia sono funzionalmente equivalenti. Sia che l'ambiente nuovamente lo stato di tutti i comandi di query. In genere, un aggiornamento non viene eseguito immediatamente. Al contrario, un aggiornamento viene posticipato fino al tempo di inattività. Le shell vengono memorizzati nella cache lo stato del comando per aiutare a garantire prestazioni ottimali. Se si desidera evitare la memorizzazione nella cache, applicare il `DontCache` flag quando si crea il comando nel file con estensione vsct. Tuttavia, usare il flag con cautela perché può ridurre le prestazioni.  
  
         Si noti che è possibile ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaccia chiamando il `QueryInterface` metodo su un <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> dell'oggetto o per ottenere l'interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> servizio.  
  
## <a name="see-also"></a>Vedere anche  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementazione](../extensibility/internals/command-implementation.md)