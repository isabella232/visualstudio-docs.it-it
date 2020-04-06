---
title: Proprietà IDebugExceptionEvent2::CanPassToDebuggee . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab57f599214cfbd7a1f5fcca15fa104b072d1d48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729877"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Determina se il motore di debug (DE) supporta l'opzione di passare questa eccezione al programma sottoposto a debug alla ripresa dell'esecuzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Valore restituito
 Restituisce `S_OK` (l'eccezione può essere `S_FALSE` passata al programma) o (l'eccezione non può essere passata).

## <a name="remarks"></a>Osservazioni
 Il DE deve avere un'azione predefinita per il passaggio all'oggetto del debug. L'IDE può ricevere il [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) evento e `CanPassToDebuggee` chiamare il [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metodo senza chiamare il metodo. Pertanto, il DE deve avere un caso predefinito per il passaggio dell'eccezione o meno.

## <a name="see-also"></a>Vedere anche
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Continuare](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
