---
title: IDebugExpression2::Abort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 490c131820cbe16b8e18be649ad5439c024ad3c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874245"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Questo metodo Annulla valutazione dell'espressione asincrona avviata da una chiamata ai [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) (metodo).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Abort(
   void
);
```

```csharp
int Abort();
```

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Quando la valutazione dell'espressione asincrona viene annullata, non inviati un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) evento al callback dell'evento passato per il [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) o [Connetti](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodi.

## <a name="see-also"></a>Vedere anche
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)