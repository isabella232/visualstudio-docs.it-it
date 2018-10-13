---
title: 'Procedura: usare la gestione di annullamento collegato | Microsoft Docs'
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
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ce5cb31e2ac3d7014dec30e71a1dc08b122a330
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229125"
---
# <a name="how-to-use-linked-undo-management"></a>Procedura: usare la gestione di annullamento collegato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fase di rollback collegata consente all'utente di annullare contemporaneamente le stesse modifiche in più file. Ad esempio, le modifiche simultanee testo su più file di programma, ad esempio un file di intestazione e un file di Visual C++, è una transazione di annullamento collegata. Funzionalità di annullamento collegata è incorporata nell'implementazione dell'ambiente di gestione degli annullamenti, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> consente di modificare questa funzionalità. Fase di rollback collegata è implementata da un'unità di annullamento padre che è possibile collegare gli stack di annullamento separato insieme deve essere considerata come una sola unità di annullamento. La procedura per l'uso di annullamento collegata è descritta in dettaglio nella sezione seguente.  
  
### <a name="to-use-linked-undo"></a>Per usare l'operazione di annullamento collegato  
  
1.  Chiamare `QueryService` sul `SVsLinkedUndoManager` per ottenere un puntatore a `IVsLinkedUndoTransactionManager`.  
  
2.  Creare l'unità di annullamento collegato padre iniziale chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Consente di impostare il punto di partenza per un set di campioni di stack di annullamento per volta essere raggruppati in stack di annullamento collegata. Nel `OpenLinkedUndo` metodo è necessario anche per specificare se si desidera che l'operazione di annullamento collegato non strict o strict. Comportamento di annullamento collegata non strict significa che alcuni dei documenti con elementi di pari livello di annullamento collegato può chiudere e lasciare l'altra collegato annullare nei rispettivi stack di elementi di pari livello. Il comportamento di annullamento collegato Strict specifica che tutti gli stack di pari livello di annullamento collegato devono essere annullata insieme o non ereditarli affatto. Aggiungere successivo collegati gli stack di annullamento chiamando [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) (metodo).  
  
3.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> per implementare tutte le unità di annullamento collegato come uno.  
  
    > [!NOTE]
    >  Per implementare la gestione di annullamento collegato in un editor, aggiungere la gestione di annullamento. Per altre informazioni sull'implementazione della gestione dell'annullamento collegato, vedere [procedura: implementare annullare gestione](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [Interfaccia IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Procedura: Implementare la gestione della fase di rollback](../extensibility/how-to-implement-undo-management.md)

