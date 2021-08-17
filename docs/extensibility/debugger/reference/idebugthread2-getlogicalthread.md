---
description: I motori di debug non implementano questo metodo.
title: Interfaccia IDebugThread2::GetLogicalThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7de78853611e8ef117fc7a4afc68648e6d3d4741796f1162f09b759331d9c9d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389488"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
I motori di debug non implementano questo metodo.

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
[in] Oggetto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) che rappresenta il stack frame.

`ppLogicalThread`\
[out] Restituisce `IDebugLogicalThread2` un'interfaccia che rappresenta il thread logico associato. Un'implementazione del motore di debug deve impostare su un valore Null.

## <a name="return-value"></a>Valore restituito
 Le implementazioni del motore di debug restituiscono sempre `E_NOTIMPL` .

## <a name="see-also"></a>Vedi anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
