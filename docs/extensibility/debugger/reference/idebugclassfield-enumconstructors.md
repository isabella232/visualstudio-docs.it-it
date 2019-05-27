---
title: IDebugClassField::EnumConstructors | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb31af11ae4ecc2618e577df6e3b1e2e45a0cbc7
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203219"
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
[in] Un valore compreso il [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) enumerazione che specifica il tipo di costruttori all'enumerazione.

`ppEnum`\
[out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco di costruttori. Restituisce un valore null se non sono presenti costruttori.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK o restituisce S_FALSE se non sono presenti costruttori. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Ogni elemento dell'enumerazione è un [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) oggetto che descrive un metodo del costruttore.

 L'elenco di costruttori non include in genere i costruttori predefiniti forniti da un compilatore.

## <a name="see-also"></a>Vedere anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)