---
title: IDebugProgramDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramDestroyEvent2
helpviewer_keywords:
- IDebugProgramDestroyEvent2
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd9f7b97dc7479b90801ebcd07966a0058fa6476
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343532"
---
# <a name="idebugprogramdestroyevent2"></a>IDebugProgramDestroyEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di sessione di debug (SDM) quando un programma ha eseguito fino al completamento.

## <a name="syntax"></a>Sintassi

```
IDebugProgramDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE o il fornitore della porta personalizzata implementa questa interfaccia al report che un programma è stato terminato e non è più disponibile per il debug. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata per lo stesso oggetto di questa interfaccia. Usa il modello SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE o il fornitore della porta personalizzato crea e invia l'oggetto evento per segnalare la chiusura di un programma. Questo evento viene inviato il Germania usando il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito per il modello SDM quando associato al programma in fase di debug. Il fornitore della porta personalizzata invia questo evento usando il [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente illustra il metodo di `IDebugProgramDestroyEvent2`.

|Metodo|Descrizione|
|------------|-----------------|
|[GetExitCode](../../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)|Ottiene il codice di uscita del programma.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)