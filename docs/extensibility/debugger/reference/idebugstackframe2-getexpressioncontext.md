---
title: IDebugStackFrame2::GetExpressionContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7a4c89861f22d1dd7df1f5a19ed7f5f3b192daf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020139"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
Ottiene un contesto di valutazione per la valutazione dell'espressione nel contesto corrente di un frame dello stack e thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```csharp  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppExprCxt`  
 [out] Restituisce un [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) oggetto che rappresenta un contesto per la valutazione dell'espressione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In genere, un contesto di valutazione di espressioni può essere considerato come un ambito per l'esecuzione di valutazione dell'espressione. Chiamare il [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metodo per analizzare un'espressione e quindi chiamare risultante [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oppure [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metodi per valutare l'espressione analizzata.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)