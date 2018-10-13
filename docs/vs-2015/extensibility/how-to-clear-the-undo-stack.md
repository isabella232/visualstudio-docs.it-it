---
title: 'Procedura: cancellare lo Stack di annullamento | Microsoft Docs'
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
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d445b4ce79dc2f048ee95c1a356863f1ed524dad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210288"
---
# <a name="how-to-clear-the-undo-stack"></a>Procedura: cancellare lo Stack di annullamento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La procedura seguente illustra come cancellare lo stack di annullamento.  
  
### <a name="to-clear-the-undo-stack"></a>Per cancellare lo stack di annullamento  
  
1.  Per cancellare l'utilizzo dello stack di annullamento il [IOleUndoManager::DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799) (metodo). Di seguito è riportato un esempio:  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Implementare la gestione della fase di rollback](../extensibility/how-to-implement-undo-management.md)

