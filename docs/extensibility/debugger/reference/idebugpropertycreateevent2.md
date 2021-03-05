---
description: Questa interfaccia viene inviata dal motore di debug (DE) a gestione debug sessione (SDM) quando crea una proprietà associata a un documento specifico.
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0a8a4317ec3e1c2c83becf0bffb5274ae5a44cf4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168049"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Questa interfaccia viene inviata dal motore di debug (DE) a gestione debug sessione (SDM) quando crea una proprietà associata a un documento specifico.

## <a name="syntax"></a>Sintassi

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per segnalare che è stata creata una proprietà. L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM utilizza [QueryInterface](/cpp/atl/queryinterface) per accedere all' `IDebugEvent2` interfaccia. Questa interfaccia viene implementata se il DE ha creato una proprietà associata a uno script che è stato caricato o creato e se lo script deve essere visualizzato nell'IDE.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento per segnalare che è stata creata una proprietà. L'evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente viene illustrato il metodo dell' `IDebugPropertyCreateEvent2` interfaccia.

|Metodo|Descrizione|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Ottiene la nuova proprietà.|

## <a name="remarks"></a>Commenti
 Se a una proprietà è associato un documento o uno script specifico, il DE può inviare questo evento all'SDM per aggiornare la finestra **documenti script** con il nome del documento. SDM chiamerà [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) con l'argomento `guidDocument` per recuperare un oggetto `VARIANT` contenente un puntatore [IUnknown](/cpp/atl/iunknown) . SDM chiamerà [QueryInterface](/cpp/atl/queryinterface) su questo puntatore per recuperare l'interfaccia [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) utilizzata per aggiornare la finestra **documenti script** .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
