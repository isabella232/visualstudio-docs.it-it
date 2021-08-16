---
description: Questa struttura rappresenta un valore restituito da un metodo o una funzione.
title: METADATA_ADDRESS_RETVAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a323d934cceff20b5e89215dfb9a6d49020a707e07f5d3ca5f37a5fe189627c2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377288"
---
# <a name="metadata_address_retval"></a>METADATA_ADDRESS_RETVAL
Questa struttura rappresenta un valore restituito da un metodo o una funzione.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagMETADATA_ADDRESS_RETVAL {
   _mdToken tokMethod;
   DWORD    dwCorType;
   DWORD    dwSigSize;
   BYTE     rgSig[10];
} METADATA_ADDRESS_RETVAL;
```

```csharp
public struct METADATA_ADDRESS_RETVAL {
   public int    tokMethod;
   public uint   dwCorType;
   public uint   dwSigSize;
   public byte[] rgSig;
}
```

## <a name="members"></a>Members
 `tokMethod`\
 ID del metodo a cui è relativo questo valore restituito.

 `dwCorType`\
 Tipo di base del valore restituito. Si tratta di un valore `CorElementType` dell'enumerazione definita nel file .NET Framework SDK corhdr.h.

 `dwSigSize`\
 Dimensione della firma del valore restituito (come archiviato in `rgSig` ).

 `rgSig`\
 Matrice di byte che forma la firma del valore restituito.

## <a name="remarks"></a>Commenti
 Questa struttura fa parte dell'unione nella [struttura DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando il campo della struttura è impostato su (un valore `dwKind` dell'enumerazione `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_RETVAL` [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) tabella).

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
