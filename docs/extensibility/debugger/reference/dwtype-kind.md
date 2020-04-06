---
title: proprietà dwTYPE_KIND . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d790f12d3fc21bbae7373470746af2ebfe6dc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737186"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
Specifica come interpretare il tipo di un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};

typedef DWORD dwTYPE_KIND;
```

```csharp
public enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};
```

## <a name="fields"></a>Campi
`TYPE_KIND_METADATA`\
L'unione [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) deve essere interpretata come una struttura [METADATA_TYPE.](../../../extensibility/debugger/reference/metadata-type.md)

`TYPE_KIND_PDB`\
L'unione `TYPE_INFO` deve essere interpretata come una struttura [PDB_TYPE.](../../../extensibility/debugger/reference/pdb-type.md)

`TYPE_KIND_BUILT`\
L'unione `TYPE_INFO` deve essere interpretata come una struttura [BUILT_TYPE.](../../../extensibility/debugger/reference/built-type.md)

## <a name="remarks"></a>Osservazioni
I valori di questa `dwKind` enumerazione vengono visualizzati nel campo della `type` struttura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) e vengono utilizzati per determinare come interpretare il membro dell'unione. La `TYPE_INFO` struttura viene restituita da una chiamata al [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) metodo.

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [Informazioni su GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
