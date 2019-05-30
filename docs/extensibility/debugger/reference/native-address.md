---
title: NATIVE_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NATIVE_ADDRESS
helpviewer_keywords:
- NATIVE_ADDRESS structure
ms.assetid: 7a0cd085-bfc8-45cc-a3d4-4459070e207a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 02a44369a68c669273207ba2f32902a0d406c61d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339006"
---
# <a name="nativeaddress"></a>NATIVE_ADDRESS

Questa struttura rappresenta un indirizzo nativo.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagNATIVE_ADDRESS {
    DWORD unknown;
} NATIVE_ADDRESS;
```

```csharp
public struct NATIVE_ADDRESS {
    public uint unknown;
}
```

## <a name="members"></a>Membri

`unknown`\
L'indirizzo nativo (il significato di questo dipende dalla fase di esecuzione e del sistema operativo).

## <a name="remarks"></a>Note

Questa struttura è parte dell'unione nel [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struttura quando il `dwKind` campo il `DEBUG_ADDRESS_UNION` struttura è impostata su `ADDRESS_KIND_NATIVE` (un valore compreso il [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumerazione).

## <a name="requirements"></a>Requisiti

Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche

- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
