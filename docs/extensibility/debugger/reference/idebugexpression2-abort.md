---
title: Proprietà IDebugExpression2::Abort . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de2e34a8ae1e038c2109627099dacc5bd03a1ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729767"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Questo metodo annulla la valutazione dell'espressione asincrona come avviato da una chiamata al [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metodo.

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
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Quando la valutazione asincrona dell'espressione viene annullata, non inviare un evento [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) al callback dell'evento passato [ai](../../../extensibility/debugger/reference/idebugprogram2-attach.md) metodi Attach o [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="see-also"></a>Vedere anche
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
