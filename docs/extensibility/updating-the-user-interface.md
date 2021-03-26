---
title: Aggiornamento dell'interfaccia utente | Microsoft Docs
description: Informazioni su come aggiungere codice per aggiornare l'interfaccia utente dopo aver implementato un nuovo comando nel pacchetto VSPackage.
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
ms.workload:
- vssdk
ms.openlocfilehash: e5aecf97683ff22b8c384acf1c8ffb83e671fa57
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073729"
---
# <a name="updating-the-user-interface"></a>Aggiornamento dell'interfaccia utente
Dopo aver implementato un comando, è possibile aggiungere il codice per aggiornare l'interfaccia utente con lo stato dei nuovi comandi.

 In una tipica applicazione Win32, il set di comandi può essere sottoposto a polling continuo e lo stato dei singoli comandi può essere modificato durante la visualizzazione da parte dell'utente. Tuttavia, poiché la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell può ospitare un numero illimitato di pacchetti VSPackage, il polling esteso può ridurre la velocità di risposta, in particolare il polling tra assembly di interoperabilità tra codice gestito e com.

### <a name="to-update-the-ui"></a>Per aggiornare l'interfaccia utente

1. Effettuare uno dei passaggi indicati di seguito.

    - Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> .

         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>È possibile ottenere un'interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> servizio, come indicato di seguito.

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

         Se il parametro di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> è diverso da zero ( `TRUE` ), l'aggiornamento viene eseguito in modo sincrono e immediato. È consigliabile passare zero ( `FALSE` ) per questo parametro per garantire prestazioni ottimali. Se si desidera evitare la memorizzazione nella cache, applicare il `DontCache` flag quando si crea il comando nel file con estensione vsct. Tuttavia, è possibile utilizzare il flag con cautela o ridurre le prestazioni. Per ulteriori informazioni sui flag di comando, vedere la documentazione relativa all' [elemento del flag di comando](../extensibility/command-flag-element.md) .

    - Nei pacchetti VSPackage che ospitano un controllo ActiveX usando il modello di attivazione sul posto in una finestra, potrebbe essere più pratico usare il <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metodo. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> metodo nell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia e il <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metodo nell' <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaccia sono funzionalmente equivalenti. Entrambi gli ambienti eseguono nuovamente la query sullo stato di tutti i comandi. In genere, un aggiornamento non viene eseguito immediatamente. Un aggiornamento viene invece posticipato fino al tempo di inattività. La shell memorizza nella cache lo stato del comando per garantire prestazioni ottimali. Se si desidera evitare la memorizzazione nella cache, applicare il `DontCache` flag quando si crea il comando nel file con estensione vsct. Tuttavia, usare il flag con cautela perché le prestazioni potrebbero ridursi.

         Si noti che è possibile ottenere l' <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaccia chiamando il `QueryInterface` metodo su un <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> oggetto o ottenendo l'interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> servizio.

## <a name="see-also"></a>Vedi anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementazione](../extensibility/internals/command-implementation.md)
