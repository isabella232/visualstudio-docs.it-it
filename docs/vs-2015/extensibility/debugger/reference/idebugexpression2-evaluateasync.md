---
title: 'IDebugExpression2:: EvaluateAsync | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e084152f6215878816739f46dc91fa322cf9c94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158435"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 in Combinazione di flag dell'enumerazione [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che controllano la valutazione dell'espressione.  
  
 `pExprCallback`  
 in Questo parametro è sempre un valore null.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore. Un codice di errore tipico è:  
  
|Errore|Descrizione|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|È attualmente in corso la valutazione di un'altra espressione e la valutazione dell'espressione simultanea non è supportata.|  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo deve restituire immediatamente dopo l'avvio della valutazione dell'espressione. Quando l'espressione viene valutata correttamente, è necessario inviare un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) al callback di evento [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) come fornito tramite [Connetti](../../../extensibility/debugger/reference/idebugprogram2-attach.md) o [Connetti](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un `CExpression` oggetto semplice che implementa l'interfaccia [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) .  
  
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
