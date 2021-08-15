---
description: Il motore di debug (DE) invia questa interfaccia alla gestione del debug di sessione (SDM) quando un programma si arresta in corrispondenza di un punto di interruzione.
title: IDebugBreakpointEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointEvent2
helpviewer_keywords:
- IDebugBreakpointEvent2 interface
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: bf70a3957dba4aa1ecdc29a904ba019363c8816b89b14bd4740363c078e29e41
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360612"
---
# <a name="idebugbreakpointevent2"></a>IDebugBreakpointEvent2
Il motore di debug (DE) invia questa interfaccia alla gestione del debug di sessione (SDM) quando un programma si arresta in corrispondenza di un punto di interruzione.

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il de implementa questa interfaccia come parte del supporto per i punti di interruzione. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia (SDM usa [QueryInterface](/cpp/atl/queryinterface) per accedere all'interfaccia). `IDebugEvent2`

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il de crea e invia questo oggetto evento quando viene rilevato almeno un punto di interruzione nel programma. L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugBreakpointEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|Crea un enumeratore per tutti i punti di interruzione generati nella posizione del codice corrente.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
