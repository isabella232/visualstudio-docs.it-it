---
title: Proprietà IDebugModule2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbbea1b52133de41dd26f437aeba31a0eff5a50a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726913"
---
# <a name="idebugmodule2"></a>IDebugModule2
Questa interfaccia rappresenta un modulo, ovvero un'unità eseguibile di un programma, ad esempio una DLL.

## <a name="syntax"></a>Sintassi

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un modulo e per fornire l'accesso alle informazioni su tale modulo.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) restituisce questa interfaccia. Il DE invia il [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) interfaccia al gestore di sessione di debug (SDM) utilizzando il [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metodo.

 Questa interfaccia può essere restituita anche in un [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struttura (che viene restituita da una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).

- [Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) restituisce anche questa interfaccia ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) restituisce il [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) interfaccia).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugModule2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Ottiene il [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) che descrive questo modulo.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETO. NON UTILIZZARE. Ricarica i simboli per questo modulo.|

## <a name="remarks"></a>Osservazioni
 Le informazioni sui moduli possono essere visualizzate nella finestra **Moduli** dell'IDE.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [Metodo GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
