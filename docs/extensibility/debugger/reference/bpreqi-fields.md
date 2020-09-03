---
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c0e10b6c253c61a9e68e0cf161201f7d2520ae6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737755"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Specifica le informazioni da recuperare su una richiesta del punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
typedef DWORD BPREQI_FIELDS;
```

```csharp
public enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
```

## <a name="fields"></a>Campi
`BPREQI_BPLOCATION`\
Inizializzare/utilizzare il `bpLocation` campo (percorso punto di interruzione) della struttura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

`BPREQI_LANGUAGE`\
Inizializza/usa il `guidLanguage` campo della `BP_REQUEST_INFO` struttura o `BP_REQUEST_INFO2` .

`BPREQI_PROGRAM`\
Inizializza/usa il `pProgram` campo della `BP_REQUEST_INFO` struttura o `BP_REQUEST_INFO2` .

`BPREQI_PROGRAMNAME`\
Inizializza/usa il `bstrProgramName` campo della `BP_REQUEST_INFO` struttura o `BP_REQUEST_INFO2` .

`BPREQI_THREAD`\
Inizializza/usa il `pThread` campo della `BP_REQUEST_INFO` struttura o `BP_REQUEST_INFO2` .

`BPREQI_THREADNAME`\
Inizializza/usa il `bstrThreadName` campo della `BP_REQUEST_INFO` struttura o `BP_REQUEST_INFO2` .

`BPREQI_PASSCOUNT`\
Inizializza/usa il `bpPassCount` campo della `BP_REQUEST_INFO` struttura o `BP_REQUEST_INFO2` .

`BPREQI_CONDITION`\
Inizializzare/utilizzare il `bpCondition` campo (condizione del punto di interruzione) della `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struttura o.

`BPREQI_FLAGS`\
Inizializza/usa il `dwFlags` campo della `BP_REQUEST_INFO` struttura o `BP_REQUEST_INFO2` .

`BPREQI_ALLOLDFIELDS`\
Inizializza/usa tutti i campi per l'oggetto della `BP_REQUEST_INFO` struttura.

`BPREQI_VENDOR`\
Inizializza/usa il `guidVendor` campo della `BP_REQUEST_INFO2` struttura.

`BPREQI_CONSTRAINT`\
Inizializza/usa il `bstrConstraint` campo della `BP_REQUEST_INFO2` struttura.

`BPREQI_TRACEPOINT`\
Inizializza/usa il `bstrTracepoint` campo della `BP_REQUEST_INFO2` struttura.

`BPREQI_ALLFIELDS`\
Specifica tutti i campi della `BP_REQUEST_INFO2` struttura.

## <a name="remarks"></a>Osservazioni
Passato come argomento ai metodi [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) e [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) per specificare i campi delle strutture [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) da inizializzare.

Questi flag vengono usati anche per indicare quali campi delle `BP_REQUEST_INFO` strutture e `BP_REQUEST_INFO2` vengono usati e validi quando viene restituita ogni struttura.

Questi valori possono essere combinati con un bit per bit `OR` .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
