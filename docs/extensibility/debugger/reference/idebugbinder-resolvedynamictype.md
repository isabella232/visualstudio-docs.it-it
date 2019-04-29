---
title: IDebugBinder::ResolveDynamicType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveDynamicType
helpviewer_keywords:
- IDebugBinder::ResolveDynamicType method
ms.assetid: 2c36ef92-5b44-4cfd-988e-54a2e5a6710c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 116a08025f70c2cd1e4c87f775511bd20ac0e4ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923630"
---
# <a name="idebugbinderresolvedynamictype"></a>IDebugBinder::ResolveDynamicType
Questo metodo restituisce il tipo esatto di una variabile.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT ResolveDynamicType (
   IDebugDynamicField *pDynamic,
   IDebugField       **ppResolved
);
```

```csharp
int ResolveDynamicType(
   IDebugDynamicField pDynamic,
   out IDebugField    ppResolved
);
```

#### <a name="parameters"></a>Parametri
 `pDynamic`

 [in] Un' [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) che rappresenta un tipo di una variabile.

 `ppResolved`

 [out] Restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) fornendo informazioni specifiche sul tipo della variabile.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)