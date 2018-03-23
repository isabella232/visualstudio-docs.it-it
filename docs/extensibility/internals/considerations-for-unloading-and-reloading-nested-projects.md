---
title: Considerazioni per scaricare e ricaricare annidati progetti | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bfe39e82a9f15825a5328fe1950347add9d182bb
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerazioni per scaricare e ricaricare progetti annidati

Quando si implementano i tipi di progetto annidato, è necessario eseguire passaggi aggiuntivi quando si scarica e ricaricare i progetti. Per notificare correttamente listener per gli eventi della soluzione, è necessario aumentare in modo corretto il `OnBeforeUnloadProject` e `OnAfterLoadProject` eventi.

Uno dei motivi per la generazione di questi eventi è per controllo del codice sorgente (SCC). Non si desidera questo strumento consente di eliminare gli elementi dal server e quindi aggiungerli nuovamente come *nuove* se è presente un `Get` operazione dal controllo del codice sorgente. In tal caso, un nuovo file verrà caricato all'esterno di controllo del codice sorgente. È necessario scaricare e ricaricare tutti i file nel caso in cui sono diversi.

Chiamate di controllo codice sorgente `ReloadItem`. Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaccia per chiamare `OnBeforeUnloadProject` e `OnAfterLoadProject` per eliminare il progetto e ricrearlo. Quando si implementa l'interfaccia in questo modo, controllo configurazione sistema viene informato che il progetto è stato temporaneamente eliminato e aggiunto nuovamente. Pertanto, non interagisce SCC sul progetto come se il progetto è stata *effettivamente* eliminato e aggiunto nuovamente.

## <a name="reloading-projects"></a>Ricaricamento di progetti

Per supportare il ricaricamento di progetti annidati, si implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodo. Nell'implementazione di `ReloadItem`, si chiudere progetti annidati e quindi ricrearli.

In genere quando un progetto è stato ricaricato, l'IDE genera il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> eventi. Tuttavia, per i progetti annidati che vengono eliminati e ricaricati, nel progetto padre avvia il processo, non l'IDE. Poiché il progetto padre non genera gli eventi della soluzione e l'IDE non dispone di informazioni sull'inizializzazione del processo, non vengono generati gli eventi.

Per gestire questo processo, le chiamate di progetto padre `QueryInterface` nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaccia. `IVsFireSolutionEvents` sono disponibili funzioni che indicano l'IDE per generare il `OnBeforeUnloadProject` evento per scaricare il progetto annidato e quindi generare il `OnAfterLoadProject` evento ricaricare il progetto stesso.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)