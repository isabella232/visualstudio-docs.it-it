---
description: Questa struttura rappresenta l'indirizzo di un campo di una classe o di una struttura.
title: METADATA_ADDRESS_FIELD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_FIELD
helpviewer_keywords:
- METADATA_ADDRESS_FIELD structure
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9757f42022cf5b590385151fc1346ad75ce8cdd3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627365"
---
# <a name="metadata_address_field"></a>METADATA_ADDRESS_FIELD

Questa struttura rappresenta l'indirizzo di un campo di una classe o di una struttura.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagMETADATA_ADDRESS_FIELD {
    _mdToken tokField;
} METADATA_ADDRESS_FIELD
```

```csharp
public struct METADATA_ADDRESS_FIELD {
    public int tokField;
}
```

## <a name="members"></a>Members

`tokField`\
ID del token di campo.

[C++] `_mdToken` è un `typedef` oggetto per un oggetto a 32 `int` bit.

## <a name="remarks"></a>Commenti

Questa struttura fa parte dell'unione nella struttura DEBUG_ADDRESS_UNION [quando](../../../extensibility/debugger/reference/debug-address-union.md) il campo della struttura è impostato su (un valore dell'enumerazione ADDRESS_KIND `dwKind` `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_FIELD` struttura). [](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requisiti

Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche

- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
