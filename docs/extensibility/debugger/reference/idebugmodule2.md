---
title: IDebugModule2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b621ae3b1408bc4af371243a1c34909117d40576
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323939"
---
# <a name="idebugmodule2"></a>IDebugModule2
Questa interfaccia rappresenta un modulo, vale a dire, un'unità di un programma eseguibile, ad esempio una DLL.

## <a name="syntax"></a>Sintassi

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un modulo e per fornire l'accesso alle informazioni su tale modulo.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) restituisce questa interfaccia. L'invia DE il [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) interfaccia per la gestione di debug di sessione (SDM) usando la [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) (metodo).

 Questa interfaccia può anche essere restituita un [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struttura (che viene restituito da una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).

- [Successivo](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) restituisce anche questa interfaccia ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) restituisce il [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) interface).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugModule2`.

|Metodo|Descrizione|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Ottiene il [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) che descrive questo modulo.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETE. NON USARE. Ricarica i simboli per questo modulo.|

## <a name="remarks"></a>Note
 Informazioni sul modulo possono essere visualizzati nei **moduli** finestra dell'IDE.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)