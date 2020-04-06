---
title: proprietà UNMANAGED_ADDRESS_THIS_RELATIVE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea493170c7b422129485fcea4248981a2b506001
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713262"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Questa struttura rappresenta un indirizzo `this` relativo`Me` a un puntatore ( in Visual Basic).

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
 Offset di byte da una posizione di base (ad esempio, l'inizio di una classe vtable).

 `dwBitOffset`\
 Offset in bit da una posizione di base (sempre 0 a meno che non si faccia riferimento a un campo di bit).

 `dwBitLength`\
 Numero di bit che rappresentano l'indirizzo (sempre 0 a meno che non si faccia riferimento a un campo di bit).

## <a name="remarks"></a>Osservazioni
 Questa struttura fa parte dell'unione nella `dwKind` struttura `DEBUG_ADDRESS_UNION` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` il campo della struttura è impostato su (un valore dell'enumerazione [ADDRESS_KIND).](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
