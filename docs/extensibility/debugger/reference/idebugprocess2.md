---
description: Questa interfaccia rappresenta un processo in esecuzione su una porta.
title: Interfaccia IDebugProcess2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 47acaa5d1776bd35fd6c418dab9abd3158b6ac8b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132834"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Questa interfaccia rappresenta un processo in esecuzione su una porta. Se la porta è la porta locale, in genere `IDebugProcess2` rappresenta un processo fisico nel computer locale.

## <a name="syntax"></a>Sintassi

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un fornitore di porte personalizzato per gestire i programmi come gruppo. Questa interfaccia deve essere implementata dal fornitore della porta.

 Un motore di debug implementa anche questa interfaccia se supporta l'avvio di un programma [tramite LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata principalmente da Gestione debug sessione (SDM) per interagire con un gruppo di programmi identificati in questo processo.

 Chiamare [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) o [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) per ottenere questa interfaccia. Questa interfaccia viene restituita anche chiamando `IDebugEngineLaunch2::LaunchSuspended` .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugProcess2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Ottiene una descrizione del processo.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Enumera i programmi contenuti in questo processo.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Ottiene il titolo, il nome descrittivo o il nome file del processo.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Ottiene l'istanza di un server del computer in cui è in esecuzione questo processo.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md).|Termina il processo.|
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Si connette al processo.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Determina se SDM può scollegare il processo.|
|[Scollega](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Scollega il debugger dal processo.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Ottiene l'identificatore del processo di sistema.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Ottiene un identificatore univoco globale per questo processo.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [DEPRECATO]|Ottiene il nome della sessione che esegue il debug del processo.<br /><br /> [DEPRECATO. DEVE SEMPRE RESTITUIRE `E_NOTIMPL` .]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Enumera i thread in esecuzione nel processo.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Richiede l'arresto del programma successivo che esegue il codice in questo processo.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Ottiene la porta su cui è in esecuzione questo processo.|

## <a name="remarks"></a>Commenti
 Contiene `IDebugProcess2` una o più interfacce [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md)

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Avanti](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
