---
title: Considerazioni per lo scaricamento e il ricaricamento di progetti nidificati Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab705953eea1fcac99883bb4f88c0e95eced108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709295"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerazioni per lo scaricamento e il ricaricamento di progetti annidatiConsiderations for unloading and reloading nested projects

Quando si implementano tipi di progetto annidati, è necessario eseguire passaggi aggiuntivi quando si scaricano e ricaricano i progetti. Per notificare correttamente i listener agli `OnBeforeUnloadProject` eventi `OnAfterLoadProject` della soluzione, è necessario generare correttamente gli eventi e .

Un motivo per generare questi eventi è per il controllo del codice sorgente (SCC). Non vuoi che SCC elimini gli elementi dal server *new* e poi li `Get` aggiuschi di nuovo come nuovo se c'è un'operazione da SCC. In tal caso, un nuovo file verrebbe caricato da SCC. Dovresti scaricare e ricaricare tutti i file nel caso in cui siano diversi.

Il controllo `ReloadItem`del codice sorgente chiama . Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> l'interfaccia per chiamare `OnBeforeUnloadProject` ed `OnAfterLoadProject` eliminare il progetto e ricrearlo. Quando si implementa l'interfaccia in questo modo, SCC viene informato che il progetto è stato temporaneamente eliminato e aggiunto nuovamente. Pertanto, SCC non opera sul progetto come se il progetto è stato *effettivamente* eliminato e aggiunto nuovamente.

## <a name="reload-projects"></a>Ricaricare i progetti

Per supportare il ricaricamento di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> progetti annidati, implementare il metodo . Nell'implementazione `ReloadItem`di , chiudere i progetti annidati e quindi ricrearli.

In genere quando un progetto viene ricaricato, l'IDE genera gli <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> eventi e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> . Tuttavia, per i progetti annidati che vengono eliminati e ricaricati, il progetto padre avvia il processo, non l'IDE. Poiché il progetto padre non genera eventi della soluzione e l'IDE non dispone di informazioni sull'inizializzazione del processo, gli eventi non vengono generati.

Per gestire questo processo, `QueryInterface` il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> progetto padre chiama sull'interfaccia. `IVsFireSolutionEvents`dispone di funzioni che indicano `OnBeforeUnloadProject` all'IDE di generare l'evento per scaricare il progetto annidato e quindi generare l'evento `OnAfterLoadProject` per ricaricare lo stesso progetto.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Nidificare i progetti](../../extensibility/internals/nesting-projects.md)
