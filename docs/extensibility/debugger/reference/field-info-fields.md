---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a3d2e796d37606c51918d8e49db920161d63f55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736901"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Specifica le informazioni da recuperare su un oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

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
Inizializza/usa il `bstrFullName` campo nella struttura [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) .

`FIF_NAME`\
Inizializza/usa il `bstrName` campo nella `FIELD_INFO` struttura.

`FIF_TYPE`\
Inizializza/usa il `bstrType` campo nella `FIELD_INFO` struttura.

`FIF_MODIFIERS`\
Inizializza/usa il `bstrModifiers` campo nella `FIELD_INFO` struttura.

## <a name="remarks"></a>Osservazioni
Questi valori vengono passati anche come argomento al metodo [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) per specificare i campi della struttura [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) da inizializzare.

Questi valori vengono inoltre utilizzati nel `dwFields` membro della `FIELD_INFO` struttura per indicare quali campi vengono utilizzati e validi.

Questi flag possono essere combinati con un bit per bit `OR` .

## <a name="requirements"></a>Requisiti
Intestazione: sh. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
