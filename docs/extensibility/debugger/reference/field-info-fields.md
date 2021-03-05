---
description: Specifica le informazioni da recuperare su un oggetto IDebugField.
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 024c12d5112398e055141a8db4995f2801ca5401
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170289"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Specifica le informazioni da recuperare su un oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Sintassi

```cpp
enum enum_FIELD_INFO_FIELDS { 
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
Inizializza/usa il `bstrFullName` campo nella struttura [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) .

`FIF_NAME`\
Inizializza/usa il `bstrName` campo nella `FIELD_INFO` struttura.

`FIF_TYPE`\
Inizializza/usa il `bstrType` campo nella `FIELD_INFO` struttura.

`FIF_MODIFIERS`\
Inizializza/usa il `bstrModifiers` campo nella `FIELD_INFO` struttura.

## <a name="remarks"></a>Commenti
Questi valori vengono passati anche come argomento al metodo [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) per specificare i campi della struttura [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) da inizializzare.

Questi valori vengono inoltre utilizzati nel `dwFields` membro della `FIELD_INFO` struttura per indicare quali campi vengono utilizzati e validi.

Questi flag possono essere combinati con un bit per bit `OR` .

## <a name="requirements"></a>Requisiti
Intestazione: sh. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
