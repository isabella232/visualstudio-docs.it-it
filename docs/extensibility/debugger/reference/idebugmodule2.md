---
description: Questa interfaccia rappresenta un modulo, ovvero un'unità eseguibile di un programma, ad esempio una DLL.
title: IDebugModule2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 848aa60ad7b8343d84489f460cfcb5fb6ec2d77d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065554"
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
 Una chiamata a [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) restituisce questa interfaccia. Il DE invia l'interfaccia [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) al gestore di debug della sessione (SDM) usando il metodo dell' [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .

 Questa interfaccia può essere restituita anche in una struttura [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) , che viene restituita da una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md).

- [Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) restituisce inoltre questa interfaccia ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) restituisce l'interfaccia [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) ).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugModule2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Ottiene la [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) che descrive il modulo.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETE. NON USARE. Ricarica i simboli per questo modulo.|

## <a name="remarks"></a>Commenti
 Le informazioni sul modulo possono essere visualizzate nella finestra **moduli** dell'IDE.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
