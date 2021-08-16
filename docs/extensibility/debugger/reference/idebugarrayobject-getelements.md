---
description: Ottiene un enumeratore di tutti gli elementi della matrice.
title: IDebugArrayObject::GetElements | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 919a6a1ea6486cedec6ede700c9db0038a41d032a606bd5f80f13af8045a1f61
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403104"
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
[out] Restituisce un [oggetto IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) che consente l'enumerazione su tutti gli elementi.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 In alternativa, usare i [metodi GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) [e GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) per scorrere gli elementi.

## <a name="see-also"></a>Vedi anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
