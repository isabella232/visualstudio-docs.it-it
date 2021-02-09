---
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e02f78e82c87bceb10b71bcb303a78f25a9a623e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899126"
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
GUID del modulo che contiene l'indirizzo.

`tokClass`\
Token che identifica la classe o il tipo dell'indirizzo.

> [!NOTE]
> Questo valore è specifico di un provider di simboli e pertanto non ha un significato generale diverso da un identificatore per un tipo di classe.

`addr`\
Struttura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , che contiene un'Unione di strutture che descrivono i singoli tipi di indirizzi. Valore `addr` .`dwKind` deriva dall'enumerazione [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , che spiega come interpretare l'Unione.

## <a name="remarks"></a>Commenti
Questa struttura viene passata al metodo [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) da compilare.

**Avviso [solo C++]**

Se `addr.dwKind` è `ADDRESS_KIND_METADATA_LOCAL` e se `addr.addr.addrLocal.pLocal` non è un valore null, è necessario chiamare `Release` sul puntatore del token:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Requisiti
Intestazione: sh. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
