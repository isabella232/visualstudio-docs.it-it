---
title: IDebugStackFrame2::GetExpressionContext | Microsoft Docs
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
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1343118b86325225a499b7caf6d19c31cc84532d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527139"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugStackFrame2::GetExpressionContext](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe2-getexpressioncontext).  
  
Ottiene un contesto di valutazione per la valutazione dell'espressione nel contesto corrente di un frame dello stack e thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
