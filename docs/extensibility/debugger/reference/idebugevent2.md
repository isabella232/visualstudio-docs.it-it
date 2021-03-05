---
description: Questa interfaccia viene usata per comunicare entrambe le informazioni di debug critiche, ad esempio l'arresto in corrispondenza di un punto di interruzione e informazioni non critiche, ad esempio un messaggio di debug.
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e162e276fc93c9e2c0d4333ac0f5c2630f75618e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152949"
---
# <a name="idebugevent2"></a>IDebugEvent2
Questa interfaccia viene usata per comunicare entrambe le informazioni di debug critiche, ad esempio l'arresto in corrispondenza di un punto di interruzione e informazioni non critiche, ad esempio un messaggio di debug.

## <a name="syntax"></a>Sintassi

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) e il fornitore della porta personalizzata implementano questa interfaccia sullo stesso oggetto di tutte le altre interfacce evento.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Utilizzando l'argomento ID di interfaccia (IID) assegnato a un [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) o a un [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md), il gestore di debug della sessione chiama [QueryInterface](/cpp/atl/queryinterface) sull' `IDebugEvent2` interfaccia per ottenere l'interfaccia evento appropriata.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Ottiene gli attributi per questo evento di debug.|

## <a name="remarks"></a>Commenti
 Le interfacce di evento più specifiche, ad esempio [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), non derivano dall'interfaccia IDebugEvent2 ma vengono invece implementate come un'interfaccia separata sullo stesso oggetto di `IDebugEvent2` .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
