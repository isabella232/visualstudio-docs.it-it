---
title: BPREQI_FIELDS90 . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737742"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Enumera i valori validi che specificano le informazioni da recuperare su una richiesta di punto di interruzione. Questa enumerazione estende l'enumerazione [BPREQI_FIELDS.](../../../extensibility/debugger/reference/bpreqi-fields.md)

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
Inizializzare o `bpLocation` utilizzare il campo (posizione punto di interruzione) della struttura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

`BPREQI90_LANGUAGE`\
Inizializzare o `guidLanguage` utilizzare `BP_REQUEST_INFO` il `BP_REQUEST_INFO2` campo della struttura o .

`BPREQI90_PROGRAM`\
Inizializzare o `pProgram` utilizzare `BP_REQUEST_INFO` il `BP_REQUEST_INFO2` campo della struttura o .

`BPREQI90_PROGRAMNAME`\
Inizializzare o `bstrProgramName` utilizzare `BP_REQUEST_INFO` il `BP_REQUEST_INFO2` campo della struttura o .

`BPREQI90_THREAD`\
Inizializzare o `pThread` utilizzare `BP_REQUEST_INFO` il `BP_REQUEST_INFO2` campo della struttura o .

`BPREQI90_THREADNAME`\
Inizializzare o `bstrThreadName` utilizzare `BP_REQUEST_INFO` il `BP_REQUEST_INFO2` campo della struttura o .

`BPREQI90_PASSCOUNT`\
Inizializzare o `bpPassCount` utilizzare `BP_REQUEST_INFO` il `BP_REQUEST_INFO2` campo della struttura o .

`BPREQI90_CONDITION`\
Inizializzare o `bpCondition` utilizzare il campo `BP_REQUEST_INFO` (condizione punto di interruzione) della struttura o `BP_REQUEST_INFO2` .

`BPREQI90_FLAGS`\
Inizializzare o `dwFlags` utilizzare `BP_REQUEST_INFO` il `BP_REQUEST_INFO2` campo della struttura o .

`BPREQI90_ALLOLDFIELDS`\
Inizializzare o utilizzare tutti `BP_REQUEST_INFO` i campi per la struttura.

`BPREQI90_VENDOR`\
Inizializzare o `guidVendor` utilizzare `BP_REQUEST_INFO2` il campo della struttura.

`BPREQI90_CONSTRAINT`\
Inizializzare o `bstrConstraint` utilizzare `BP_REQUEST_INFO2` il campo della struttura.

`BPREQI90_TRACEPOINT`\
Inizializzare o `bstrTracepoint` utilizzare `BP_REQUEST_INFO2` il campo della struttura.

`BPREQI90_MACROTRACEPOINT`\
Inizializzare o `bstrMacroTracepoint` utilizzare `BP_REQUEST_INFO2` il campo della struttura. BPREQI_ALLFIELDS non include questo campo.

`BPREQI90_ALLFIELDS`\
Specifica tutti i `BP_REQUEST_INFO2` campi per la struttura.

## <a name="requirements"></a>Requisiti
Intestazione: Msdbg90.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
