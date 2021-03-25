---
description: Ottiene la proprietà derivata dalla maggior parte di una proprietà.
title: 'IDebugProperty2:: GetDerivedMostProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6187b71338e6a91a412e704857a6c92888490f52
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065060"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Ottiene la proprietà derivata dalla maggior parte di una proprietà.

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
out Restituisce un oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta la proprietà Derived-most.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice errore. Restituisce `S_GETDERIVEDMOST_NO_DERIVED_MOST` se non esiste alcuna proprietà derivata-most da recuperare.

## <a name="remarks"></a>Commenti
 Se, ad esempio, questa proprietà descrive un oggetto che implementa `ClassRoot` , ma che in realtà è una creazione di un'istanza di `ClassDerived` derivata da `ClassRoot` , questo metodo restituisce un oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che descrive l' `ClassDerived` oggetto.

## <a name="see-also"></a>Vedi anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
