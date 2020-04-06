---
title: METADATA_ADDRESS_METHOD . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc3dd7a34e4f9a3e1b933781aeaf4e18cad7ec17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714451"
---
# <a name="metadata_address_method"></a>METADATA_ADDRESS_METHOD
Questa struttura rappresenta l'indirizzo di un metodo di una classe.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagMETADATA_ADDRESS_METHOD {
   _mdToken tokMethod;
   DWORD    dwOffset;
   DWORD    dwVersion;
} METADATA_ADDRESS_METHOD;
```

```csharp
public struct METADATA_ADDRESS_METHOD {
   public int  tokMethod;
   public uint dwOffset;
   public uint dwVersion;
}
```

## <a name="members"></a>Membri
 `tokMethod`\
 ID del metodo.

 [C]: `_mdToken` è `typedef` un per un `int`oggetto a 32 bit.

 `dwOffset`\
 Offset dall'inizio della classe a questo metodo (può rappresentare l'offset nella vtable).

 `dwVersion`\
 La versione del metodo (questo valore è univoco per il provider di simboli).

## <a name="remarks"></a>Osservazioni
 Questa struttura fa parte dell'unione nella `dwKind` struttura `DEBUG_ADDRESS_UNION` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando `ADDRESS_KIND_METHOD` il campo della struttura è impostato su (un valore dell'enumerazione [ADDRESS_KIND).](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
