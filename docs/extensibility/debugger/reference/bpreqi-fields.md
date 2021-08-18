---
description: Specifica le informazioni da recuperare su una richiesta di punto di interruzione.
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88288b6d3c57e65f5f59f580468bde3180f877c4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120231"
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
Inizializzare/usare il campo (posizione del punto di `bpLocation` interruzione) della [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struttura .

`BPREQI_LANGUAGE`\
Inizializzare/usare `guidLanguage` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_PROGRAM`\
Inizializzare/usare `pProgram` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_PROGRAMNAME`\
Inizializzare/usare `bstrProgramName` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_THREAD`\
Inizializzare/usare `pThread` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_THREADNAME`\
Inizializzare/usare `bstrThreadName` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_PASSCOUNT`\
Inizializzare/usare `bpPassCount` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_CONDITION`\
Inizializzare/usare il campo (condizione del punto di `bpCondition` interruzione) della `BP_REQUEST_INFO` struttura o `BP_REQUEST_INFO2` .

`BPREQI_FLAGS`\
Inizializzare/usare `dwFlags` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_ALLOLDFIELDS`\
Inizializzare/usare tutti i campi per l'oggetto della `BP_REQUEST_INFO` struttura .

`BPREQI_VENDOR`\
Inizializzare/usare `guidVendor` il campo della struttura `BP_REQUEST_INFO2` .

`BPREQI_CONSTRAINT`\
Inizializzare/usare `bstrConstraint` il campo della struttura `BP_REQUEST_INFO2` .

`BPREQI_TRACEPOINT`\
Inizializzare/usare `bstrTracepoint` il campo della struttura `BP_REQUEST_INFO2` .

`BPREQI_ALLFIELDS`\
Specifica tutti i campi per la `BP_REQUEST_INFO2` struttura .

## <a name="remarks"></a>Commenti
Passato come argomento ai metodi [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) [e BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) per specificare [](../../../extensibility/debugger/reference/bp-request-info.md) quali campi delle strutture BP_REQUEST_INFO e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) devono essere inizializzati.

Questi flag vengono usati anche per indicare quali campi delle strutture e vengono usati e validi `BP_REQUEST_INFO` `BP_REQUEST_INFO2` quando viene restituita ogni struttura.

Questi valori possono essere combinati con un oggetto bit per `OR` bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
