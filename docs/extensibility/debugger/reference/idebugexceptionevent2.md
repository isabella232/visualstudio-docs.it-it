---
description: Il motore di debug invia questa interfaccia alla gestione del debug di sessione (SDM) quando viene generata un'eccezione nel programma attualmente in esecuzione.
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 0fe5176217e0c683c2a68b36b0276015ccdc16c0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710297"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Il motore di debug invia questa interfaccia alla gestione del debug di sessione (SDM) quando viene generata un'eccezione nel programma attualmente in esecuzione.

## <a name="syntax"></a>Sintassi

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 De implementa questa interfaccia per segnalare che si è verificata un'eccezione nel programma di cui è in corso il debug. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM usa [QueryInterface per](/cpp/atl/queryinterface) accedere all'interfaccia. `IDebugEvent2`

## <a name="notes-for-callers"></a>Note per i chiamanti
 De crea e invia questo oggetto evento per segnalare un'eccezione. L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma di cui è in corso il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugExceptionEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Ottiene informazioni dettagliate sull'eccezione che ha generato questo evento.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Ottiene una descrizione leggibile per l'eccezione generata che ha generato questo evento.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Determina se il motore di debug supporta o meno l'opzione per passare questa eccezione al programma di cui è in corso il debug alla ripresa dell'esecuzione.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Specifica se l'eccezione deve essere passata al programma di cui è in corso il debug alla ripresa dell'esecuzione o se l'eccezione deve essere eliminata.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Commenti
 Prima di inviare l'evento, de controlla se questo evento di eccezione è stato designato come eccezione first-chance o second-chance da una chiamata precedente a [SetException.](../../../extensibility/debugger/reference/idebugengine2-setexception.md) Se è stato designato come eccezione first-chance, `IDebugExceptionEvent2` l'evento viene inviato a SDM. In caso contrario, de offre all'applicazione la possibilità di gestire l'eccezione. Se non viene fornito alcun gestore di eccezioni e se l'eccezione è stata designata come eccezione second-chance, l'evento viene `IDebugExceptionEvent2` inviato a SDM. In caso contrario, de riprende l'esecuzione del programma e il sistema operativo o il runtime gestisce l'eccezione.

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
