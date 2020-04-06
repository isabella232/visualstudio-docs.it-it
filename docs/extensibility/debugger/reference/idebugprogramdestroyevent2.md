---
title: Proprietà IDebugProgramDestroyEvent2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramDestroyEvent2
helpviewer_keywords:
- IDebugProgramDestroyEvent2
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc83e15372a15cefccc47ea60db5ba451546ecba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722587"
---
# <a name="idebugprogramdestroyevent2"></a>IDebugProgramDestroyEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di sessione di debug (SDM) quando un programma è stato eseguito fino al completamento.

## <a name="syntax"></a>Sintassi

```
IDebugProgramDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE o il fornitore della porta personalizzata implementa questa interfaccia per segnalare che un programma è stato terminato e non è più disponibile per il debug. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Il modello SDM utilizza `IDebugEvent2` [QueryInterface](/cpp/atl/queryinterface) per accedere all'interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE o il fornitore della porta personalizzata crea e invia questo oggetto evento per segnalare la chiusura di un programma. Il DE invia questo evento utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) che viene fornita dal modello SDM quando collegato al programma in fase di debug. Il fornitore della porta personalizzata invia questo evento utilizzando il [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente viene `IDebugProgramDestroyEvent2`illustrato il metodo di .

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
