---
title: Proprietà IDebugPropertyCreateEvent2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84d8fcb4375f29820b51752ac3fdebbd04f06f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720926"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di sessione di debug (SDM) quando crea una proprietà associata a un documento specifico.

## <a name="syntax"></a>Sintassi

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per segnalare che una proprietà è stata creata. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Il modello SDM utilizza `IDebugEvent2` [QueryInterface](/cpp/atl/queryinterface) per accedere all'interfaccia. Questa interfaccia viene implementata se il DE ha creato una proprietà associata a uno script che è stato caricato o creato e se tale script deve essere visualizzato nell'IDE.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento per segnalare che è stata creata una proprietà. L'evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita dal modello SDM quando è collegato al programma in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente viene `IDebugPropertyCreateEvent2` illustrato il metodo dell'interfaccia.

|Metodo|Descrizione|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Ottiene la nuova proprietà.|

## <a name="remarks"></a>Osservazioni
 Se a una proprietà è associato un documento o uno script specifico, il DE può inviare questo evento al modello SDM per aggiornare la finestra **Script Documents** con il nome del documento. Il modello SDM chiamerà [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) con l'argomento `guidDocument` per recuperare un contenente un `VARIANT` puntatore [IUnknown.](/cpp/atl/iunknown) Il modello SDM chiamerà [QueryInterface](/cpp/atl/queryinterface) su questo puntatore per recuperare il [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaccia utilizzata per aggiornare il **Script Documents** finestra.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
