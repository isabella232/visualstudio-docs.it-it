---
title: Proprietà IDebugProcess2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72659491ec6718397a4fbb494175eea0896c7f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723807"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Questa interfaccia rappresenta un processo in esecuzione su una porta. Se la porta è la `IDebugProcess2` porta locale, rappresenta in genere un processo fisico nel computer locale.

## <a name="syntax"></a>Sintassi

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un fornitore di porta personalizzato per gestire i programmi come gruppo. Questa interfaccia deve essere implementata dal fornitore della porta.

 Un motore di debug implementa anche questa interfaccia se supporta l'avvio di un programma tramite [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata principalmente dal gestore di sessione di debug (SDM) per interagire con un gruppo di programmi identificati in questo processo.

 Chiamare [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) o [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) per ottenere questa interfaccia. Questa interfaccia viene restituita `IDebugEngineLaunch2::LaunchSuspended`anche chiamando .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugProcess2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Ottiene una descrizione del processo.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Enumera i programmi contenuti in questo processo.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Ottiene il titolo, il nome descrittivo o il nome file del processo.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Ottiene l'istanza di un server del computer in cui è in esecuzione questo processo.|
|[Terminare](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Termina il processo.|
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Si connette al processo.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Determina se il modello SDM può scollegare il processo.|
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Disconnette il debugger dal processo.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Ottiene l'identificatore del processo di sistema.|
|[IdProcessoGetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Ottiene un identificatore univoco globale per questo processo.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [DEPRECATO]|Ottiene il nome della sessione che esegue il debug del processo.<br /><br /> [DEPRECATO. DEVE SEMPRE `E_NOTIMPL`RESTITUIRE .]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Enumera i thread in esecuzione nel processo.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Richiede che il codice in esecuzione del programma successivo in questo processo venga interrotto.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Ottiene la porta su cui è in esecuzione questo processo.|

## <a name="remarks"></a>Osservazioni
 Un `IDebugProcess2` contiene una o più [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfacce.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Avanti](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
