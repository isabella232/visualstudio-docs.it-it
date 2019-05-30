---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 30a70f33edbe3cf817ebe4ad383c54bc02275a72
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316106"
---
# <a name="unmanagedaddressthisrelative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Questa struttura rappresenta un indirizzo a cui fa riferimento a un `this` puntatore (`Me` in Visual Basic).

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagUNMANAGED_THIS_RELATIVE {
   DWORD dwOffset;
   DWORD dwBitOffset;
   DWORD dwBitLength;
} UNMANAGED_ADDRESS_THIS_RELATIVE;
```

```csharp
public struct UNMANAGED_THIS_RELATIVE {
   public uint dwOffset;
   public uint dwBitOffset;
   public uint dwBitLength;
}
```

## <a name="members"></a>Membri
 `dwOffset`\
 Offset da una posizione di base (ad esempio, avvio di un oggetto vtable classe) in byte.

 `dwBitOffset`\
 Offset in bit da una posizione di base (sempre 0 a meno che non fa riferimento a un campo di bit).

 `dwBitLength`\
 Numero di bit che rappresenta l'indirizzo (sempre 0 a meno che non fa riferimento a un campo di bit).

## <a name="remarks"></a>Note
 Questa struttura è parte dell'unione nel [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struttura quando il `dwKind` campo il `DEBUG_ADDRESS_UNION` struttura è impostata su `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` (un valore compreso il [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumerazione).

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)