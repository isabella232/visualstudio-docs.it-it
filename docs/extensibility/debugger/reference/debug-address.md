---
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d45fa0be28fcad891366581e13425d3940a0a967
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684611"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
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

## <a name="terms"></a>Termini
ulAppDomainID l'ID del processo.

guidModule GUID del modulo che contiene questo indirizzo.

tokClass il token che identifica la classe o un tipo di questo indirizzo.

> [!NOTE]
> Questo valore è specifico di un provider di simboli e pertanto non ha alcun significato generale diverso da come identificatore per un tipo di classe.

Oggetto addr [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struttura, che contiene un'unione di strutture che descrivono i tipi di singoli indirizzi. Il valore `addr`.`dwKind` proviene il [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumerazione, che viene illustrato come interpretare l'unione.

## <a name="remarks"></a>Note
Questa struttura viene passata per il [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) metodo deve essere compilato.

**Avviso [solo C++]**

Se `addr.dwKind` viene `ADDRESS_KIND_METADATA_LOCAL` e, se `addr.addr.addrLocal.pLocal` non è un valore null, sarà necessario chiamare `Release` sul puntatore token:

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

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
