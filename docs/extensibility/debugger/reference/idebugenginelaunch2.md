---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4485001341399d3830864a30b64fec24a77c5a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892723"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Utilizzato da un motore di debug (DE) per avviare e terminare i programmi.

## <a name="syntax"></a>Sintassi

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un oggetto personalizzato se dispone di requisiti speciali per l'avvio di un processo che non può essere gestito interamente da una porta personalizzata. Questa situazione si verifica in genere quando il DE fa parte di un interprete e il processo di cui è in corso il debug è uno script: l'interprete deve essere avviato per primo, quindi lo script viene caricato e avviato. Una porta può avviare l'interprete, ma è possibile che lo script richieda una gestione speciale (dove il DE ha un ruolo). Questa interfaccia viene implementata solo se sono presenti requisiti specifici per l'avvio di un programma non gestibile da una porta personalizzata.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata da gestione debug sessione (SDM) se SDM può ottenere questa interfaccia dall'interfaccia [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (usando QueryInterface). Se è possibile ottenere questa interfaccia, il SDM sa che il DE dispone di requisiti speciali e chiama questa interfaccia per avviare il programma anziché fare in modo che la porta venga avviata.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugEngineLaunch2` .

|Metodo|Descrizione|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Avvia un processo per mezzo di DE.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Riprende l'esecuzione del processo.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Determina se un processo può essere terminato.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Termina un processo.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
