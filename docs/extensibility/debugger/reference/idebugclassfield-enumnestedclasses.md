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
ms.openlocfilehash: 512329317ce1e9587848edf15c68f57fe112299e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876842"
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

#### <a name="parameters"></a>Parametri
`ppEnum`

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
