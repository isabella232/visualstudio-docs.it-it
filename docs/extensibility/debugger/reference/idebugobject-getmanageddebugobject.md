---
description: Crea una copia dell'oggetto gestito nello spazio degli indirizzi del motore di debug.
title: 'IDebugObject:: GetManagedDebugObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 56961930e08e7d53dfe387c00642ae7266c230c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081919"
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
out Restituisce un oggetto [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) che rappresenta l'oggetto gestito appena creato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore. Restituisce E_FAIL se questo [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) non rappresenta un'istanza della classe di valori gestita.

## <a name="remarks"></a>Commenti
 Questo oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) deve rappresentare un'istanza della classe di valori gestita, ad esempio un' `System.Decimal` istanza di. Con una copia locale viene eliminato il sovraccarico della chiamata di [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
