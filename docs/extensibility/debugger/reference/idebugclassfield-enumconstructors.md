---
description: Crea un enumeratore per i costruttori per questa classe.
title: 'IDebugClassField:: EnumConstructors | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8efba9ecb25259b6aa4998a1f22fedf443c1281a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084974"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Crea un enumeratore per i costruttori per questa classe.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametri
`cMatch`\
in Valore dell'enumerazione [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) che specifica il tipo di costruttori da enumerare.

`ppEnum`\
out Restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco dei costruttori. Restituisce un valore null se non sono presenti costruttori.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti costruttori. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Ogni elemento dell'enumerazione è un oggetto [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) che descrive un metodo del costruttore.

 L'elenco dei costruttori non include in genere i costruttori predefiniti forniti da un compilatore.

## <a name="see-also"></a>Vedi anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
