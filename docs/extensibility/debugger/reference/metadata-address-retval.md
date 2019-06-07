---
title: METADATA_ADDRESS_RETVAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ff96d5ca9d292d9e2952b9a2e5e1f628b54d43b
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746340"
---
# <a name="metadataaddressretval"></a>METADATA_ADDRESS_RETVAL
Questa struttura rappresenta un valore restituito da un metodo o funzione.

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

## <a name="members"></a>Membri
 `tokMethod`\
 L'ID del metodo di questo valore restituito è per.

 `dwCorType`\
 Il tipo di base del valore restituito. Si tratta di un valore compreso il `CorElementType` enumerazione definita nel file corhdr. h di .NET Framework SDK.

 `dwSigSize`\
 Le dimensioni della firma del valore restituito (archiviato in `rgSig`).

 `rgSig`\
 Matrice di byte che costituiscono la firma del valore restituito.

## <a name="remarks"></a>Note
 Questa struttura è parte dell'unione nel [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struttura quando il `dwKind` campo il `DEBUG_ADDRESS_UNION` struttura è impostata su `ADDRESS_KIND_RETVAL` (un valore compreso il [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumerazione).

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)