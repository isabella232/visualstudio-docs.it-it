---
description: Questa interfaccia indica al gestore di debug della sessione (SDM) che un'operazione asincrona è stata completata correttamente.
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8d2369b2219d155b2210fb2860cc868ec3813bad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088796"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Questa interfaccia indica al gestore di debug della sessione (SDM) che un'operazione asincrona è stata completata correttamente.

## <a name="syntax"></a>Sintassi

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per supportare le interruzioni utente in un programma. L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia (il SDM USA [QueryInterface](/cpp/atl/queryinterface) per accedere all' `IDebugEvent2` interfaccia).

## <a name="notes-for-callers"></a>Note per i chiamanti
 SDM chiama [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) quando l'utente ha richiesto la sospensione del programma di cui è in corso il debug. Quando il programma viene sospeso correttamente, il DE invia l' `IDebugBreakEvent2` evento. Questo evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug.

## <a name="remarks"></a>Commenti
 Un utente può, ad esempio, selezionare il comando **Interrompi tutto** dal menu **debug** per suddividere in un programma che esegue un ciclo infinito. SDM indica al programma di arrestarsi chiamando [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). Il DE Invia `IDebugBreakEvent2` quando il programma si arresta.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
