---
title: IDebugReturnValueEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReturnValueEvent2
helpviewer_keywords:
- IDebugReturnValueEvent2
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0afc4284795ae8dcae7b41d9207ddc6e7c11e67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720254"
---
# <a name="idebugreturnvalueevent2"></a>IDebugReturnValueEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di debug della sessione (SDM) dopo l'esecuzione dell'istruzione/routine di una funzione.

## <a name="syntax"></a>Sintassi

```
IDebugReturnValueEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per segnalare il valore restituito da una funzione di cui è stato effettuato il ripasso o superiore. L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM utilizza [QueryInterface](/cpp/atl/queryinterface) per accedere all' `IDebugEvent2` interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento per segnalare il valore restituito di una funzione. L'evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente viene illustrato il metodo di `IDebugReturnValueEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|Ottiene il valore restituito durante l'esecuzione dell'istruzione/routine di una funzione.|

## <a name="remarks"></a>Osservazioni
 Il valore restituito da una funzione può essere ottenuto chiamando [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md). Il valore restituito viene visualizzato nella finestra **auto** .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
