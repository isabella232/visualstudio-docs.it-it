---
description: Questa struttura rappresenta l'indirizzo di un metodo di una classe.
title: METADATA_ADDRESS_METHOD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b462e63ec64fec9de292ee7f497f8b62333dd7ba
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711882"
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

## <a name="members"></a>Members
 `tokMethod`\
 ID del metodo.

 [C++] `_mdToken` è un `typedef` oggetto per un oggetto a 32 `int` bit.

 `dwOffset`\
 Offset dall'inizio della classe a questo metodo (può rappresentare l'offset nella tabella vtable).

 `dwVersion`\
 Versione del metodo (questo valore è univoco per il provider di simboli).

## <a name="remarks"></a>Commenti
 Questa struttura fa parte dell'unione nella [struttura DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando il campo della struttura è impostato su (un valore `dwKind` dell'enumerazione `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_METHOD` [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) dati).

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
