---
description: Specifica le informazioni da recuperare su un oggetto proprietà di debug.
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89e440c199347bfb28709d97f4a93c0ccb537ab2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145562"
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
Inizializzare/usare il `bstrFullName` campo .

`DEBUGPROP_INFO_NAME`\
Inizializzare/usare il `bstrName` campo .

`DEBUGPROP_INFO_TYPE`\
Inizializzare/usare il `bstrType` campo .

`DEBUGPROP_INFO_VALUE`\
Inizializzare/usare il `bstrValue` campo .

`DEBUGPROP_INFO_ATTRIB`\
Inizializzare/usare il `dwAttrib` campo .

`DEBUGPROP_INFO_PROP`\
Inizializzare/usare il `pProperty` campo che contiene [un'interfaccia IDebugProperty2.](../../../extensibility/debugger/reference/idebugproperty2.md)

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Specifica che il campo del valore deve contenere il valore espanso automaticamente, se disponibile, per questo tipo di oggetto.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Deprecato.

`DEBUGPROP_INFO_VALUE_RAW`\
Non restituire valori o membri abbelliti, ovvero non formattare i valori.

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Non restituire valori sintetizzati speciali( ad esempio, non chiamare su `ToString()` un oggetto per produrre un valore).

`DEBUGPROP_INFO_NONE`\
Specifica che non sono stati impostati flag.

`DEBUGPROP_INFO_STANDARD`\
Inizializzare/usare `dwAttrib` i campi , , e `bstrName` `bstrType` `bstrValue` .

`DEBUGPROP_INFO_All`\
Indica una maschera di tutti i flag.

## <a name="remarks"></a>Commenti
Questi valori vengono passati ai [metodi GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)ed [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) per indicare quali campi devono essere inizializzati DEBUG_PROPERTY_INFO [struttura.](../../../extensibility/debugger/reference/debug-property-info.md)

Questi valori vengono usati anche per il membro della struttura per indicare quali campi della struttura vengono usati e validi `dwFields` quando la struttura viene `DEBUG_PROPERTY_INFO` restituita.

Questi valori possono essere combinati con un oggetto bit per `OR` bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
