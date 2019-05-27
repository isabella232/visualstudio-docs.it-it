---
title: IDebugClassField::EnumNestedClasses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf46b0a143b61be6897caa0adb03ab40c375e7bb
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206864"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Crea un enumeratore per le classi annidate di questa classe.

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
[out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco di classi annidate. Restituisce un valore null se non esistono Nessun classi annidate.

## <a name="return-value"></a>Valore restituito
Se l'operazione riesce, restituisce S_OK o restituisce S_FALSE se nessuna classe annidata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
Ogni elemento dell'enumerazione è un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto che descrive una classe annidata.

Una classe annidata è una classe definita all'interno di un'altra classe. Ad esempio:

```
class RootClass {
   class NestedClass { }
};
```

Il [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) enumerazione contiene un oggetto che rappresenta il `NestedClass` classe.

## <a name="see-also"></a>Vedere anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
