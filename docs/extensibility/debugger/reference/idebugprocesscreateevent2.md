---
title: IDebugProcessCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessCreateEvent2
helpviewer_keywords:
- IDebugProcessCreateEvent2
ms.assetid: c660439d-8b23-4dbb-923e-ebb5e1d7edf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cfc9b0bbdebde01af48ab1436dbfd17ac0c3241b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723531"
---
# <a name="idebugprocesscreateevent2"></a>IDebugProcessCreateEvent2
Questa interfaccia viene inviata quando viene avviato un processo.

## <a name="syntax"></a>Sintassi

```
IDebugProcessCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) o il fornitore della porta personalizzata implementa questa interfaccia per segnalare che è stato creato un processo. L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM utilizza [QueryInterface](/cpp/atl/queryinterface) per accedere all' `IDebugEvent2` interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il fornitore della porta DE o Custom crea e invia questo oggetto evento per segnalare la creazione di un processo. Il DE Invia questo evento usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug. Il fornitore della porta personalizzata invia questo evento usando l'interfaccia [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
