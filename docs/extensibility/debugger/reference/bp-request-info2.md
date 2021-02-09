---
title: BP_REQUEST_INFO2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ad3c5492143f97559770c57d528971ac84f22fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903274"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Contiene le informazioni necessarie per implementare un punto di interruzione, tra cui GUID del fornitore, vincolo e punto di analisi.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _BP_REQUEST_INFO2 {
    BPREQI_FIELDS   dwFields;
    GUID            guidLanguage;
    BP_LOCATION     bpLocation;
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    IDebugThread2*  pThread;
    BSTR            bstrThreadName;
    BP_CONDITION    bpCondition;
    BP_PASSCOUNT    bpPassCount;
    BP_FLAGS        dwFlags;
    GUID            guidVendor;
    BSTR            bstrConstraint;
    BSTR            bstrTracepoint;
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
    public uint           dwFields;
    public Guid           guidLanguage;
    public BP_LOCATION    bpLocation;
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public IDebugThread2  pThread;
    public string         bstrThreadName;
    public BP_CONDITION   bpCondition;
    public BP_PASSCOUNT   bpPassCount;
    public uint           dwFlags;
    public Guid           guidVendor;
    public string         bstrConstraint;
    public string         bstrTracepoint;
};
```

## <a name="members"></a>Members
`dwFields`\
Combinazione di flag dell'enumerazione [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) che specifica i campi che vengono compilati.

`guidLanguage`\
GUID del linguaggio.

`bpLocation`\
Struttura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) che specifica il tipo di posizione del punto di interruzione.

`pProgram`\
Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta l'applicazione in cui si verifica il punto di interruzione.

`bstrProgramName`\
Nome dell'applicazione in cui si verifica il punto di interruzione.

`pThread`\
Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread in cui si verifica il punto di interruzione.

`bstrThreadName`\
Nome del thread in cui si verifica il punto di interruzione.

`bpCondition`\
Struttura [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) che descrive le condizioni in base alle quali verrà attivato il punto di interruzione.

`bpPassCount`\
Struttura di [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) contenente le informazioni sul conteggio dei passaggi del punto di interruzione.

`dwFlags`\
Combinazione di flag dell'enumerazione [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) che specifica i flag per il punto di interruzione richiesto.

`guidVendor`\
GUID del fornitore. Può essere un valore null.

`bstrConstraint`\
Nome del vincolo di punto di interruzione. Può essere un valore null.

`bstrTracepoint`\
Nome del punto di traccia. Può essere un valore null.

## <a name="remarks"></a>Commenti
Questa struttura viene restituita dal metodo [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
