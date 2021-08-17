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
ms.openlocfilehash: de33532e0d81287b44e9e623df683c9a76de1a7c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029560"
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
