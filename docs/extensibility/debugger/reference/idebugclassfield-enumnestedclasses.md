---
title: Proprietà IDebugClassField::EnumNestedClasses . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e6ef918b55d8b311380264d688085b0d2803601
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734441"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Crea un enumeratore per le classi annidate in questa classe.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumNestedClasses(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedClasses(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametri
`ppEnum`\
[fuori] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco di classi annidate. Restituisce un valore null se non sono presenti classi annidate.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti classi annidate. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Osservazioni
Ogni elemento dell'enumerazione è un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto che descrive una classe annidata.

Una classe annidata è una classe definita all'interno di un'altra classe. Ad esempio:

```
class RootClass {
   class NestedClass { }
};
```

Il [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) enumerazione conterrà `NestedClass` un oggetto che rappresenta la classe.

## <a name="see-also"></a>Vedere anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
