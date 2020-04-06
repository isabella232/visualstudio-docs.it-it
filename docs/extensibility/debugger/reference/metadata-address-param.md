---
title: proprietà METADATA_ADDRESS_PARAM . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_PARAM
helpviewer_keywords:
- METADATA_ADDRESS_PARAM structure
ms.assetid: 90904f19-0e71-4cb3-a56e-6a2e92f66dfc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a0319cfc6f2be817a25126e67cdc470bc727a4ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714447"
---
# <a name="metadata_address_param"></a>METADATA_ADDRESS_PARAM
Questa struttura rappresenta un parametro di un metodo o di una funzione.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagMETADATA_ADDRESS_PARAM {
   _mdToken tokMethod;
   _mdToken tokParam;
   DWORD    dwIndex;
} METADATA_ADDRESS_PARAM;
```

```csharp
public struct METADATA_ADDRESS_PARAM {
   public int  tokMethod;
   public int  tokParam;
   public uint dwIndex;
}
```

## <a name="members"></a>Membri
 `tokMethod`\
 ID del metodo di cui fa parte il parametro.

 `tokParam`\
 ID del parametro.

 `dwIndex`\
 Indice del parametro in un elenco di parametri.

## <a name="remarks"></a>Osservazioni
 Questa struttura fa parte dell'unione nella `dwKind` struttura `DEBUG_ADDRESS_UNION` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando `ADDRESS_KIND_PARAM` il campo della struttura è impostato su (un valore dell'enumerazione [ADDRESS_KIND).](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
