---
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 25b95e2934de9d09ef9541162b05920a04f645bd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723045"
---
# <a name="bpreqifields"></a>BPREQI_FIELDS
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

## <a name="members"></a>Membri
BPREQI_BPLOCATION Initialize/usare la `bpLocation` campo (posizione punto di interruzione) del [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struttura.

BPREQI_LANGUAGE Initialize/usare la `guidLanguage` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.

BPREQI_PROGRAM Initialize/usare la `pProgram` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.

BPREQI_PROGRAMNAME Initialize/usare la `bstrProgramName` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.

BPREQI_THREAD Initialize/usare la `pThread` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.

BPREQI_THREADNAME Initialize/usare la `bstrThreadName` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.

BPREQI_PASSCOUNT Initialize/usare la `bpPassCount` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.

BPREQI_CONDITION Initialize/usare la `bpCondition` campo (condizione di punto di interruzione) del `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.

BPREQI_FLAGS Initialize/usare la `dwFlags` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.

Initialize BPREQI_ALLOLDFIELDS/Usa tutti i campi per la del `BP_REQUEST_INFO` struttura.

BPREQI_VENDOR Initialize/usare la `guidVendor` campo `BP_REQUEST_INFO2` struttura.

BPREQI_CONSTRAINT Initialize/usare la `bstrConstraint` campo `BP_REQUEST_INFO2` struttura.

BPREQI_TRACEPOINT Initialize/usare la `bstrTracepoint` campo `BP_REQUEST_INFO2` struttura.

BPREQI_ALLFIELDS specifica tutti i campi per il `BP_REQUEST_INFO2` struttura.

## <a name="remarks"></a>Note
Passato come argomento per il [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) e [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) metodi per specificare quali campi della [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2 ](../../../extensibility/debugger/reference/bp-request-info2.md) strutture devono essere inizializzate.

Questi flag vengono usanti anche per indicare quali campi della `BP_REQUEST_INFO` e `BP_REQUEST_INFO2` strutture sono utilizzate e validi quando viene restituito ogni struttura.

Questi valori possono essere combinati con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
