---
description: Questo metodo annulla la valutazione dell'espressione asincrona avviata da una chiamata al metodo EvaluateAsync).
title: IDebugExpression2::Abort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be5637b350e9448b5c02ede5087fed6c2df26bb4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127130"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Questo metodo annulla la valutazione asincrona dell'espressione avviata da una chiamata al [metodo EvaluateAsync.](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)

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

## <a name="remarks"></a>Commenti
 Quando la valutazione asincrona dell'espressione viene annullata, non inviare un evento [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) al callback dell'evento passato ai [metodi Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) [o Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="see-also"></a>Vedi anche
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
