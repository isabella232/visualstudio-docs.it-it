---
title: BPREQI_FIELDS . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737755"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Specifica le informazioni da recuperare su una richiesta di punto di interruzione.

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
Inizializzare/utilizzare `bpLocation` il campo (posizione punto di interruzione) della struttura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

`BPREQI_LANGUAGE`\
Inizializzare/utilizzare `guidLanguage` il `BP_REQUEST_INFO` campo `BP_REQUEST_INFO2` della struttura o .

`BPREQI_PROGRAM`\
Inizializzare/utilizzare `pProgram` il `BP_REQUEST_INFO` campo `BP_REQUEST_INFO2` della struttura o .

`BPREQI_PROGRAMNAME`\
Inizializzare/utilizzare `bstrProgramName` il `BP_REQUEST_INFO` campo `BP_REQUEST_INFO2` della struttura o .

`BPREQI_THREAD`\
Inizializzare/utilizzare `pThread` il `BP_REQUEST_INFO` campo `BP_REQUEST_INFO2` della struttura o .

`BPREQI_THREADNAME`\
Inizializzare/utilizzare `bstrThreadName` il `BP_REQUEST_INFO` campo `BP_REQUEST_INFO2` della struttura o .

`BPREQI_PASSCOUNT`\
Inizializzare/utilizzare `bpPassCount` il `BP_REQUEST_INFO` campo `BP_REQUEST_INFO2` della struttura o .

`BPREQI_CONDITION`\
Inizializzare/utilizzare `bpCondition` il campo (condizione `BP_REQUEST_INFO` `BP_REQUEST_INFO2` punto di interruzione) della struttura o .

`BPREQI_FLAGS`\
Inizializzare/utilizzare `dwFlags` il `BP_REQUEST_INFO` campo `BP_REQUEST_INFO2` della struttura o .

`BPREQI_ALLOLDFIELDS`\
Inizializzare/utilizzare tutti i `BP_REQUEST_INFO` campi per la struttura.

`BPREQI_VENDOR`\
Inizializzare/utilizzare `guidVendor` il `BP_REQUEST_INFO2` campo della struttura.

`BPREQI_CONSTRAINT`\
Inizializzare/utilizzare `bstrConstraint` il `BP_REQUEST_INFO2` campo della struttura.

`BPREQI_TRACEPOINT`\
Inizializzare/utilizzare `bstrTracepoint` il `BP_REQUEST_INFO2` campo della struttura.

`BPREQI_ALLFIELDS`\
Specifica tutti i `BP_REQUEST_INFO2` campi per la struttura.

## <a name="remarks"></a>Osservazioni
Passato come argomento ai metodi [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) e [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) per specificare quali campi delle strutture [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) devono essere inizializzati.

Questi flag vengono utilizzati anche `BP_REQUEST_INFO` per `BP_REQUEST_INFO2` indicare quali campi delle strutture e vengono utilizzati e validi quando viene restituita ogni struttura.

Questi valori possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
