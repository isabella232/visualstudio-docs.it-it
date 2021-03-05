---
description: Rimuove l'eccezione specificata in modo che non venga più gestita dal motore di debug.
title: 'IDebugEngine2:: RemoveSetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 588037ef9dcf495f8fbbb210acc3154c31558a32
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153949"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Rimuove l'eccezione specificata in modo che non venga più gestita dal motore di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parametri
`pException`\
in Struttura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) che descrive l'eccezione da rimuovere.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'eccezione da rimuovere deve essere stata precedentemente impostata da una chiamata precedente al metodo [seexception](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .

 Per rimuovere tutte le eccezioni set contemporaneamente, chiamare il metodo [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
