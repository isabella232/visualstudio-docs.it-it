---
description: Questa struttura specifica informazioni su un tipo di campo tratto da un simbolo PDB.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 115d327411cb3d04f26e44ede6fee0f17ff3d9b6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034630"
---
# <a name="pdb_type"></a>PDB_TYPE

Questa struttura specifica informazioni su un tipo di campo tratto da un simbolo PDB.

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
ID dell'applicazione da cui deriva il simbolo. Viene usato per identificare in modo univoco un'istanza dell'applicazione.

`guidModule`\
GUID del modulo che contiene questo campo.

`symid`\
ID del simbolo che corrisponde a questo campo.

## <a name="remarks"></a>Commenti

Questa struttura viene visualizzata come parte dell'unione nella struttura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando il campo della struttura è impostato su (un valore `dwKind` `TYPE_INFO` `TYPE_KIND_PDB` dell'enumerazione dwTYPE_KIND). [](../../../extensibility/debugger/reference/dwtype-kind.md)

## <a name="requirements"></a>Requisiti

Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche

- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
