---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5c09b81a6a3eb56734e7d3a95dc5d1a8d1717fba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933115"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Il motore di debug (DE) Invia questa interfaccia a gestione debug sessione (SDM) quando viene generata un'eccezione nel programma attualmente in esecuzione.

## <a name="syntax"></a>Sintassi

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per segnalare che si è verificata un'eccezione nel programma di cui è in corso il debug. L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM utilizza [QueryInterface](/cpp/atl/queryinterface) per accedere all' `IDebugEvent2` interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento per segnalare un'eccezione. L'evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugExceptionEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Ottiene informazioni dettagliate sull'eccezione che ha generato l'evento.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Ottiene una descrizione leggibile per l'eccezione generata che ha generato l'evento.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Determina se il motore di debug (DE) supporta l'opzione di passaggio di questa eccezione al programma di cui è in corso il debug al riavvio dell'esecuzione.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Specifica se l'eccezione deve essere passata al programma di cui è in corso il debug al riavvio dell'esecuzione o se l'eccezione deve essere eliminata.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Commenti
 Prima di inviare l'evento, il DE verifica se questo evento di eccezione è stato designato come un'eccezione first-chance o Second-Chance da una precedente chiamata a [seexception](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Se è stato designato come un'eccezione first-chance, l' `IDebugExceptionEvent2` evento viene inviato a SDM. In caso contrario, il DE fornisce all'applicazione la possibilità di gestire l'eccezione. Se non viene fornito alcun gestore eccezioni e se l'eccezione è stata designata come un'eccezione di seconda probabilità, l' `IDebugExceptionEvent2` evento viene inviato a SDM. In caso contrario, il DE riprende l'esecuzione del programma e il sistema operativo o il runtime gestisce l'eccezione.

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
