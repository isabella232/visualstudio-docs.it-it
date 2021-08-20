---
description: Contiene le informazioni necessarie per implementare un punto di interruzione.
title: BP_REQUEST_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe85c279173932adc3ccc4dab98cc5b0727d1b3b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145887"
---
# <a name="bp_request_info"></a>BP_REQUEST_INFO
Contiene le informazioni necessarie per implementare un punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _BP_REQUEST_INFO {
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
} BP_REQUEST_INFO;
```

```csharp
public struct BP_REQUEST_INFO {
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
};
```

## <a name="members"></a>Members
`dwFields`\
Combinazione di flag [dell'BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) che specifica quali campi vengono compilati.

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
Struttura [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) che descrive le condizioni in cui verrà generato il punto di interruzione.

`bpPassCount`\
Struttura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) che contiene le informazioni sul conteggio dei passaggi del punto di interruzione.

`dwFlags`\
Combinazione di flag [dell'enumerazione BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) che specifica i flag per il punto di interruzione richiesto.

## <a name="remarks"></a>Commenti
Questa struttura viene restituita dal [metodo GetRequestInfo.](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)

Se è necessario ottenere il GUID del fornitore del motore di debug, il vincolo del punto di interruzione o il punto di traccia, vedere la BP_REQUEST_INFO2 [struttura.](../../../extensibility/debugger/reference/bp-request-info2.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
