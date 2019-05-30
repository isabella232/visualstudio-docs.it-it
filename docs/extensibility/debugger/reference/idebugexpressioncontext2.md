---
title: IDebugExpressionContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ad9c3d6bb1b0a5baccbcf5bf47eb02a8bb5efa5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325862"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Questa interfaccia rappresenta un contesto per la valutazione dell'espressione

## <a name="syntax"></a>Sintassi

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un contesto in cui un'espressione può essere valutata.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) restituisce questa interfaccia. Questa interfaccia è accessibile solo quando il programma sottoposto a debug è stata sospesa e non è disponibile un frame dello stack.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugExpressionContext2`.

|Metodo|Descrizione|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Recupera il nome del contesto di valutazione.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analizza un'espressione basata su testo per la valutazione.|

## <a name="remarks"></a>Note
 Un contesto di valutazione può essere considerato come un ambito per l'esecuzione di valutazione dell'espressione.

 Quando un programma è interrotta, gestore di sessione di debug (SDM) Ottiene uno stack frame dal DE con una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Chiama quindi il modello SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere il `IDebugExpressionContext2` interfaccia. Questa è seguita da una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per creare un [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfaccia che rappresenta l'espressione analizzata pronta per essere valutata.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)