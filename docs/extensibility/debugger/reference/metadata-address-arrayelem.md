---
description: Questa struttura rappresenta un elemento di matrice all'interno di una matrice.
title: METADATA_ADDRESS_ARRAYELEM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords:
- METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59125943d34eb30f470c1cfd2abd3ca36807e244
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634788"
---
# <a name="metadata_address_arrayelem"></a>METADATA_ADDRESS_ARRAYELEM

Questa struttura rappresenta un elemento di matrice all'interno di una matrice.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {
    _mdToken tokMethod;
    DWORD    dwIndex;
} METADATA_ADDRESS_ARRAYELEM;
```

```csharp
public struct METADATA_ADDRESS_ARRAYELEM {
    public int  tokMethod;
    public uint dwIndex;
}
```

## <a name="members"></a>Members

`tokMethod`\
ID della matrice di cui fa parte questo elemento.

[C++] `_mdToken` è un `typedef` oggetto per un oggetto a 32 `int` bit.

`dwIndex`\
Indice di questo elemento all'interno della matrice.

## <a name="remarks"></a>Commenti
Questa struttura fa parte dell'unione nella [struttura DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando il campo della struttura è impostato su (un valore `dwKind` dell'enumerazione `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_ARRAYELEM` [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) dati).

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche

- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
