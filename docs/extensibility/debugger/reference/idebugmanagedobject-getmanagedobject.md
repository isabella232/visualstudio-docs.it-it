---
title: Proprietà IDebugManagedObject::GetManagedObject . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b7080760b174c51d62c44cd2757944948e0104ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727745"
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
[fuori] Restituisce un'interfaccia che rappresenta l'oggetto gestito.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 L'interfaccia restituita da questo metodo può essere eseguita una query per qualsiasi interfaccia implementata dalla classe gestita, consentendo la chiamata dei relativi metodi.

## <a name="see-also"></a>Vedere anche
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
