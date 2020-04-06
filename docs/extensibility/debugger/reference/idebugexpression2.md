---
title: Proprietà IDebugExpression2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2e23ad4f673e4e150ea677d993c5b36a4e386c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729685"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Questa interfaccia rappresenta un'espressione analizzata pronta per l'associazione e la valutazione.

## <a name="syntax"></a>Sintassi

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un'espressione analizzata pronta per essere valutata.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) restituisce questa interfaccia. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) restituisce il [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia. Queste interfacce sono accessibili solo quando il programma in fase di debug è stato sospeso ed è disponibile uno stack frame.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugExpression2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Valuta questa espressione in modo asincrono.|
|[Interrompere](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina la valutazione asincrona dell'espressione.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Valuta questa espressione in modo sincrono.|

## <a name="remarks"></a>Osservazioni
 Quando un programma è stato arrestato, il gestore di debug della sessione (SDM) ottiene uno stack frame dal DE con una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Il file SDM chiama quindi [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere il [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia. Segue una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per `IDebugExpression2` creare l'interfaccia, che rappresenta l'espressione analizzata pronta per essere valutata.

 Il file SDM chiama [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per valutare effettivamente l'espressione e produrre un valore.

 In un'implementazione di , `IDebugExpressionContext2::ParseText` `CoCreateInstance` il DE utilizza la funzione di COM per creare un'istanza `IDebugExpressionEvaluator` di un analizzatore di espressioni e ottenere un [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfaccia (vedere l'esempio nell'interfaccia ). Il DE quindi chiama [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per ottenere un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) interfaccia. Questa interfaccia viene utilizzata `IDebugExpression2::EvaluateSync` nell'implementazione di ed `IDebugExpression2::EvaluateAsync` eseguire la valutazione.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
