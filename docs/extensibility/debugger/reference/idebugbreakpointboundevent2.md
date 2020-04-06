---
title: Proprietà IDebugBreakpointBoundEvent2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2
helpviewer_keywords:
- IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7943addb4334710da3252a4d822330e45b6e0f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735306"
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
Questa interfaccia indica al gestore di sessione di debug (SDM) che un punto di interruzione in sospeso è stato associato correttamente a un programma caricato.

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointBoundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia come parte del supporto per i punti di interruzione. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia `IDebugEvent2` (il modello SDM utilizza [QueryInterface](/cpp/atl/queryinterface) per accedere all'interfaccia).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento quando un punto di interruzione in sospeso viene associato correttamente al programma in fase di debug. L'evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita dal modello SDM quando è collegato al programma in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugBreakpointBoundEvent2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso che viene associato.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|Crea un enumeratore di punti di interruzione associati a questo evento.|

## <a name="remarks"></a>Osservazioni
 Ogni volta che viene associato un punto di interruzione, viene inviato un evento al modello SDM. Se il punto di interruzione non può essere associato, un [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) viene inviato; in caso `IDebugBreakpointBoundEvent2` contrario, viene inviato un oggetto .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
