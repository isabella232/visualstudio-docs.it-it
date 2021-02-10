---
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d7b6508a635edf3dc328f79a06a386efce07aae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949584"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Questa interfaccia rappresenta un'espressione analizzata pronta per l'associazione e la valutazione.

## <a name="syntax"></a>Sintassi

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un'espressione analizzata pronta per la valutazione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) restituisce questa interfaccia. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) restituisce l'interfaccia [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Queste interfacce sono accessibili solo quando il programma di cui è in corso il debug è stato sospeso ed è disponibile un stack frame.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugExpression2` .

|Metodo|Descrizione|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Valuta questa espressione in modo asincrono.|
|[Interruzione](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina la valutazione dell'espressione asincrona.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Valuta questa espressione in modo sincrono.|

## <a name="remarks"></a>Commenti
 Quando un programma si interrompe, gestione debug sessione (SDM) ottiene un stack frame da DE con una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Il SDM chiama quindi [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere l'interfaccia [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Questa operazione è seguita da una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per creare l' `IDebugExpression2` interfaccia, che rappresenta l'espressione analizzata pronta per la valutazione.

 SDM chiama [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per valutare effettivamente l'espressione e produrre un valore.

 In un'implementazione di `IDebugExpressionContext2::ParseText` , il de utilizza la `CoCreateInstance` funzione com per creare un'istanza di un analizzatore di espressioni e ottenere un'interfaccia [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) (vedere l'esempio nell' `IDebugExpressionEvaluator` interfaccia). Il DE chiama quindi [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per ottenere un'interfaccia [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) . Questa interfaccia viene utilizzata nell'implementazione di `IDebugExpression2::EvaluateSync` e `IDebugExpression2::EvaluateAsync` per eseguire la valutazione.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
