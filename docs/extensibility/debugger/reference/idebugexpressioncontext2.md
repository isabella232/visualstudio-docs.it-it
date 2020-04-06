---
title: Proprietà IDebugExpressionContext2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 344ae287b3784ceca87fbbab09ad2b2e0a304205
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729636"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Questa interfaccia rappresenta un contesto per la valutazione delle espressioni

## <a name="syntax"></a>Sintassi

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un contesto in cui è possibile valutare un'espressione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) restituisce l'interfaccia this. Questa interfaccia è accessibile solo quando il programma in fase di debug è stato sospeso ed è disponibile uno stack frame.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugExpressionContext2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Recupera il nome del contesto di valutazione.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analizza un'espressione basata su testo per la valutazione.|

## <a name="remarks"></a>Osservazioni
 Un contesto di valutazione può essere considerato come un ambito per l'esecuzione della valutazione dell'espressione.

 Quando un programma è stato arrestato, il gestore di debug della sessione (SDM) ottiene uno stack frame dal DE con una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Il file SDM chiama quindi `IDebugExpressionContext2` [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere l'interfaccia. Questo è seguito da una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per creare un [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfaccia, che rappresenta l'espressione analizzata pronta per essere valutata.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
