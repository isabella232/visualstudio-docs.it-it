---
title: Valutazione dell'espressione in modalità di interruzione Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738729"
---
# <a name="expression-evaluation-in-break-mode"></a>Valutazione dell'espressione in modalità di interruzione
Nella sezione seguente viene descritto il processo che si verifica quando il debugger è in modalità di interruzione e deve eseguire la valutazione dell'espressione.

## <a name="expression-evaluation-process"></a>Processo di valutazione delle espressioni
 Di seguito sono riportati i passaggi di base necessari per valutare un'espressione:

1. Il gestore di sessione di debug (SDM) chiama [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere un'interfaccia di contesto di espressione, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. Il file SDM chiama quindi [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la stringa da analizzare.

3. Se ParseText non restituisce S_OK, viene restituito il motivo dell'errore.

     -altrimenti-

     Se ParseText restituisce S_OK, il file SDM può quindi chiamare [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere un valore finale dall'espressione analizzata.

    - Quando `IDebugExpression2::EvaluateSync`si utilizza , l'interfaccia di callback specificata comunica il processo in corso della valutazione. Il valore finale viene restituito in un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia.

    - Quando `IDebugExpression2::EvaluateAsync`si utilizza , l'interfaccia di callback specificata comunica il processo in corso della valutazione. Al termine della valutazione, EvaluateAsync invia [un'interfaccia IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) tramite il callback. Con questa interfaccia eventi, il valore finale risulta con [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Vedere anche
- [Chiamare eventi del debuggerCall debugger events](../../extensibility/debugger/calling-debugger-events.md)
