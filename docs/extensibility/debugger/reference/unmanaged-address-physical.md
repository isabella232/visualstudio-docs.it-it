---
description: Questa struttura rappresenta un indirizzo fisico.
title: UNMANAGED_ADDRESS_PHYSICAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_PHYSICAL
helpviewer_keywords:
- UNMANAGED_ADDRESS_PHYSICAL structure
ms.assetid: fed09686-caa6-4efc-851e-a0432019e9d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b9c9b3b0759d5a1831525708b5ae4915d063ca801a9e2c998ccaa0d1655b788e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388890"
---
# <a name="unmanaged_address_physical"></a>UNMANAGED_ADDRESS_PHYSICAL
Questa struttura rappresenta un indirizzo fisico.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagUNMANAGED_ADDRESS_PHYSICAL {
   ULONGLONG offset;
} UNMANAGED_ADDRESS_PHYSICAL;
```

```csharp
public struct UNMANAGED_ADDRESS_PHYSICAL {
   public ulong offset;
}
```

## <a name="members"></a>Members
 `offset`\
 Offset a 64 bit in uno spazio indirizzi fisico.

## <a name="remarks"></a>Commenti
 Questa struttura fa parte dell'unione nella struttura DEBUG_ADDRESS_UNION [quando](../../../extensibility/debugger/reference/debug-address-union.md) il campo della struttura è impostato su (un valore dell'enumerazione ADDRESS_KIND `dwKind` di `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_UNMANAGED_PHYSICAL` dati). [](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
