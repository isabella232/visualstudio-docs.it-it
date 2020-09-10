---
title: Scaricamento e ricaricamento di progetti annidati
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
ms.openlocfilehash: 86f8f2f02258bc55f3221635fddab8ecdaaa3cf7
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743237"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerazioni per lo scaricamento e il ricaricamento di progetti annidati

Quando si implementano tipi di progetto annidati, è necessario eseguire passaggi aggiuntivi quando si scaricano e ricaricano i progetti. Per notificare correttamente ai listener gli eventi della soluzione, è necessario generare correttamente gli `OnBeforeUnloadProject` `OnAfterLoadProject` eventi e.

Uno dei motivi per cui è necessario generare questi eventi è il controllo del codice sorgente (SCC). Non si vuole che SCC elimini gli elementi dal server e li aggiunga nuovamente come *nuovi* se è presente un' `Get` operazione da SCC. In tal caso, verrà caricato un nuovo file fuori da SCC. È necessario scaricare e ricaricare tutti i file se sono diversi.

Chiamate del controllo del codice sorgente `ReloadItem` . Implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaccia per chiamare `OnBeforeUnloadProject` ed `OnAfterLoadProject` eliminare il progetto e ricrearlo. Quando si implementa l'interfaccia in questo modo, SCC viene informato che il progetto è stato temporaneamente eliminato e aggiunto nuovamente. Quindi, SCC non opera sul progetto come se il progetto fosse stato *effettivamente* eliminato e aggiunto nuovamente.

## <a name="reload-projects"></a>Ricarica progetti

Per supportare il ricaricamento di progetti annidati, è necessario implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodo. Nell'implementazione di `ReloadItem` è possibile chiudere i progetti annidati e quindi ricrearli.

In genere, quando un progetto viene ricaricato, l'IDE genera gli <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> eventi e. Tuttavia, per i progetti annidati che vengono eliminati e ricaricati, il progetto padre avvia il processo, non l'IDE. Poiché il progetto padre non genera eventi di soluzione e l'IDE non contiene informazioni sull'inizializzazione del processo, gli eventi non vengono generati.

Per gestire questo processo, il progetto padre chiama `QueryInterface` sull' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaccia. `IVsFireSolutionEvents` dispone di funzioni che indicano all'IDE di generare l' `OnBeforeUnloadProject` evento per scaricare il progetto annidato e quindi generare l' `OnAfterLoadProject` evento per ricaricare lo stesso progetto.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Annida progetti](../../extensibility/internals/nesting-projects.md)
