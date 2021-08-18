---
description: Specifica come interpretare il tipo di un oggetto IDebugField.
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71579d77883246e4dd945276668eb2ca3ed26205
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127610"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
Specifica come interpretare il tipo di un [oggetto IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

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
[L TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) union deve essere interpretata come una [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struttura .

`TYPE_KIND_PDB`\
`TYPE_INFO`L'unione deve essere interpretata come [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struttura .

`TYPE_KIND_BUILT`\
`TYPE_INFO`L'unione deve essere interpretata come [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) struttura .

## <a name="remarks"></a>Commenti
I valori di questa enumerazione vengono visualizzati nel campo della struttura TYPE_INFO e vengono utilizzati per determinare come `dwKind` interpretare il membro di [](../../../extensibility/debugger/reference/type-info.md) `type` unione. La `TYPE_INFO` struttura viene restituita da una chiamata al [metodo GetTypeInfo.](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
