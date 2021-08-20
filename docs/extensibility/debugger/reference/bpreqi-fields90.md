---
description: Enumera i valori validi che specificano le informazioni da recuperare su una richiesta di punto di interruzione.
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 859da0750f3522ae8a889612ae13db43816aa4d1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145744"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Enumera i valori validi che specificano le informazioni da recuperare su una richiesta di punto di interruzione. Questa enumerazione estende [l'BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) di dati.

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
Inizializzare o usare il campo (posizione del punto di interruzione) della `bpLocation` [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struttura .

`BPREQI90_LANGUAGE`\
Inizializzare o usare `guidLanguage` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_PROGRAM`\
Inizializzare o usare `pProgram` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_PROGRAMNAME`\
Inizializzare o usare `bstrProgramName` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_THREAD`\
Inizializzare o usare `pThread` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_THREADNAME`\
Inizializzare o usare `bstrThreadName` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_PASSCOUNT`\
Inizializzare o usare `bpPassCount` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_CONDITION`\
Inizializzare o usare il `bpCondition` campo (condizione del punto di interruzione) della `BP_REQUEST_INFO` struttura o `BP_REQUEST_INFO2` .

`BPREQI90_FLAGS`\
Inizializzare o usare `dwFlags` il campo della struttura o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_ALLOLDFIELDS`\
Inizializzare o usare tutti i campi per l'oggetto della `BP_REQUEST_INFO` struttura .

`BPREQI90_VENDOR`\
Inizializzare o usare `guidVendor` il campo della struttura `BP_REQUEST_INFO2` .

`BPREQI90_CONSTRAINT`\
Inizializzare o usare `bstrConstraint` il campo della struttura `BP_REQUEST_INFO2` .

`BPREQI90_TRACEPOINT`\
Inizializzare o usare `bstrTracepoint` il campo della struttura `BP_REQUEST_INFO2` .

`BPREQI90_MACROTRACEPOINT`\
Inizializzare o usare `bstrMacroTracepoint` il campo della struttura `BP_REQUEST_INFO2` . BPREQI_ALLFIELDS non include questo campo.

`BPREQI90_ALLFIELDS`\
Specifica tutti i campi per la `BP_REQUEST_INFO2` struttura .

## <a name="requirements"></a>Requisiti
Intestazione: Msdbg90.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
