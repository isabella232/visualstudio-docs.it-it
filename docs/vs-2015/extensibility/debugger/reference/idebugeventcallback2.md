---
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6114a31701e5abc4714f315b4e4f1ecf022c401c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964649"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia viene utilizzata dal motore di debug (DE) per inviare gli eventi di debug al gestore di sessione di debug (SDM).  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] implementa questa interfaccia per ricevere eventi da un motore di debug.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Un motore di debug riceve in genere questa interfaccia quando chiama il modello SDM [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un motore di debug invia eventi per il modello SDM chiamando [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugEventCallback2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Invia una notifica di eventi per il modello SDM di debug.|  
  
## <a name="remarks"></a>Note  
 Sebbene [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) specificare che richiedono un `IDebugEventCallback2` interfaccia, non è questo il caso e il puntatore a interfaccia sarà sempre un valore null. In alternativa, è necessario usare il motore di debug la `IDebugEventCallback2` interfaccia ricevuto nella chiamata a [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Se un pacchetto implementa [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) nel codice gestito, è consigliabile che <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> essere richiamato su varie interfacce che vengono passate al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Collegare](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
