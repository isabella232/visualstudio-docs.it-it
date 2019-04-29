---
title: Considerazioni per lo scaricamento e il ricaricamento annidati progetti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5738a5e8cf01466dd632797c3f92ffd135a44
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861335"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerazioni per scaricare e ricaricare i progetti annidati

Quando si implementano i tipi di progetto annidato, è necessario eseguire passaggi aggiuntivi quando si scarica e ricaricare i progetti. Per comunicare correttamente i listener di eventi della soluzione, è necessario aumentare in modo corretto le `OnBeforeUnloadProject` e `OnAfterLoadProject` eventi.

Uno dei motivi per la generazione di questi eventi è di controllo del codice sorgente (SCC). Non si desidera che controllo del codice sorgente per eliminare gli elementi dal server e quindi aggiungerli nuovamente come *nuove* se è presente un `Get` operazione dal controllo del codice sorgente. In tal caso, potrebbe caricare un nuovo file da SCC. È necessario scaricare e ricaricare tutti i file nel caso in cui siano diversi.

Le chiamate di controllo codice sorgente `ReloadItem`. Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaccia da chiamare `OnBeforeUnloadProject` e `OnAfterLoadProject` per eliminare il progetto e ricrearlo. Quando si implementa l'interfaccia in questo modo, controllo configurazione sistema viene informato che il progetto è stato temporaneamente eliminato e aggiunto di nuovo. Di conseguenza, controllo del codice sorgente non opera sul progetto come se il progetto è stato *effettivamente* eliminato e aggiunto di nuovo.

## <a name="reload-projects"></a>Ricaricamento di progetti

Per supportare il ricaricamento di progetti annidati, si implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (metodo). Nell'implementazione di `ReloadItem`, si chiude i progetti annidati e quindi crearli di nuovo.

In genere quando un progetto viene ricaricato, l'IDE genera il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> eventi. Tuttavia, per i progetti annidati che vengono eliminati e ricaricati, il progetto principale avvia il processo, non l'IDE. Poiché il progetto principale non genera eventi della soluzione e l'IDE non dispone di informazioni sull'inizializzazione del processo, non vengono generati gli eventi.

Per gestire questo processo, le chiamate di progetto padre `QueryInterface` nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaccia. `IVsFireSolutionEvents` sono disponibili funzioni che indicano l'IDE per generare il `OnBeforeUnloadProject` eventi per scaricare il progetto annidato e quindi generare il `OnAfterLoadProject` evento ricaricare il progetto stesso.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Progetti di annidamento](../../extensibility/internals/nesting-projects.md)