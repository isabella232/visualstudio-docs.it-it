---
title: IDebugEngine2::RemoveSetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45c3cec5ab0511ea80a6b04d9b3ee575afd9d149
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352541"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Rimuove l'eccezione specificata in modo che non viene più gestito dal motore di debug.

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
[in] Un' [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura che descrive l'eccezione deve essere rimosso.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 L'eccezione viene rimosso deve avere stato impostato in precedenza da una precedente chiamata ai [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) (metodo).

 Per rimuovere tutte le eccezioni di set in una sola volta, chiama il [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)