---
title: 'IDebugObject:: EQUAL | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 406e93456f1bd6d92a42f1584d19aeb52dd5ff93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846777"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Confronta un oggetto con l'oggetto corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT IsEqual( 
   IDebugObject* pObject,
   BOOL*         pfIsEqual
);
```

```csharp
int IsEqual(
   IDebugObject pObject,
   out int      pfIsEqual
);
```

## <a name="parameters"></a>Parametri
`pObject`\
in Oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta l'oggetto con cui eseguire il confronto.

`pfIsEqual`\
out Restituisce un valore diverso da zero ( `TRUE` ) se i valori degli oggetti sono uguali; in caso contrario, restituisce zero ( `FALSE` ).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 In genere, questo metodo può confrontare gli indirizzi dei valori rappresentati dal `pObject` parametro e da questo oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ; se gli indirizzi sono uguali, gli oggetti possono essere considerati uguali.

## <a name="see-also"></a>Vedi anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
