---
description: Questa struttura rappresenta un indirizzo.
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16d79efe98500de3f09c1004859d1b9cafaa87ca
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073097"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
Questa struttura rappresenta un indirizzo.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagDEBUG_ADDRESS {
    ULONG32             ulAppDomainID;
    GUID                guidModule;
    _mdToken            tokClass;
    DEBUG_ADDRESS_UNION addr;
} DEBUG_ADDRESS;
```

```csharp
public struct DEBUG_ADDRESS {
    public uint                ulAppDomainID;
    public Guid                guidModule;
    public int                 tokClass;
    public DEBUG_ADDRESS_UNION addr;
}
```

## <a name="members"></a>Members
`ulAppDomainID`\
ID del processo.

`guidModule`\
GUID del modulo che contiene questo indirizzo.

`tokClass`\
Token che identifica la classe o il tipo di questo indirizzo.

> [!NOTE]
> Questo valore è specifico di un provider di simboli e pertanto non ha un significato generale diverso da come identificatore per un tipo di classe.

`addr`\
Struttura [DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) che contiene un'unione di strutture che descrivono i singoli tipi di indirizzo. Valore `addr` .`dwKind` deriva [dall'enumerazione ADDRESS_KIND,](../../../extensibility/debugger/reference/address-kind.md) che illustra come interpretare l'unione.

## <a name="remarks"></a>Commenti
Questa struttura viene passata [al metodo GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) da completare.

**Avviso [solo C++]**

Se `addr.dwKind` è e se non è un valore `ADDRESS_KIND_METADATA_LOCAL` `addr.addr.addrLocal.pLocal` Null, è necessario chiamare sul `Release` puntatore del token:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
