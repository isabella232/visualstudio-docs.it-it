---
title: 'Procedura: Implementare la gestione di annullamento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0cd5c72f8f423ec8ace409cafa82a1e42c6eaf90
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112611"
---
# <a name="how-to-implement-undo-management"></a>Procedura: Gestione dell'annullamento implementare
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'interfaccia primaria usata per la gestione dell'annullamento è <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, che viene implementato dall'ambiente. Per supportare la gestione dell'annullamento, implementare le unità di annullamento separato (vale a dire <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, che può contenere più i singoli passaggi.  
  
 Modalità di implementazione di gestione dell'annullamento varia a seconda se l'editor supporta più visualizzazioni o meno. Nelle sezioni seguenti vengono descritti in dettaglio le procedure per ogni implementazione.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Casi in cui un editor supporta una singola visualizzazione  
 In questo scenario, l'editor non supporta più visualizzazioni. È presente solo un editor e un solo documento, e supporta l'annullamento. Utilizzare la procedura seguente per implementare la gestione di annullamento.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Per supportare la gestione di annullamento per un editor a visualizzazione singola  
  
1. Chiamare `QueryInterface` nella `IServiceProvider` interfaccia nella cornice `IOleUndoManager`, dall'oggetto di visualizzazione del documento per la gestione degli annullamenti di accesso (`IID_IOLEUndoManager`).  
  
2. Quando una visualizzazione viene individuata in una cornice di finestra, ottiene un puntatore a sito, che può usare per chiamare `QueryInterface` per `IServiceProvider`.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Casi in cui un editor supporta più visualizzazioni  
 Se si dispone di separazione di documento e visualizzazione, è in genere una gestione degli annullamenti associata al documento. Tutte le unità di annullamento vengono posizionate in una gestione degli annullamenti associata con l'oggetto dati del documento.  
  
 Invece di visualizzare l'esecuzione di query per la gestione degli annullamenti, di cui è presente una per ogni visualizzazione, i dati del documento object chiama <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> per creare un'istanza di gestione degli annullamenti, specificando un identificatore di classe di CLSID_OLEUndoManager. L'identificatore di classe è definita nel file OCUNDOID.h.  
  
 Quando si usa <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> per creare l'istanza di gestione di annullamento, usare la procedura seguente per associare il gestore di annullamento nell'ambiente.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Per associare il gestore di annullamento nell'ambiente  
  
1. Chiamare `QueryInterface` sull'oggetto restituito da <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> per `IID_IOleUndoManager`. Il puntatore per Store <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2. Chiamare `QueryInterface` sul `IOleUndoManager` per `IID_IOleCommandTarget`. Il puntatore per Store <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3. Inoltro del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> chiamate all'oggetto memorizzato `IOleCommandTarget` interfaccia per i comandi StandardCommandSet97 seguenti:  
  
   - cmdidUndo  
  
   - cmdidMultiLevelUndo  
  
   - cmdidRedo  
  
   - cmdidMultiLevelRedo  
  
   - cmdidMultiLevelUndoList  
  
   - cmdidMultiLevelRedoList  
  
4. Chiamare `QueryInterface` sul `IOleUndoManager` per `IID_IVsChangeTrackingUndoManager`. Il puntatore per Store <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
    Usare il puntatore alla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> per chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>e il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> metodi.  
  
5. Chiamare `QueryInterface` sul `IOleUndoManager` per `IID_IVsLinkCapableUndoManager`.  
  
6. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> con il documento, che deve inoltre implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> interfaccia. Quando la chiusura del documento, chiamare `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7. Quando la chiusura del documento, chiamare `QueryInterface` nella gestione degli annullamenti per `IID_IVsLifetimeControlledObject`.  
  
8. Chiamare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Quando vengono apportate modifiche al documento, chiamare <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> del gestore con un `OleUndoUnit` classe. Il <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> metodo mantiene un riferimento all'oggetto, generalmente si rilasciarlo subito dopo il <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
   Il `OleUndoManager` classe rappresenta un'istanza dello stack di singola operazione di annullamento. Pertanto, è disponibile un oggetto di gestione di annullamento per ogni entità di dati si tiene traccia di annullamento o ripristino.  
  
> [!NOTE]
>  Anche se l'oggetto di gestore di annullamento è ampiamente utilizzato da editor di testo, è un componente generale che non dispone di alcun supporto specifico per l'editor di testo. Se si desidera supportare l'annullamento a più livelli o ripristino, è possibile utilizzare questa oggetto a tale scopo.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Procedura: Cancella lo Stack di annullamento](../extensibility/how-to-clear-the-undo-stack.md)
