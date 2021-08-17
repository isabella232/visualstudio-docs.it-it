---
description: Questa interfaccia viene usata dal motore di debug (DE) per inviare eventi di debug al gestore di debug di sessione (SDM).
title: Interfaccia IDebugEventCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a4d75583b2c936b82e167618356a9ae0547f337e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089017"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Questa interfaccia viene usata dal motore di debug (DE) per inviare eventi di debug al gestore di debug di sessione (SDM).

## <a name="syntax"></a>Sintassi

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementa questa interfaccia per ricevere eventi da un motore di debug.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Un motore di debug riceve in genere questa interfaccia quando SDM chiama [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un motore di debug invia eventi a SDM chiamando [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugEventCallback2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Invia una notifica degli eventi di debug a SDM.|

## <a name="remarks"></a>Commenti
 Anche [se EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) specificano che accettano un'interfaccia, questo non è il caso e il puntatore a interfaccia `IDebugEventCallback2` sarà sempre un valore Null. Il motore di debug deve invece usare l'interfaccia ricevuta nella chiamata a `IDebugEventCallback2` [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Se un pacchetto implementa [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) nel codice gestito, è consigliabile richiamare le varie interfacce passate <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> [all'evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
