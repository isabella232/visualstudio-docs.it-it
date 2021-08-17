---
description: Questa interfaccia indica al gestore di debug della sessione (SDM) che un punto di interruzione in sospeso è stato associato correttamente a un programma caricato.
title: IDebugBreakpointBoundEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2
helpviewer_keywords:
- IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ab7d7155deda4e7ab6144c3ee6b1c9d69b26a795
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079870"
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
Questa interfaccia indica al gestore di debug della sessione (SDM) che un punto di interruzione in sospeso è stato associato correttamente a un programma caricato.

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointBoundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il de implementa questa interfaccia come parte del supporto per i punti di interruzione. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia (SDM usa [QueryInterface](/cpp/atl/queryinterface) per accedere all'interfaccia). `IDebugEvent2`

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il de crea e invia questo oggetto evento quando un punto di interruzione in sospeso viene associato correttamente al programma in fase di debug. L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugBreakpointBoundEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso associato.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|Crea un enumeratore di punti di interruzione associati a questo evento.|

## <a name="remarks"></a>Commenti
 Ogni volta che viene associato un punto di interruzione, viene inviato un evento a SDM. Se il punto di interruzione non può essere associato, viene inviato [un IDebugBreakpointErrorEvent2.](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) In caso contrario, `IDebugBreakpointBoundEvent2` viene inviato un oggetto .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
