---
title: proprietà FIELD_INFO_FIELDS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a3d2e796d37606c51918d8e49db920161d63f55
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736901"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Specifica le informazioni da recuperare su un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="fields"></a>Campi
`FIF_FULLNAME`\
Inizializzare/utilizzare `bstrFullName` il campo nella [struttura FIELD_INFO.](../../../extensibility/debugger/reference/field-info.md)

`FIF_NAME`\
Inizializzare/utilizzare `bstrName` il `FIELD_INFO` campo nella struttura.

`FIF_TYPE`\
Inizializzare/utilizzare `bstrType` il `FIELD_INFO` campo nella struttura.

`FIF_MODIFIERS`\
Inizializzare/utilizzare `bstrModifiers` il `FIELD_INFO` campo nella struttura.

## <a name="remarks"></a>Osservazioni
Questi valori vengono inoltre passati come argomento per il [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metodo per specificare quali campi del [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struttura devono essere inizializzati.

Questi valori vengono utilizzati anche nel `dwFields` membro della `FIELD_INFO` struttura per indicare quali campi vengono utilizzati e validi.

Questi flag possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
