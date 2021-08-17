---
description: Questa interfaccia viene inviata dal motore di debug (DE) al gestore di debug sessione (SDM) quando una proprietà associata a un documento specifico sta per essere distrutta.
title: IDebugPropertyDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: de8728fa9f7ff4b74ec25d335c3519b6688f12ad1e79f10cdb5cca28d852571d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338644"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di debug sessione (SDM) quando una proprietà associata a un documento specifico sta per essere distrutta.

## <a name="syntax"></a>Sintassi

```
IDebugPropertyDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il de implementa questa interfaccia per segnalare che una proprietà è stata distrutta. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM usa [QueryInterface per](/cpp/atl/queryinterface) accedere all'interfaccia. `IDebugEvent2` Questa interfaccia viene implementata se il derea ha creato in precedenza una proprietà associata a uno script; L'eliminazione della proprietà rimuove lo script associato dall'IDE.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il de crea e invia questo oggetto evento per segnalare che una proprietà è stata distrutta. L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma di cui viene eseguito il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente viene illustrato il metodo di `IDebugPropertyDestroyEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Ottiene la proprietà da eliminare.|

## <a name="remarks"></a>Commenti
 Per informazioni dettagliate sul motivo per cui vengono usati questi eventi, vedere Note [per IDebugPropertyCreateEvent2.](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)
