---
description: Questa struttura specifica le informazioni su un tipo di campo tratto da un simbolo PDB.
title: PDB_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b9b27024979faaebbacdfdde93e26ffddb6f312
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082231"
---
# <a name="pdb_type"></a>PDB_TYPE

Questa struttura specifica le informazioni su un tipo di campo tratto da un simbolo PDB.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagTYPE_PDB {
    ULONG32 ulAppDomainID;
    GUID    guidModule;
    DWORD   symid;
} PDB_TYPE;
```

```csharp
public struct PDB_TYPE {
    public uint ulAppDomainID;
    public Guid guidModule;
    public uint symid;
};
```

## <a name="members"></a>Members

`ulAppDomainID`\
ID dell'applicazione da cui è arrivato il simbolo. Viene utilizzato per identificare in modo univoco un'istanza dell'applicazione.

`guidModule`\
GUID del modulo che contiene questo campo.

`symid`\
ID del simbolo che corrisponde a questo campo.

## <a name="remarks"></a>Commenti

Questa struttura viene visualizzata come parte dell'Unione nella struttura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando il `dwKind` campo della `TYPE_INFO` struttura è impostato su `TYPE_KIND_PDB` (un valore dell'enumerazione [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

## <a name="requirements"></a>Requisiti

Intestazione: sh. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche

- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
