---
title: Considerazioni per lo scaricamento e il ricaricamento annidati progetti | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1712c05ab1bd6dbf32537d4306517ddf189b4084
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277562"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerazioni per lo scaricamento e il ricaricamento di progetti annidati
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando si implementano i tipi di progetto annidato, è necessario eseguire passaggi aggiuntivi quando si scarica e ricaricare i progetti. Per comunicare correttamente i listener di eventi della soluzione, è necessario aumentare in modo corretto le `OnBeforeUnloadProject` e `OnAfterLoadProject` eventi.  
  
 Uno dei motivi è necessario aumentare questi eventi in questo modo è che non si desidera controllo del codice sorgente (SCC) per eliminare gli elementi dal server e quindi aggiungerli nuovamente come qualcosa di nuovo se è presente un `Get` operazione dal controllo del codice sorgente. In tal caso, un nuovo file verranno caricato da SCC ed è necessario scaricare e ricaricare tutti i file nel caso in cui sono diversi. Le chiamate di controllo del codice sorgente `ReloadItem`. L'implementazione di tale chiamata consiste nell'eliminare il progetto e ricrearlo nuovamente implementando `IVsFireSolutionEvents` chiamare `OnBeforeUnloadProject` e `OnAfterLoadProject`. Quando si esegue questa implementazione, il controllo del codice sorgente viene informato che il progetto è stato temporaneamente eliminato e aggiunto di nuovo. Pertanto, il controllo del codice sorgente non opera sul progetto come se il progetto è stato effettivamente eliminato dal server e quindi aggiunto nuovamente.  
  
## <a name="reloading-projects"></a>Ricaricamento di progetti  
 Per supportare il ricaricamento di progetti annidati, si implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (metodo). Nell'implementazione di `ReloadItem`, si chiude i progetti annidati e quindi crearli di nuovo.  
  
 In genere quando un progetto viene ricaricato, l'IDE genera il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> e il `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` gli eventi. Tuttavia, per i progetti annidati che verranno eliminati e ricaricati, il progetto principale avvia il processo, non l'IDE. Poiché il progetto principale non genera eventi della soluzione e l'IDE non dispone di informazioni sull'inizializzazione del processo, gli eventi non vengono generati.  
  
 Per gestire questo processo, le chiamate di progetto padre `QueryInterface` nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaccia disattivato il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interfaccia. `IVsFireSolutionEvents` sono disponibili funzioni che indicano l'IDE per generare il `OnBeforeUnloadProject` eventi per scaricare il progetto annidato e quindi generare il `OnAfterLoadProject` evento ricaricare il progetto stesso.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)

