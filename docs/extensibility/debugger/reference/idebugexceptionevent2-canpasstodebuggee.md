---
title: 'IDebugExceptionEvent2:: CanPassToDebuggee | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 498b928d7e04fc97ec076cb67722b7947686c3a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933297"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Determina se il motore di debug (DE) supporta l'opzione di passaggio di questa eccezione al programma di cui è in corso il debug al riavvio dell'esecuzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Valore restituito
 Restituisce `S_OK` (l'eccezione può essere passata al programma) o `S_FALSE` (non è possibile passare l'eccezione).

## <a name="remarks"></a>Commenti
 Il DE deve avere un'azione predefinita per passare all'oggetto del debug. L'IDE può ricevere l'evento [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) e chiamare il metodo [continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) senza chiamare il `CanPassToDebuggee` metodo. Pertanto, il valore di DE deve avere un caso predefinito per il passaggio dell'eccezione.

## <a name="see-also"></a>Vedi anche
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
