---
title: DEBUGPROP_INFO_FLAGS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa7e4a498188dc91f2a47b3ccf27f367f15ec77b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737402"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Specifica le informazioni da recuperare su un oggetto proprietà di debug.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>Campi
`DEBUGPROP_INFO_FULLNAME`\
Inizializzare/utilizzare `bstrFullName` il campo.

`DEBUGPROP_INFO_NAME`\
Inizializzare/utilizzare `bstrName` il campo.

`DEBUGPROP_INFO_TYPE`\
Inizializzare/utilizzare `bstrType` il campo.

`DEBUGPROP_INFO_VALUE`\
Inizializzare/utilizzare `bstrValue` il campo.

`DEBUGPROP_INFO_ATTRIB`\
Inizializzare/utilizzare `dwAttrib` il campo.

`DEBUGPROP_INFO_PROP`\
Inizializzare/utilizzare `pProperty` il campo che contiene un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaccia.

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Specifica che il campo valore deve contenere il valore espanso automaticamente, se disponibile, per questo tipo di oggetto.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Operazione deprecata.

`DEBUGPROP_INFO_VALUE_RAW`\
Non restituire valori o membri abbelliti, ovvero non formattare i valori.

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Non restituire valori sintetizzati speciali (ad `ToString()` esempio, non chiamare su un oggetto per produrre un valore).

`DEBUGPROP_INFO_NONE`\
Specifica che non sono stati impostati flag.

`DEBUGPROP_INFO_STANDARD`\
Inizializzare/utilizzare `dwAttrib` `bstrName`i `bstrType`campi `bstrValue` , , , e .

`DEBUGPROP_INFO_All`\
Indica una maschera di tutti i flag.

## <a name="remarks"></a>Osservazioni
Questi valori vengono passati ai metodi [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)ed [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) per indicare i campi da inizializzare [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struttura.

Questi valori vengono utilizzati anche per il `dwFields` membro della `DEBUG_PROPERTY_INFO` struttura per indicare quali campi della struttura vengono utilizzati e validi quando viene restituita la struttura.

Questi valori possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
