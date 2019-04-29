---
title: IDebugEngine2::RemoveSetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d4e8e919f69736025eb211dfd46ee72f461839d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920998"
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

#### <a name="parameters"></a>Parametri
 `pException`

 [in] Un' [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura che descrive l'eccezione deve essere rimosso.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 L'eccezione viene rimosso deve avere stato impostato in precedenza da una precedente chiamata ai [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) (metodo).

 Per rimuovere tutte le eccezioni di set in una sola volta, chiama il [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)