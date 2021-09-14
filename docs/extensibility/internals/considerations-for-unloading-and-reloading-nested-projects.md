---
title: Scaricamento e ricaricamento di progetti annidati
description: Informazioni sui passaggi aggiuntivi da eseguire durante lo scaricamento e il ricaricamento di progetti annidati in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4b320829afd749a6aac82c71155bfed9e5766eba
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626195"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerazioni per lo scaricamento e il ricaricamento di progetti annidati

Quando si implementano tipi di progetto annidati, è necessario eseguire passaggi aggiuntivi quando si scaricano e ricaricano i progetti. Per notificare correttamente ai listener gli eventi della soluzione, è necessario generare correttamente gli `OnBeforeUnloadProject` eventi `OnAfterLoadProject` e .

Uno dei motivi per generare questi eventi è il controllo del codice sorgente (SCC). Non si vuole che SCC elimini gli elementi dal  server e quindi li aggiunge di nuovo come nuovi se è presente un'operazione `Get` da SCC. In tal caso, un nuovo file viene caricato all'uscita da SCC. È necessario scaricare e ricaricare tutti i file nel caso in cui siano diversi.

Il controllo del codice sorgente chiama `ReloadItem` . Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> l'interfaccia `OnBeforeUnloadProject` per chiamare e per eliminare il progetto e `OnAfterLoadProject` crearlo di nuovo. Quando si implementa l'interfaccia in questo modo, SCC viene informato che il progetto è stato temporaneamente eliminato e aggiunto nuovamente. Pertanto, SCC non opera sul progetto come se il progetto fosse stato *effettivamente* eliminato e aggiunto di nuovo.

## <a name="reload-projects"></a>Ricaricare i progetti

Per supportare il ricaricamento di progetti annidati, implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodo . Nell'implementazione `ReloadItem` di , chiudere i progetti annidati e quindi crearli nuovamente.

In genere, quando un progetto viene ricaricato, l'IDE genera gli <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> eventi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> e . Tuttavia, per i progetti annidati che vengono eliminati e ricaricati, il progetto padre avvia il processo, non l'IDE. Poiché il progetto padre non genera eventi della soluzione e l'IDE non dispone di informazioni sull'inizializzazione del processo, gli eventi non vengono generati.

Per gestire questo processo, il progetto padre chiama `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> sull'interfaccia . `IVsFireSolutionEvents` dispone di funzioni che specificano all'IDE di generare l'evento per scaricare il progetto annidato e quindi generare l'evento per `OnBeforeUnloadProject` `OnAfterLoadProject` ricaricare lo stesso progetto.

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Annidare progetti](../../extensibility/internals/nesting-projects.md)
