---
title: IDebugThread2::GetLogicalThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e8c1543383b3d0df0166b50359caf0f80a8b3ef
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320230"
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

## <a name="parameters"></a>Parametri
`pStackFrame`\
[in] Un' [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) oggetto che rappresenta il frame dello stack.

`ppLogicalThread`\
[out] Restituisce un `IDebugLogicalThread2` interfaccia che rappresenta il thread logico associato. Un'implementazione del motore di debug debba impostare un valore null.

## <a name="return-value"></a>Valore restituito
 Eseguire il debug restituiscono sempre le implementazioni di motore `E_NOTIMPL`.

## <a name="see-also"></a>Vedere anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)