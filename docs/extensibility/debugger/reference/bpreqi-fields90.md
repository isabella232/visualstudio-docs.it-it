---
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea46939118ec48490280d6a85cc84e144d320d4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737742"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Enumera i valori validi che specificano le informazioni da recuperare su una richiesta del punto di interruzione. Questa enumerazione estende l'enumerazione [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) .

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
typedef DWORD BPREQI_FIELDS90;
```

```csharp
public enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
```

## <a name="fields"></a>Campi
`BPREQI90_BPLOCATION`\
Inizializzare o utilizzare il `bpLocation` campo (percorso punto di interruzione) della struttura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

`BPREQI90_LANGUAGE`\
Inizializzare o utilizzare il `guidLanguage` campo della `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struttura o.

`BPREQI90_PROGRAM`\
Inizializzare o utilizzare il `pProgram` campo della `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struttura o.

`BPREQI90_PROGRAMNAME`\
Inizializzare o utilizzare il `bstrProgramName` campo della `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struttura o.

`BPREQI90_THREAD`\
Inizializzare o utilizzare il `pThread` campo della `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struttura o.

`BPREQI90_THREADNAME`\
Inizializzare o utilizzare il `bstrThreadName` campo della `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struttura o.

`BPREQI90_PASSCOUNT`\
Inizializzare o utilizzare il `bpPassCount` campo della `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struttura o.

`BPREQI90_CONDITION`\
Inizializzare o utilizzare il `bpCondition` campo (condizione del punto di interruzione) della `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struttura o.

`BPREQI90_FLAGS`\
Inizializzare o utilizzare il `dwFlags` campo della `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struttura o.

`BPREQI90_ALLOLDFIELDS`\
Inizializzare o utilizzare tutti i campi per l'oggetto della `BP_REQUEST_INFO` struttura.

`BPREQI90_VENDOR`\
Inizializzare o utilizzare il `guidVendor` campo della `BP_REQUEST_INFO2` struttura.

`BPREQI90_CONSTRAINT`\
Inizializzare o utilizzare il `bstrConstraint` campo della `BP_REQUEST_INFO2` struttura.

`BPREQI90_TRACEPOINT`\
Inizializzare o utilizzare il `bstrTracepoint` campo della `BP_REQUEST_INFO2` struttura.

`BPREQI90_MACROTRACEPOINT`\
Inizializzare o utilizzare il `bstrMacroTracepoint` campo della `BP_REQUEST_INFO2` struttura. BPREQI_ALLFIELDS non include questo campo.

`BPREQI90_ALLFIELDS`\
Specifica tutti i campi della `BP_REQUEST_INFO2` struttura.

## <a name="requirements"></a>Requisiti
Intestazione: Msdbg90. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
