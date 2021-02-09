---
title: BP_ERROR_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 489d1f8738d5f6d9655bf7978f617ca2c2a37c8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853065"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Descrive la risoluzione di un punto di interruzione di errore, tra cui percorso, programma e thread.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>Members
`dwFields`\
Combinazione di valori dell'enumerazione [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) che specifica i campi della struttura da compilare.

`bpResLocation`\
Unione [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) che specifica la posizione di risoluzione del punto di interruzione.

`pProgram`\
Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta l'applicazione in cui si è verificato l'errore del punto di interruzione.

`pThread`\
Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread in cui è in esecuzione l'applicazione che ha generato l'errore del punto di interruzione.

`bstrMessage`\
Stringa contenente un messaggio di avviso o di errore risultante da questa risoluzione degli errori.

`dwType`\
Valore dell'enumerazione [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) che specifica il tipo di errore del punto di interruzione.

## <a name="remarks"></a>Commenti
Questa struttura viene restituita dal metodo [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
