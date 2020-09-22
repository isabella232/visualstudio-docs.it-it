---
title: 'Procedura: implementare la gestione di annullamento | Microsoft Docs'
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
ms.openlocfilehash: 0f3d56ae02718f5dfdf373eeeb6aff774d11931e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840151"
---
# <a name="how-to-implement-undo-management"></a>Procedura: Implementare la gestione della fase di rollback
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'interfaccia primaria utilizzata per la gestione dell'annullamento è <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> , implementata dall'ambiente. Per supportare la gestione degli annullamenti, implementare unità di annullamento separate, ovvero, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> che possono contenere più singoli passaggi.  
  
 La modalità di implementazione della gestione degli annullamenti varia a seconda che l'editor supporti o meno più viste. Le procedure per ogni implementazione sono descritte in dettaglio nelle sezioni seguenti.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Casi in cui un editor supporta una sola visualizzazione  
 In questo scenario, l'editor non supporta più visualizzazioni. È disponibile un solo editor e un solo documento, che supportano l'annullamento. Utilizzare la procedura seguente per implementare la gestione degli annullamenti.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Per supportare la gestione degli annullamenti per un editor a visualizzazione singola  
  
1. Chiamare `QueryInterface` sull' `IServiceProvider` interfaccia sulla cornice della finestra per `IOleUndoManager` , dall'oggetto visualizzazione del documento per accedere al gestore di annullamento ( `IID_IOLEUndoManager` ).  
  
2. Quando una visualizzazione viene posizionata in una cornice della finestra, ottiene un puntatore del sito, che può essere usato per chiamare `QueryInterface` per `IServiceProvider` .  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Casi in cui un editor supporta più visualizzazioni  
 Se è presente una separazione tra documenti e viste, in genere esiste una gestione degli annullamenti associata al documento stesso. Tutte le unità di annullamento vengono inserite in un gestore di annullamento associato all'oggetto dati del documento.  
  
 Anziché visualizzare la query per il gestore di annullamento, di cui ne esiste uno per ogni visualizzazione, l'oggetto dati del documento chiama <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> per creare un'istanza del gestore di annullamento, specificando un identificatore di classe di CLSID_OLEUndoManager. L'identificatore di classe è definito nel file OCUNDOID. h.  
  
 Quando <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> si utilizza per creare un'istanza del gestore di annullamento, utilizzare la procedura seguente per associare il gestore di annullamento all'ambiente.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Per associare il gestore di annullamento all'ambiente  
  
1. Chiamare `QueryInterface` sull'oggetto restituito da <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> per `IID_IOleUndoManager` . Archiviare il puntatore a <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> .  
  
2. Chiamare `QueryInterface` `IOleUndoManager` per `IID_IOleCommandTarget` . Archiviare il puntatore a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
3. Inoltrare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> chiamate e nell'interfaccia archiviata `IOleCommandTarget` per i comandi StandardCommandSet97 seguenti:  
  
   - cmdidUndo  
  
   - cmdidMultiLevelUndo  
  
   - cmdidRedo  
  
   - cmdidMultiLevelRedo  
  
   - cmdidMultiLevelUndoList  
  
   - cmdidMultiLevelRedoList  
  
4. Chiamare `QueryInterface` `IOleUndoManager` per `IID_IVsChangeTrackingUndoManager` . Archiviare il puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> .  
  
    Usare il puntatore a per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> chiamare i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A> metodi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> .  
  
5. Chiamare `QueryInterface` `IOleUndoManager` per `IID_IVsLinkCapableUndoManager` .  
  
6. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> con il documento, che dovrebbe implementare anche l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> interfaccia. Quando il documento viene chiuso, chiamare `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient` .  
  
7. Quando il documento è chiuso, chiamare il `QueryInterface` gestore di annullamento per `IID_IVsLifetimeControlledObject` .  
  
8. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Quando vengono apportate modifiche al documento, chiamare <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> sul Manager con una `OleUndoUnit` classe. Il <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> metodo mantiene un riferimento all'oggetto, quindi in genere viene rilasciato immediatamente dopo <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> .  
  
   La `OleUndoManager` classe rappresenta una singola istanza dello stack di annullamento. Per ogni entità di dati rilevata per l'annullamento o il rollforward è quindi presente un oggetto del gestore di annullamento.  
  
> [!NOTE]
> Mentre l'oggetto gestione annullamento viene utilizzato estensivamente dall'editor di testo, si tratta di un componente generale che non dispone di supporto specifico per l'editor di testo. Se si desidera supportare l'annullamento o la ripetizione a più livelli, è possibile utilizzare questo oggetto a tale scopo.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Procedura: Cancellare lo stack di fasi di rollback](../extensibility/how-to-clear-the-undo-stack.md)
