---
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5a60939b779fe7377662a267826722b4c916679
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317380"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
Specifica come interpretare il tipo di un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto.

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

#### <a name="parameters"></a>Parametri
TYPE_KIND_METADATA  
Il [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) unione deve essere interpretato come una [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struttura.

TYPE_KIND_PDB  
Il `TYPE_INFO` unione deve essere interpretata come un [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struttura.

TYPE_KIND_BUILT  
Il `TYPE_INFO` unione deve essere interpretata come un [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) struttura.

## <a name="remarks"></a>Note
I valori di questa enumerazione vengono visualizzati nei `dwKind` campo del [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) strutturare e vengono usate per determinare come interpretare il `type` membro dell'unione. Il `TYPE_INFO` struttura viene restituita da una chiamata per il [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) (metodo).

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
[Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)  
[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
