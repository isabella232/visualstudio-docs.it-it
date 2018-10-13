---
title: IDebugProcess2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5d1fcdb6df958a62ed23b3bc7e812e1f4a7e15f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218777"
---
# <a name="idebugprocess2"></a>IDebugProcess2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta un processo in esecuzione su una porta. Se la porta è la porta locale, quindi `IDebugProcess2` rappresenta in genere un processo nel computer locale fisico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata da un fornitore di porte personalizzate per i programmi sono gestiti come gruppo. Questa interfaccia deve essere implementata dal fornitore della porta.  
  
 Un motore di debug anche implementa questa interfaccia se supporta l'avvio di un programma attraverso [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene chiamata principalmente dal gestore di sessione di debug (SDM) per interagire con un gruppo di programmi identificate in questo processo.  
  
 Chiamare [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) oppure [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) per ottenere questa interfaccia. Questa interfaccia viene inoltre restituita chiamando `IDebugEngineLaunch2::LaunchSuspended`.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProcess2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Ottiene una descrizione del processo.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Enumera i programmi contenuti in questo processo.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Ottiene il titolo, un nome descrittivo o un nome di file del processo.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Ottiene l'istanza di questo processo è in esecuzione in una macchina server.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Termina il processo.|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Collega al processo.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Determina se il modello SDM possibile scollegare il processo.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Scollega debugger dal processo.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Ottiene l'identificatore di processo di sistema.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Ottiene un identificatore univoco globale per questo processo.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [DEPRECATO]|Ottiene il nome della sessione che sta eseguendo il debug del processo.<br /><br /> [DEPRECATO. DEVE SEMPRE RESTITUIRE `E_NOTIMPL`.]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Enumera i thread in esecuzione nel processo.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Richiede che il successivo programma in esecuzione di codice in arrestare questo processo.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Ottiene la porta su cui è in esecuzione in questo processo.|  
  
## <a name="remarks"></a>Note  
 Un' `IDebugProcess2` contiene uno o più [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfacce.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Avanti](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

