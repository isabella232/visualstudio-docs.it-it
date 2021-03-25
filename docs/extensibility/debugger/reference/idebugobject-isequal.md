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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cff388778ea584f589f92b5dc9dab11c060c953c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054088"
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
