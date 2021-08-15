---
description: Questa interfaccia viene utilizzata per comunicare informazioni di debug critiche, ad esempio l'arresto in corrispondenza di un punto di interruzione, e informazioni non critiche, ad esempio un messaggio di debug.
title: Interfaccia IDebugEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 71b36a0647baa9ff7224fde5ad65ea073153497a0eaabd83feb80b6ffc0cc397
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121238918"
---
# <a name="idebugevent2"></a>IDebugEvent2
Questa interfaccia viene utilizzata per comunicare informazioni di debug critiche, ad esempio l'arresto in corrispondenza di un punto di interruzione, e informazioni non critiche, ad esempio un messaggio di debug.

## <a name="syntax"></a>Sintassi

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) e il fornitore di porte personalizzate implementano questa interfaccia sullo stesso oggetto di tutte le altre interfacce di evento.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Usando l'argomento IID (Interface [](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ID) assegnato all'evento o all'evento [,](../../../extensibility/debugger/reference/idebugportevents2-event.md)gestione debug sessione chiama [QueryInterface](/cpp/atl/queryinterface) sull'interfaccia per ottenere l'interfaccia `IDebugEvent2` evento appropriata.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Ottiene gli attributi per questo evento di debug.|

## <a name="remarks"></a>Commenti
 Le interfacce eventi più specifiche, ad esempio [IDebugBreakpointEvent2,](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)non derivano dall'interfaccia IDebugEvent2, ma vengono implementate come interfaccia separata nello stesso oggetto di `IDebugEvent2` .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
