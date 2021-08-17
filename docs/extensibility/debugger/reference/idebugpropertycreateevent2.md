---
description: Questa interfaccia viene inviata dal motore di debug (DE) al gestore di debug sessione (SDM) quando crea una proprietà associata a un documento specifico.
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 124f404ef5c43bd09ec4cab4489a5709dfb7f0d9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071256"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di debug sessione (SDM) quando crea una proprietà associata a un documento specifico.

## <a name="syntax"></a>Sintassi

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il de implementa questa interfaccia per segnalare che è stata creata una proprietà. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM usa [QueryInterface per](/cpp/atl/queryinterface) accedere all'interfaccia. `IDebugEvent2` Questa interfaccia viene implementata se de ha creato una proprietà associata a uno script che è stato caricato o creato e se tale script deve essere visualizzato nell'IDE.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il de crea e invia questo oggetto evento per segnalare che è stata creata una proprietà. L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma di cui viene eseguito il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente viene illustrato il metodo `IDebugPropertyCreateEvent2` dell'interfaccia .

|Metodo|Descrizione|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Ottiene la nuova proprietà.|

## <a name="remarks"></a>Commenti
 Se a una proprietà è associato un documento o uno script specifico, il DE  può inviare questo evento a SDM per aggiornare la finestra Documenti script con il nome del documento. SDM chiamerà [GetExtendedInfo con](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) l'argomento per recuperare `guidDocument` un oggetto contenente un `VARIANT` [puntatore IUnknown.](/cpp/atl/iunknown) SDM chiamerà [QueryInterface](/cpp/atl/queryinterface) su questo puntatore per recuperare [l'interfaccia IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) usata per aggiornare la **finestra Documenti script.**

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
