---
description: I motori di debug non implementano questo metodo.
title: 'IDebugThread2:: GetLogicalThread | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3fe053a15ca6c89167b4b4cbf9bdffc8d7c334e8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070973"
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
in Oggetto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) che rappresenta l'stack frame.

`ppLogicalThread`\
out Restituisce un' `IDebugLogicalThread2` interfaccia che rappresenta il thread logico associato. Un'implementazione del motore di debug deve impostare questa impostazione su un valore null.

## <a name="return-value"></a>Valore restituito
 Le implementazioni del motore di debug restituiscono sempre `E_NOTIMPL` .

## <a name="see-also"></a>Vedi anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
