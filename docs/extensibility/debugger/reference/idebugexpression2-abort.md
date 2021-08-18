---
description: Questo metodo annulla la valutazione asincrona delle espressioni come avviata da una chiamata al metodo EvaluateAsync.
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
ms.openlocfilehash: 1c2647c262d4a5a2700f2293d5737fab533d680d5c0a74da1a9b542b9b4c4a31
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417288"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Questo metodo annulla la valutazione asincrona delle espressioni come avviata da una chiamata al [metodo EvaluateAsync.](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)

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
 Quando la valutazione asincrona delle espressioni viene annullata, non inviare un evento [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) al callback dell'evento passato ai metodi [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) [o Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="see-also"></a>Vedi anche
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
