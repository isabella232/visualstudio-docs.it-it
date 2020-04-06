---
title: Proprietà IDebugBreakEvent2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1af6ce13de529fef5e16b3bc1be7053f0e1347b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735399"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Questa interfaccia indica al gestore di sessione di debug (SDM) che un'interruzione asincrona è stata completata correttamente.

## <a name="syntax"></a>Sintassi

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per supportare le interruzioni utente in un programma. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia `IDebugEvent2` (il modello SDM utilizza [QueryInterface](/cpp/atl/queryinterface) per accedere all'interfaccia).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il file SDM chiama [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) quando l'utente ha richiesto la sospensione del programma sottoposto a debug. Quando il programma è stato sospeso correttamente, il DE invia l'evento. `IDebugBreakEvent2` Questo evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita dal modello SDM quando è collegato al programma in fase di debug.

## <a name="remarks"></a>Osservazioni
 Ad esempio, un utente può selezionare il comando **Interrompi tutto** del menu **Debug** per uscire da un programma che esegue un ciclo infinito. Il file SDM indica al programma di interrompere chiamando [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). Il DE `IDebugBreakEvent2` invia quando il programma si ferma finalmente.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
