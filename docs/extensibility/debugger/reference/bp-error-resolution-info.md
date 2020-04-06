---
title: BP_ERROR_RESOLUTION_INFO . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48c4bc888db0ad8be6a0d6e98eeea2223a27e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738094"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Viene descritta la risoluzione di un punto di interruzione di errore, inclusi percorso, programma e thread.

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

## <a name="members"></a>Membri
`dwFields`\
Combinazione di valori dell'enumerazione [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) che specifica quali campi di questa struttura vengono compilati.

`bpResLocation`\
Unione [BP_RESOLUTION_LOCATION,](../../../extensibility/debugger/reference/bp-resolution-location.md) che specifica la posizione di risoluzione del punto di interruzione.

`pProgram`\
Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta l'applicazione in cui si è verificato l'errore del punto di interruzione.

`pThread`\
Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread in cui è in esecuzione l'applicazione che ha generato l'errore del punto di interruzione.

`bstrMessage`\
Stringa contenente qualsiasi messaggio di avviso o di errore risultante da questa risoluzione degli errori.

`dwType`\
Valore dell'enumerazione [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) che specifica il tipo di errore del punto di interruzione.

## <a name="remarks"></a>Osservazioni
Questa struttura viene restituita dal [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metodo.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
