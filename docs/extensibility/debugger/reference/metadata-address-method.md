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
ms.openlocfilehash: 21acc912a391f7fcc46a568df95be23a3e44c7d7e54ab8d5f77af7aecda5d283
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338254"
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
 Questa struttura fa parte dell'unione nella struttura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando il campo della struttura è impostato su (un valore dell'enumerazione ADDRESS_KIND `dwKind` di `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_METHOD` dati). [](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
