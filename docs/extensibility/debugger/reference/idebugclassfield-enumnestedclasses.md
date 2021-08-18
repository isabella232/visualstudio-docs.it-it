---
description: Crea un enumeratore per le classi annidate in questa classe.
title: IDebugClassField::EnumNestedClasses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a1b31e31df47dd2668f175f0dc1960bb272e23fa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119711"
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
[out] Restituisce un [oggetto IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco di classi annidate. Restituisce un valore Null se non sono presenti classi annidate.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti classi annidate. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
Ogni elemento dell'enumerazione è un oggetto [IDebugClassField che](../../../extensibility/debugger/reference/idebugclassfield.md) descrive una classe annidata.

Una classe annidata è una classe definita all'interno di un'altra classe. Esempio:

```
class RootClass {
   class NestedClass { }
};
```

[L'enumerazione IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) conterrà un oggetto che rappresenta la `NestedClass` classe .

## <a name="see-also"></a>Vedi anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
