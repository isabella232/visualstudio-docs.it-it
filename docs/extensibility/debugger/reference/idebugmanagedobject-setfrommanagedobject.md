---
title: Proprietà IDebugManagedObject::SetFromManagedObject . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4056befa0b5b053d480983901b24feb6b25cf538
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727706"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Imposta il valore dell'istanza dell'oggetto classe di valori dall'istanza della classe di valori fornita come parametro.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

## <a name="parameters"></a>Parametri
`pManagedObject`\
[in] Interfaccia che rappresenta l'oggetto gestito contenente il nuovo valore.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo viene utilizzato per modificare l'oggetto gestito come rappresentato dal [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) oggetto.

## <a name="see-also"></a>Vedere anche
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
