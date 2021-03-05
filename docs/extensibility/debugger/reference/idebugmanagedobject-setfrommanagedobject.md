---
description: Imposta il valore dell'istanza dell'oggetto classe valore dall'istanza della classe di valori fornita come parametro.
title: 'IDebugManagedObject:: SetFromManagedObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b4038b4f3560b7cd526261f898c01f384421f42
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165221"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Imposta il valore dell'istanza dell'oggetto classe valore dall'istanza della classe di valori fornita come parametro.

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
in Interfaccia che rappresenta l'oggetto gestito che contiene il nuovo valore.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene usato per modificare l'oggetto gestito come rappresentato dall'oggetto [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
