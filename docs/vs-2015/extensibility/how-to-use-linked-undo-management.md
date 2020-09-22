---
title: 'Procedura: utilizzare la gestione di annullamento collegata | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67d0d173909b8cdfe2eaf0d56aa5c99c437d5ad8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839520"
---
# <a name="how-to-use-linked-undo-management"></a>Procedura: Usare la gestione della fase di rollback collegata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il rollback collegato consente all'utente di annullare contemporaneamente le stesse modifiche in più file. Ad esempio, le modifiche di testo simultanee tra più file di programma, ad esempio un file di intestazione e un file di Visual C++, sono una transazione di annullamento collegata. La funzionalità di annullamento collegata è incorporata nell'implementazione dell'ambiente del gestore degli annullamenti e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> consente di modificare questa funzionalità. Il rollback collegato viene implementato da un'unità di annullamento padre che consente di collegare gli stack di annullamento separati per essere considerati come una singola unità di annullamento. La procedura per l'utilizzo dell'annullamento collegato è descritta in dettaglio nella sezione seguente.  
  
### <a name="to-use-linked-undo"></a>Per utilizzare il comando Annulla collegato  
  
1. Chiamare `QueryService` `SVsLinkedUndoManager` per ottenere un puntatore a `IVsLinkedUndoTransactionManager` .  
  
2. Creare l'unità di annullamento collegata padre iniziale chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A> . In questo modo viene impostato il punto di partenza per un set di stack di annullamento da raggruppare in stack di annullamento collegati. Nel `OpenLinkedUndo` metodo sarà inoltre necessario specificare se si desidera che il rollback collegato sia rigoroso o non rigoroso. Il comportamento di annullamento collegato non rigoroso significa che alcuni documenti con elementi di pari livello collegati possono chiudere e lasciare gli altri elementi di pari livello collegati nei relativi stack. Il comportamento di annullamento del collegamento Strict specifica che tutti gli stack di elementi di pari livello di annullamento collegati devono essere annullati o meno. Aggiungere gli stack di annullamento collegati successivi chiamando il metodo [IOleUndoManager:: Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) .  
  
3. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> per eseguire il rollback di tutte le unità di annullamento collegate come una.  
  
    > [!NOTE]
    > Per implementare la gestione degli annullamenti collegati in un editor, aggiungere gestione annullamento. Per ulteriori informazioni sull'implementazione della gestione degli annullamenti collegati, vedere [procedura: implementare la gestione degli annullamenti](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [Procedura: Implementare la gestione della fase di rollback](../extensibility/how-to-implement-undo-management.md)
