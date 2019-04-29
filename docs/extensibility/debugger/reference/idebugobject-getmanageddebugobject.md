---
title: IDebugObject::GetManagedDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6738c70b75ff1e2f393b59e330ce57f2232de61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918528"
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

#### <a name="parameters"></a>Parametri
 `ppObject`

 [out] Restituisce un [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) oggetto che rappresenta l'oggetto gestito appena creato.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore. Restituisce E_FAIL se l'oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) non rappresenta un'istanza della classe valore gestito.

## <a name="remarks"></a>Note
 Ciò [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto deve rappresentare un'istanza della classe valore gestito, ad esempio un `System.Decimal` istanza. Facendo in modo che una copia locale, l'overhead della chiamata al metodo [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) viene eliminato.

## <a name="see-also"></a>Vedere anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)