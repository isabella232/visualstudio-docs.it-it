---
title: IDebugManagedObject::GetManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a02fbe5b954fca78e2f75f982a62a1b9bf5f4a0b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210620"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Restituisce un'interfaccia che rappresenta l'oggetto gestito.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetManagedObject( 
   IUnknown** ppManagedObject
);
```

```cpp
int GetManagedObject(
   out object ppManagedObject
);
```

## <a name="parameters"></a>Parametri
`ppManagedObject`\
[out] Restituisce un'interfaccia che rappresenta l'oggetto gestito.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 L'interfaccia restituita da questo metodo è possibile eseguire query per qualsiasi interfaccia implementata dalla classe gestita, che consente di chiamare i relativi metodi.

## <a name="see-also"></a>Vedere anche
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)