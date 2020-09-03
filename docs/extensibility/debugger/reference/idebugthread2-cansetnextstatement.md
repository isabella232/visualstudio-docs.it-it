---
title: 'IDebugThread2:: CanSetNextStatement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4232c25bfe9acd7f17c88c28aa4211a9c62175f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718835"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
Determina se il puntatore all'istruzione corrente può essere impostato sulla stack frame specificata.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanSetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int CanSetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Parametri
`pStackFrame`\
Riservato per un utilizzo futuro; impostare su un valore null. Se si tratta di un valore null, utilizzare la stack frame corrente.

`pCodeContext`\
in Oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che descrive la posizione del codice che sta per essere eseguita e il relativo contesto.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Se questo metodo restituisce `S_OK` , chiamare il metodo [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) per impostare effettivamente l'istruzione successiva.

## <a name="see-also"></a>Vedere anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
