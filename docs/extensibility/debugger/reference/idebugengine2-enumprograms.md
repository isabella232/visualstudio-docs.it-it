---
title: IDebugEngine2::EnumPrograms | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::EnumPrograms
helpviewer_keywords:
- IDebugEngine2::EnumPrograms
ms.assetid: 56bf98eb-beec-4e5f-9ebe-46c922e54c56
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c424dca7b20e6abe1afd419e9c156a400583b5cb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678566"
---
# <a name="idebugengine2enumprograms"></a>IDebugEngine2::EnumPrograms
Recupera un elenco di tutti i programmi in fase di debug da un motore di debug (DE).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumPrograms( 
   IEnumDebugPrograms2** ppEnum
);
```

```csharp
int EnumPrograms( 
   out IEnumDebugPrograms2 ppEnum
);
```

#### <a name="parameters"></a>Parametri
 `ppEnum`

 [out] Restituisce un [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md) oggetto che contiene un elenco di tutti i programmi in fase di debug da un CRI.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)