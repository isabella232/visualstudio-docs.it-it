---
title: Valutazione delle espressioni in modalità di interruzioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc09fc43bd9f0edea4f6dc32e5f37c387c045796
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738729"
---
# <a name="expression-evaluation-in-break-mode"></a>Valutazione delle espressioni in modalità di interruzioni
Nella sezione seguente viene descritto il processo che si verifica quando il debugger è in modalità di interruzione ed è necessario eseguire la valutazione dell'espressione.

## <a name="expression-evaluation-process"></a>Processo di valutazione delle espressioni
 Di seguito sono riportati i passaggi di base necessari per la valutazione di un'espressione:

1. Il gestore di debug della sessione chiama [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere un'interfaccia del contesto dell'espressione, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. Il SDM chiama quindi [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la stringa da analizzare.

3. Se ParseText non restituisce S_OK, viene restituito il motivo dell'errore.

     in caso contrario

     Se ParseText restituisce S_OK, SDM può quindi chiamare [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere un valore finale dall'espressione analizzata.

    - Quando si usa `IDebugExpression2::EvaluateSync` , l'interfaccia di callback specificata comunica il processo in corso della valutazione. Il valore finale viene restituito in un'interfaccia [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .

    - Quando si usa `IDebugExpression2::EvaluateAsync` , l'interfaccia di callback specificata comunica il processo in corso della valutazione. Al termine della valutazione, EvaluateAsync Invia un'interfaccia [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) tramite il callback. Con questa interfaccia evento, il valore finale restituisce [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Vedere anche
- [Chiama eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
