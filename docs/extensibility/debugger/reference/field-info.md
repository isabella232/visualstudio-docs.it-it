---
description: Questa struttura descrive una variabile locale, un parametro o un altro campo.
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27055178f01f41bb6b4642b8c4d70ea6346b9e74
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059420"
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

## <a name="members"></a>Members
`dwFields`\
Combinazione di flag dell'enumerazione [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) che specifica i membri che vengono compilati.

`bstrFullName`\
Nome completo del campo.

`bstrName`\
Nome breve del campo.

`bstrType`\
Tipo del campo.

`dwModifiers`\
Combinazione di flag dell'enumerazione [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) che descrive il campo.

## <a name="remarks"></a>Commenti
Questa struttura viene passata al metodo [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) dove viene compilata.

## <a name="requirements"></a>Requisiti
Intestazione: sh. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
