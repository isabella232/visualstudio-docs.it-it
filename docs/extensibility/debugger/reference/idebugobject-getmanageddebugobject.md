---
title: Proprietà IDebugObject::GetManagedDebugObject . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67d0d7a8642c9dd90067b0e197f420d4cc821faa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726684"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Crea una copia dell'oggetto gestito nello spazio degli indirizzi del motore di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetManagedDebugObject( 
   IDebugManagedObject** ppObject
);
```

```csharp
int GetManagedDebugObject(
   out IDebugManagedObject ppObject
);
```

## <a name="parameters"></a>Parametri
`ppObject`\
[fuori] Restituisce un [oggetto IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) che rappresenta l'oggetto gestito appena creato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore. Restituisce E_FAIL se questo [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) non rappresenta un'istanza della classe di valori gestita.

## <a name="remarks"></a>Osservazioni
 Questo [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto deve rappresentare un'istanza `System.Decimal` della classe di valori gestita, ad esempio un'istanza. Avendo una copia locale, l'overhead della chiamata [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) viene eliminato.

## <a name="see-also"></a>Vedere anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
