---
description: Crea un enumeratore per le classi annidate in questa classe.
title: 'IDebugClassField:: EnumNestedClasses | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87538db39df590fd3885f545e5442c7dafecb9a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164266"
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
out Restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco di classi annidate. Restituisce un valore null se non sono presenti classi annidate.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti classi annidate. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
Ogni elemento dell'enumerazione è un oggetto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) che descrive una classe annidata.

Una classe annidata è una classe definita all'interno di un'altra classe. Ad esempio:

```
class RootClass {
   class NestedClass { }
};
```

L'enumerazione [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) conterrà un oggetto che rappresenta la `NestedClass` classe.

## <a name="see-also"></a>Vedi anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
