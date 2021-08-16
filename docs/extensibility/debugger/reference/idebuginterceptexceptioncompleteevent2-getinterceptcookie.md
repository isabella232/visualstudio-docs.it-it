---
description: Chiamato al completamento dell'elaborazione di un'eccezione intercettata.
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88b4dbaa4cd34f6a6c63294153b0a974768830a6e6f3fb58b615fe902d3c5e0e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389696"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Chiamato al completamento dell'elaborazione di un'eccezione intercettata.

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
[out] Valore univoco associato all'eccezione intercettata.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Commenti
 Dopo che [il metodo InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) ha completato la gestione di un'eccezione intercettata, invia l'evento [IDebugInterceptExceptionCompleteEvent2.](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) Il gestore può usare il `GetInterceptCookie` metodo per recuperare il valore univoco associato all'eccezione (lo stesso valore passato al metodo `InterceptCurrentException` ).

## <a name="see-also"></a>Vedi anche
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
