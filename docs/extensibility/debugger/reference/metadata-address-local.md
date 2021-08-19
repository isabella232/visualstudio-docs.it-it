---
description: Questa struttura rappresenta l'indirizzo di una variabile locale all'interno di un ambito (in genere una funzione o un metodo).
title: METADATA_ADDRESS_LOCAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71b8b4ef578646a63ec64fbbde506dd71984fe35
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042816"
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

## <a name="members"></a>Members

`tokMethod`\
ID del metodo o della funzione di cui fa parte la variabile locale.

[C++] `_mdToken` è un `typedef` oggetto per un oggetto a 32 `int` bit.

`pLocal`\
Token di cui rappresenta l'indirizzo rappresentato da questa struttura.

`dwIndex`\
Può essere l'indice di questa variabile locale nel metodo o nella funzione o un altro valore (specifico del linguaggio).

## <a name="remarks"></a>Commenti

Questa struttura fa parte dell'unione nella struttura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando il campo della struttura è impostato su (un valore dell'enumerazione ADDRESS_KIND `dwKind` di `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_LOCAL` dati). [](../../../extensibility/debugger/reference/address-kind.md)

> [!WARNING]
> [Solo C++] Se non è Null, è necessario chiamare sul puntatore del token ( è un campo `pLocal` nella `Release` `addr` [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struttura):
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

## <a name="see-also"></a>Vedi anche

- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
