---
title: IDebugBreakpointErrorEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09cb93f0f16420e56104f371d9caab262873390f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735050"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Questa interfaccia indica al gestore di debug della sessione (SDM) che non è stato possibile associare un punto di interruzione in sospeso a un programma caricato, a causa di un avviso o di un errore.

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia come parte del supporto per i punti di interruzione. L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia (il SDM USA [QueryInterface](/cpp/atl/queryinterface) per accedere all' `IDebugEvent2` interfaccia).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento quando un punto di interruzione in sospeso non può essere associato al programma di cui è in corso il debug. L'evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugBreakpointErrorEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Ottiene l'interfaccia [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) che descrive l'avviso o l'errore.|

## <a name="remarks"></a>Osservazioni
 Ogni volta che viene associato un punto di interruzione, viene inviato un evento all'SDM. Se non è possibile associare il punto di interruzione, `IDebugBreakpointErrorEvent2` viene inviato un oggetto; in caso contrario, viene inviato un [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) .

 Ad esempio, quando la condizione associata al punto di interruzione in sospeso non riesce ad analizzare o valutare, viene inviato un avviso che attualmente non è possibile associare al punto di interruzione in sospeso. Questo problema può verificarsi se il codice per il punto di interruzione non è ancora stato caricato.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
