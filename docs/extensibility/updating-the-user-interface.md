---
title: Aggiornamento del Interfaccia utente | Microsoft Docs
description: Informazioni su come aggiungere codice per aggiornare l'interfaccia utente dopo l'implementazione di un nuovo comando nel pacchetto VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 046484eaba6ff131d5f39522b7dc04460380c0f0aed0496acc537c9c60d522e5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413846"
---
# <a name="updating-the-user-interface"></a>Aggiornamento dell'interfaccia utente
Dopo aver implementato un comando, è possibile aggiungere codice per aggiornare l'interfaccia utente con lo stato dei nuovi comandi.

 In una tipica applicazione Win32 è possibile eseguire continuamente il polling del set di comandi e modificare lo stato dei singoli comandi quando l'utente li visualizza. Tuttavia, poiché la shell può ospitare un numero illimitato di VSPackage, il polling esteso potrebbe ridurre la velocità di risposta, in particolare il polling tra assembly di interoperabilità tra codice [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gestito e COM.

### <a name="to-update-the-ui"></a>Per aggiornare l'interfaccia utente

1. Effettuare uno dei passaggi indicati di seguito.

    - Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> .

         È <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> possibile ottenere un'interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> servizio, come indicato di seguito.

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

         Se il parametro di è diverso da zero ( ), l'aggiornamento viene eseguito in modo sincrono <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> `TRUE` e immediato. È consigliabile passare zero ( `FALSE` ) per questo parametro per garantire prestazioni ottimali. Se si vuole evitare la memorizzazione nella cache, applicare il `DontCache` flag quando si crea il comando nel file con estensione vsct. Tuttavia, usare il flag con cautela o le prestazioni potrebbero diminuire. Per altre informazioni sui flag di comando, vedere la documentazione [relativa all'elemento Command Flag.](../extensibility/command-flag-element.md)

    - Nei pacchetti VSPackage che ospitano un controllo ActiveX usando il modello di attivazione sul posto in una finestra, potrebbe essere più pratico usare il <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metodo . Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> nell'interfaccia e il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> nell'interfaccia sono equivalenti dal punto di vista funzionale. In entrambi i casi, l'ambiente esegue nuovamente una query sullo stato di tutti i comandi. In genere, un aggiornamento non viene eseguito immediatamente. Un aggiornamento viene invece posticipato fino al tempo di inattività. La shell memorizza nella cache lo stato del comando per garantire prestazioni ottimali. Se si vuole evitare la memorizzazione nella cache, applicare il `DontCache` flag quando si crea il comando nel file con estensione vsct. Tuttavia, usare il flag con cautela perché le prestazioni potrebbero diminuire.

         Si noti che è possibile ottenere l'interfaccia chiamando il metodo su un oggetto o <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> `QueryInterface` ottenendo <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> l'interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> servizio.

## <a name="see-also"></a>Vedi anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementazione](../extensibility/internals/command-implementation.md)
