---
title: PDB_TYPE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f736d7d9b190fc46945e2f4f7c309b88c3e851f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714098"
---
# <a name="pdb_type"></a>PDB_TYPE

Questa struttura specifica le informazioni su un tipo di campo ricavato da un simbolo PDB.

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

## <a name="members"></a>Membri

`ulAppDomainID`\
ID dell'applicazione da cui proveniva il simbolo. Viene utilizzato per identificare in modo univoco un'istanza dell'applicazione.

`guidModule`\
GUID del modulo che contiene questo campo.

`symid`\
ID del simbolo che corrisponde a questo campo.

## <a name="remarks"></a>Osservazioni

Questa struttura viene visualizzata come parte dell'unione `TYPE_INFO` nella struttura `TYPE_KIND_PDB` [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando il `dwKind` campo della struttura è impostato su (un valore dell'enumerazione [dwTYPE_KIND).](../../../extensibility/debugger/reference/dwtype-kind.md)

## <a name="requirements"></a>Requisiti

Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche

- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
