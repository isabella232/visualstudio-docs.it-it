---
title: proprietà DEBUGREF_INFO_FLAGS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb10ae5d3b4ce9f8aa777f643d412e075bd5293f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737384"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Specifica le informazioni da recuperare su un oggetto di riferimento di debug.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Campi
`DEBUGREF_INFO_NAME`\
Inizializzare/utilizzare `bstrName` il campo nella struttura.

`DEBUGREF_INFO_TYPE`\
Inizializzare/utilizzare `bstrType` il campo nella struttura.

`DEBUGREF_INFO_VALUE`\
Inizializzare/utilizzare `bstrValue` il campo nella struttura.

`DEBUGREF_INFO_ATTRIB`\
Inizializzare/utilizzare `dwAttrib` il campo nella struttura.

`DEBUGREF_INFO_REFTYPE`\
Inizializzare/utilizzare `dwRefType` il campo nella struttura.

`DEBUGREF_INFO_REF`\
Inizializzare/utilizzare `pReference` il campo nella struttura.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Il campo value deve contenere il valore espanso automaticamente, se disponibile, per questo tipo di oggetto.

`DEBUGREF_INFO_NONE`\
Indica che non sono impostati flag.

`DEBUGREF_INFO_ALL`\
Indica una maschera dei flag.

## <a name="remarks"></a>Osservazioni
Questi flag vengono passati ai metodi [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) e [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) per indicare quali campi della struttura [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) devono essere inizializzati.

Utilizzato per `dwFields` il `DEBUG_REFERENCE_INFO` membro della struttura per indicare i campi utilizzati e validi quando viene restituita la struttura.

Questi valori possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
