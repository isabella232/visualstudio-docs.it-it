---
title: Proprietà IDebugEvent2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6341f8003b962a7f45420b076b23623ebdaf861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729906"
---
# <a name="idebugevent2"></a>IDebugEvent2
Questa interfaccia viene utilizzata per comunicare sia informazioni di debug critiche, ad esempio l'arresto in corrispondenza di un punto di interruzione, sia informazioni non critiche, ad esempio un messaggio di debug.

## <a name="syntax"></a>Sintassi

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) e il fornitore di porta personalizzato implementano questa interfaccia sullo stesso oggetto di tutte le altre interfacce di eventi.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Utilizzando l'argomento ID di interfaccia (IID) fornito a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) o [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md), il gestore di sessione di debug (SDM) chiama [QueryInterface](/cpp/atl/queryinterface) sull'interfaccia `IDebugEvent2` per ottenere l'interfaccia eventi appropriata.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugEvent2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Ottiene gli attributi per questo evento di debug.|

## <a name="remarks"></a>Osservazioni
 Le interfacce eventi più specifiche, ad esempio [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), non derivano dall'interfaccia IDebugEvent2, `IDebugEvent2`ma vengono invece implementate come un'interfaccia separata sullo stesso oggetto di .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
