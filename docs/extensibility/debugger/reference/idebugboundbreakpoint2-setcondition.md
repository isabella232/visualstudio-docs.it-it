---
title: IDebugBoundBreakpoint2::SetCondition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93109204a02b808c69bed242665bb6e373d6fe7d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337438"
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
Imposta o modifica la condizione associata a questo punto di interruzione associato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   enum_BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Parametri
`bpCondition`\
[in] Un valore compreso il [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) enumerazione che descrive la condizione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_BP_DELETED` se lo stato dell'oggetto punto di interruzione associato viene impostato su `BPS_DELETED` (in parte il [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumerazione).

## <a name="remarks"></a>Note
 Tutte le condizioni che è stato precedentemente associata a questo punto di interruzione vengono persa.

## <a name="see-also"></a>Vedere anche
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)