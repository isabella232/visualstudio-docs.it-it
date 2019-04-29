---
title: IDebugArrayObject::GetElements | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cad81d76e2fcec01fa50a37fa6ab6cb49cfc79be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423699"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Ottiene un enumeratore di tutti gli elementi della matrice.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

#### <a name="parameters"></a>Parametri
 `ppEnum`

 [out] Restituisce un [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) oggetto che consente l'enumerazione su tutti gli elementi.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 In alternativa, usare il [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) e [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) metodi per scorrere gli elementi.

## <a name="see-also"></a>Vedere anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)