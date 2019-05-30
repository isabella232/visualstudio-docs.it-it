---
title: Valutazione dell'espressione in modalità di interruzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af231333981697705ba58fe505b0bf55304b8287
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353832"
---
# <a name="expression-evaluation-in-break-mode"></a>Valutazione dell'espressione in modalità di interruzione
La sezione seguente descrive il processo che si verifica quando il debugger è in modalità di interruzione e deve eseguire la valutazione dell'espressione.

## <a name="expression-evaluation-process"></a>Processo di valutazione di espressioni
 Ecco i passaggi fondamentali nella valutazione di un'espressione:

1. Gestore di sessione di debug (SDM) chiama [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere un'interfaccia di contesto, espressione [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. Chiama quindi il modello SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la stringa da analizzare.

3. Se ParseText non restituisce S_OK, viene restituito il motivo dell'errore.

     -otherwise-

     Se ParseText restituisce S_OK, il modello SDM può quindi chiamare [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oppure [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere un valore finale dall'espressione analizzata.

    - Quando si usa `IDebugExpression2::EvaluateSync`, l'interfaccia di callback specificato comunica il processo continuo di valutazione. Viene restituito il valore finale un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia.

    - Quando si usa `IDebugExpression2::EvaluateAsync`, l'interfaccia di callback specificato comunica il processo continuo di valutazione. Una volta completata la valutazione, EvaluateAsync invia un' [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfaccia tramite il callback. Con questa interfaccia, il valore finale dei risultati con [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Vedere anche
- [Chiamare gli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)