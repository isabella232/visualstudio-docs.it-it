---
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fdefbfa71ed220eed6e3f32ee95c02197f58a85d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923426"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Questa interfaccia indica al gestore di sessione di debug (SDM) che un'interruzione asincrona è stata completata correttamente.

## <a name="syntax"></a>Sintassi

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 La Germania implementa questa interfaccia per supportare le interruzioni utente in un programma. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata per lo stesso oggetto di questa interfaccia (Usa il modello SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso il `IDebugEvent2` interface).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Le chiamate SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) quando l'utente ha richiesto il programma in fase di debug per essere messo in pausa. Quando il programma è stata sospesa, la Germania invia il `IDebugBreakEvent2` evento. Questo evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback fornita dal modello SDM quando associato al programma in fase di debug.

## <a name="remarks"></a>Note
 Ad esempio, un utente può selezionare il **Interrompi tutto** comando le **Debug** menu per interrompere un programma che esegue un ciclo infinito. Il modello SDM indica al programma di arrestare chiamando [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). L'invio di DE `IDebugBreakEvent2` quando infine si arresterà.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)