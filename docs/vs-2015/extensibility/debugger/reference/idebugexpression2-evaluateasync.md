---
title: IDebugExpression2::EvaluateAsync | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d40d619c0e26b9b7f099972a8559791b6686044
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532959"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugExpression2::EvaluateAsync](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpression2-evaluateasync).  
  
Questo metodo valuta l'espressione in modo asincrono.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```csharp  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFlags`  
 [in] Una combinazione di flag dal [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumerazione che controllano la valutazione dell'espressione.  
  
 `pExprCallback`  
 [in] Questo parametro è sempre un valore null.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Un codice di errore tipico è:  
  
|Error|Descrizione|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Un'altra espressione in fase di valutazione e la valutazione dell'espressione simultanee non è supportata.|  
  
## <a name="remarks"></a>Note  
 Questo metodo deve restituire immediatamente dopo l'avvio della valutazione dell'espressione. Quando l'espressione viene valutata correttamente, un' [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) devono essere inviati al [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback di evento forniti tramite [Attach ](../../../extensibility/debugger/reference/idebugprogram2-attach.md) oppure [collegare](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un semplice `CExpression` oggetto che implementa le [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfaccia.  
  
```cpp#  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
