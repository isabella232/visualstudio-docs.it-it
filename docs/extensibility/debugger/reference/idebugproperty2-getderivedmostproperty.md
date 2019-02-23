---
title: IDebugProperty2::GetDerivedMostProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1227cb697dc78a8833e304d775fb4b1af85a2a69
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686457"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Ottiene la proprietà più derivato di una proprietà.

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

#### <a name="parameters"></a>Parametri
 `ppDerivedMost`

 [out] Restituisce un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta la proprietà più derivato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore. Restituisce `S_GETDERIVEDMOST_NO_DERIVED_MOST` se è presente nessuna proprietà più derivato da recuperare.

## <a name="remarks"></a>Note
 Ad esempio, se questa proprietà descrive un oggetto che implementa `ClassRoot` ma che è effettivamente un'istanza di `ClassDerived` che è derivato da `ClassRoot`, questo metodo restituisce un' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto che descrive il `ClassDerived` oggetto.

## <a name="see-also"></a>Vedere anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)