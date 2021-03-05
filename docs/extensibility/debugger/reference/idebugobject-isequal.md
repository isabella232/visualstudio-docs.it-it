---
description: Confronta un oggetto con l'oggetto corrente.
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
ms.openlocfilehash: 0907b72f2a0647fc6ff6181ecdc5c7fd8c2134cb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151662"
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
