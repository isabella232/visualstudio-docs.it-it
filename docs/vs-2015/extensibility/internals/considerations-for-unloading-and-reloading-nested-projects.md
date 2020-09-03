---
title: Considerazioni per lo scaricamento e il ricaricamento di progetti annidati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65145530c8cd6b68b82391a09b395bb8c9a61117
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197006"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerazioni per lo scaricamento e il ricaricamento di progetti annidati
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando si implementano tipi di progetto annidati, è necessario eseguire passaggi aggiuntivi quando si scaricano e ricaricano i progetti. Per notificare correttamente ai listener gli eventi della soluzione, è necessario generare correttamente gli `OnBeforeUnloadProject` `OnAfterLoadProject` eventi e.  
  
 Un motivo per cui è necessario generare questi eventi in questo modo è che non si vuole che il controllo del codice sorgente (SCC) elimini gli elementi dal server e li aggiunga come un elemento nuovo se è presente un' `Get` operazione da SCC. In tal caso, viene caricato un nuovo file fuori da SCC ed è necessario scaricare e ricaricare tutti i file nel caso siano diversi. Chiamate SCC `ReloadItem` . L'implementazione di tale chiamata consiste nell'eliminare il progetto e ricrearlo implementando `IVsFireSolutionEvents` per chiamare `OnBeforeUnloadProject` e `OnAfterLoadProject` . Quando si esegue questa implementazione, il SCC viene informato che il progetto è stato temporaneamente eliminato e aggiunto nuovamente. Per questo motivo, SCC non opera sul progetto come se il progetto fosse stato effettivamente eliminato dal server e quindi aggiunto nuovamente.  
  
## <a name="reloading-projects"></a>Ricaricamento di progetti  
 Per supportare il ricaricamento di progetti annidati, è necessario implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodo. Nell'implementazione di `ReloadItem` è possibile chiudere i progetti annidati e quindi ricrearli.  
  
 In genere, quando un progetto viene ricaricato, l'IDE genera gli <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` eventi e. Tuttavia, per i progetti annidati che verranno eliminati e ricaricati, il progetto padre avvierà il processo, non l'IDE. Poiché il progetto padre non genera eventi di soluzione e l'IDE non dispone di informazioni sull'inizializzazione del processo, gli eventi non vengono generati.  
  
 Per gestire questo processo, il progetto padre chiama `QueryInterface` sull' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaccia dall' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interfaccia. `IVsFireSolutionEvents` dispone di funzioni che indicano all'IDE di generare l' `OnBeforeUnloadProject` evento per scaricare il progetto annidato e quindi generare l' `OnAfterLoadProject` evento per ricaricare lo stesso progetto.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)
