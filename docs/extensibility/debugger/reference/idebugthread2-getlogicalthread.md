---
title: IDebugThread2::GetLogicalThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99e8dbd78ef262479fbc8405b77fa0cf53f8087a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723292"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Motori di debug non implementano questo metodo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetLogicalThread( 
   IDebugStackFrame2*     pStackFrame,
   IDebugLogicalThread2** ppLogicalThread
);
```

```csharp
int GetLogicalThread( 
   IDebugStackFrame2        pStackFrame,
   out IDebugLogicalThread2 ppLogicalThread
);
```

#### <a name="parameters"></a>Parametri
 `pStackFrame`

 [in] Un' [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) oggetto che rappresenta il frame dello stack.

 `ppLogicalThread`

 [out] Restituisce un `IDebugLogicalThread2` interfaccia che rappresenta il thread logico associato. Un'implementazione del motore di debug debba impostare un valore null.

## <a name="return-value"></a>Valore restituito
 Eseguire il debug restituiscono sempre le implementazioni di motore `E_NOTIMPL`.

## <a name="see-also"></a>Vedere anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)