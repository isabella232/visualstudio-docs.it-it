---
title: Aggiornamento dell'interfaccia utente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf41a41e68aa73e07bdcafe8bcdcd335fff6e6eb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718791"
---
# <a name="updating-the-user-interface"></a>Aggiornamento dell'interfaccia utente
Dopo aver implementato un comando, è possibile aggiungere il codice per aggiornare l'interfaccia utente con lo stato dei nuovi comandi.

 In una tipica applicazione Win32, il set di comandi può essere sottoposto a polling continuo e lo stato dei singoli comandi può essere modificato durante la visualizzazione da parte dell'utente. Tuttavia, poiché la shell di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] può ospitare un numero illimitato di pacchetti VSPackage, il polling esteso può ridurre la velocità di risposta, in particolare il polling tra assembly di interoperabilità tra codice gestito e COM.

### <a name="to-update-the-ui"></a>Per aggiornare l'interfaccia utente

1. Effettuare uno dei passaggi indicati di seguito.

    - Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.

         È possibile ottenere un'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> dal servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, come indicato di seguito.

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

         Se il parametro del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> è diverso da zero (`TRUE`), l'aggiornamento viene eseguito in modo sincrono e immediato. È consigliabile passare zero (`FALSE`) per questo parametro per garantire prestazioni ottimali. Se si desidera evitare la memorizzazione nella cache, applicare il flag di `DontCache` quando si crea il comando nel file con estensione vsct. Tuttavia, è possibile utilizzare il flag con cautela o ridurre le prestazioni. Per ulteriori informazioni sui flag di comando, vedere la documentazione relativa all' [elemento del flag di comando](../extensibility/command-flag-element.md) .

    - Nei pacchetti VSPackage che ospitano un controllo ActiveX usando il modello di attivazione sul posto in una finestra, potrebbe essere più pratico usare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>. Il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> nell'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> e il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> nell'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> sono equivalenti dal punto di vista funzionale. Entrambi gli ambienti eseguono nuovamente la query sullo stato di tutti i comandi. In genere, un aggiornamento non viene eseguito immediatamente. Un aggiornamento viene invece posticipato fino al tempo di inattività. La shell memorizza nella cache lo stato del comando per garantire prestazioni ottimali. Se si desidera evitare la memorizzazione nella cache, applicare il flag di `DontCache` quando si crea il comando nel file con estensione vsct. Tuttavia, usare il flag con cautela perché le prestazioni potrebbero ridursi.

         Si noti che è possibile ottenere l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> chiamando il metodo `QueryInterface` su un oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> o ottenendo l'interfaccia dal servizio <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>.

## <a name="see-also"></a>Vedere anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementazione](../extensibility/internals/command-implementation.md)