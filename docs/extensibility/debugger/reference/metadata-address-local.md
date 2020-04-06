---
title: METADATA_ADDRESS_LOCAL . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3adf9ca5f679c7a526f10b1ee6c91d50dac52d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714482"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL

Questa struttura rappresenta l'indirizzo di una variabile locale all'interno di un ambito (in genere una funzione o un metodo).

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagMETADATA_ADDRESS_LOCAL {
    _mdToken  tokMethod;
    IUnknown* pLocal;
    DWORD     dwIndex;
} METADATA_ADDRESS_LOCAL;
```

```csharp
public struct METADATA_ADDRESS_LOCAL {
    public int    tokMethod;
    public object pLocal;
    public uint   dwIndex;
}
```

## <a name="members"></a>Membri

`tokMethod`\
ID del metodo o della funzione di cui fa parte la variabile locale.

[C]: `_mdToken` è `typedef` un per un `int`oggetto a 32 bit.

`pLocal`\
Token di cui rappresenta l'indirizzo di questa struttura.

`dwIndex`\
Può essere l'indice di questa variabile locale nel metodo o nella funzione o un altro valore (specifico della lingua).

## <a name="remarks"></a>Osservazioni

Questa struttura fa parte dell'unione nella `dwKind` struttura `DEBUG_ADDRESS_UNION` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando `ADDRESS_KIND_LOCAL` il campo della struttura è impostato su (un valore dell'enumerazione [ADDRESS_KIND).](../../../extensibility/debugger/reference/address-kind.md)

> [!WARNING]
> [Solo C) Se `pLocal` non è null, `Release` è necessario chiamare`addr` il puntatore token ( è un campo nella struttura [DEBUG_ADDRESS):](../../../extensibility/debugger/reference/debug-address.md)
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>Requisiti

Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche

- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
