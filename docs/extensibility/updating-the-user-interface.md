---
title: Aggiornamento dell'interfaccia utente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c51ae790eb35645fbe9aec5d9c422e1051aaa69
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698878"
---
# <a name="updating-the-user-interface"></a>Aggiornamento dell'interfaccia utente
Dopo aver implementato un comando, è possibile aggiungere codice per aggiornare l'interfaccia utente con lo stato dei nuovi comandi.

 In una tipica applicazione Win32, il set di comandi può essere sottoposto a polling continuo e lo stato dei singoli comandi può essere regolato man mano che l'utente li visualizza. Tuttavia, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] poiché la shell può ospitare un numero illimitato di VSPackage, polling esteso potrebbe ridurre la velocità di risposta, in particolare il polling tra gli assembly di interoperabilità tra codice gestito e COM.

### <a name="to-update-the-ui"></a>Per aggiornare l'interfaccia utente

1. Effettuare uno dei passaggi indicati di seguito.

    - Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> .

         Un'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> può essere <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> ottenuta dal servizio, come indicato di seguito.

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

         Se il parametro di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> è`TRUE`diverso da zero ( ), l'aggiornamento viene eseguito in modo sincrono e immediato. Si consiglia di passare`FALSE`zero ( ) per questo parametro per mantenere buone prestazioni. Se si desidera evitare la `DontCache` memorizzazione nella cache, applicare il flag quando si crea il comando nel file vsct. Tuttavia, utilizzare il flag con cautela o le prestazioni potrebbero diminuire. Per altre informazioni sui flag di comando, vedere la documentazione relativa [all'elemento Flag di comando.](../extensibility/command-flag-element.md)

    - Nei package VS che ospitano un controllo ActiveX utilizzando il modello di attivazione <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> sul posto in una finestra, potrebbe essere più conveniente utilizzare il metodo. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> nell'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> il metodo nell'interfaccia sono equivalenti dal punto di lavoro. Entrambi fanno sì che l'ambiente ri-query lo stato di tutti i comandi. In genere, un aggiornamento non viene eseguito immediatamente. Al contrario, un aggiornamento viene ritardato fino al tempo di inattività. La shell memorizza nella cache lo stato del comando per mantenere buone prestazioni. Se si desidera evitare la `DontCache` memorizzazione nella cache, applicare il flag quando si crea il comando nel file vsct. Tuttavia, utilizzare il flag con cautela perché le prestazioni potrebbero diminuire.

         Si noti che <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> è possibile `QueryInterface` ottenere <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> l'interfaccia chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> su un oggetto o ottenendo l'interfaccia dal servizio.

## <a name="see-also"></a>Vedere anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementazione](../extensibility/internals/command-implementation.md)
