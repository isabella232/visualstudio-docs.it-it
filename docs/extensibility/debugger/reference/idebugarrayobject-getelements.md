---
description: Ottiene un enumeratore di tutti gli elementi della matrice.
title: 'IDebugArrayObject:: GetElements | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42ecdcedef00ee9d9ca56a365689ff819375fb82
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094354"
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

## <a name="parameters"></a>Parametri
`ppEnum`\
out Restituisce un oggetto [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) che consente l'enumerazione su tutti gli elementi.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 In alternativa, usare i metodi [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) e [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) per scorrere gli elementi.

## <a name="see-also"></a>Vedi anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
