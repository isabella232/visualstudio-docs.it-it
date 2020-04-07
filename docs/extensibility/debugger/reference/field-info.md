---
title: PROPRIETÀ FIELD_INFO . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e2089746adecc583d04176afca18ad19826ea53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736892"
---
# <a name="field_info"></a>FIELD_INFO
Questa struttura descrive una variabile locale, un parametro o un altro campo.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>Membri
`dwFields`\
Combinazione di flag dell'enumerazione [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) che specifica quali membri vengono compilati.

`bstrFullName`\
Nome completo del campo.

`bstrName`\
Nome breve del campo.

`bstrType`\
Tipo del campo.

`dwModifiers`\
Combinazione di flag dell'enumerazione [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) che descrive il campo.

## <a name="remarks"></a>Osservazioni
Questa struttura viene passata al [metodo GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) in cui viene compilata.

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
