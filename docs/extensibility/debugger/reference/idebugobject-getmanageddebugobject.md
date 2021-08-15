---
description: Crea una copia dell'oggetto gestito nello spazio degli indirizzi del motore di debug.
title: Oggetto IDebugObject::GetManagedDebugObject | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3aa4089a22988bc6a64ca8928dfd7a2b24e300438337ee8646634a4d34b2ae4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307258"
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
[out] Restituisce un [oggetto IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) che rappresenta l'oggetto gestito appena creato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore. Restituisce E_FAIL se questo [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) non rappresenta un'istanza della classe di valori gestita.

## <a name="remarks"></a>Commenti
 Questo [oggetto IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) deve rappresentare un'istanza della classe di valori gestita, ad esempio un'istanza `System.Decimal` di . Con una copia locale, il sovraccarico della chiamata [a Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) viene eliminato.

## <a name="see-also"></a>Vedi anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
