---
title: Proprietà IDebugProperty2::GetDerivedMostProperty . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2086aded4361049d722ec36ba1d470ed8f7ac6e5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721498"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Ottiene la proprietà più derivata di una proprietà.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDerivedMostProperty ( 
   IDebugProperty2** ppDerivedMost
);
```

```csharp
int GetDerivedMostProperty ( 
   out IDebugProperty2 ppDerivedMost
);
```

## <a name="parameters"></a>Parametri
`ppDerivedMost`\
[fuori] Restituisce un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta la proprietà più derivata.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario restituisce il codice di errore. Restituisce `S_GETDERIVEDMOST_NO_DERIVED_MOST` se non è presente alcuna proprietà derivata da recuperare.

## <a name="remarks"></a>Osservazioni
 Ad esempio, se questa proprietà descrive `ClassRoot` un oggetto che implementa `ClassDerived` ma che `ClassRoot`in realtà è un'istanza di che `ClassDerived` deriva da , questo metodo restituisce un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto che descrive l'oggetto.

## <a name="see-also"></a>Vedere anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
