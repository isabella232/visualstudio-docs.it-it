---
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9065c0b7868efaeb70c10a3ab921a8764694662e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727783"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Chiamato quando l'elaborazione di un'eccezione intercettata è stata completata.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetInterceptCookie(
   UINT64* pqwCookie
);
```

```csharp
int GetInterceptCookie(
   out ulong pqwCookie
);
```

## <a name="parameters"></a>Parametri
`pqwCookie`\
[fuori] Valore univoco associato all'eccezione intercettata.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario restituisce il codice di errore.

## <a name="remarks"></a>Osservazioni
 Dopo che il [metodo InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) ha completato la gestione di un'eccezione intercettata, invia l'evento [IDebugInterceptExceptionCompleteEvent2.](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) Il gestore `GetInterceptCookie` può utilizzare il metodo per recuperare il valore univoco `InterceptCurrentException` associato all'eccezione (lo stesso valore passato al metodo).

## <a name="see-also"></a>Vedere anche
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
