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
ms.openlocfilehash: 5ec0844ce76be009e0111cc5edfc71350f05037d685aaa4d793b7e9446a9b891
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401817"
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
Questa struttura fa parte dell'unione nella struttura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando il campo della struttura è impostato su (un valore dell'enumerazione ADDRESS_KIND `dwKind` `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_ARRAYELEM` struttura). [](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche

- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
