---
title: IDebugThreadCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThreadCreateEvent2
helpviewer_keywords:
- IDebugThreadCreateEvent2
ms.assetid: aee34a14-4f9c-4ad3-845f-c96ee938cefd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1aaa25e719f17701344d821759a0dac06aa88698
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718533"
---
# <a name="idebugthreadcreateevent2"></a>IDebugThreadCreateEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di debug della sessione (SDM) quando viene creato un thread in un programma di cui è in corso il debug.

## <a name="syntax"></a>Sintassi

```
IDebugThreadCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per segnalare che un thread è stato creato. L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM utilizza [QueryInterface](/cpp/atl/queryinterface) per accedere all' `IDebugEvent2` interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento per segnalare che è stato creato un thread. L'evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
