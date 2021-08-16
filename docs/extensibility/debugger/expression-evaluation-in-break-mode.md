---
title: Valutazione delle espressioni in modalità di interruzione | Microsoft Docs
description: Informazioni sul processo che si verifica quando il debugger è in modalità di interruzione e deve eseguire la valutazione delle espressioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: c0b1264063553b13d3401f770dbd08ef2a51417df2314c30e895987a969851e3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378120"
---
# <a name="expression-evaluation-in-break-mode"></a>Valutazione delle espressioni in modalità di interruzione
Nella sezione seguente viene descritto il processo che si verifica quando il debugger è in modalità di interruzione e deve eseguire la valutazione delle espressioni.

## <a name="expression-evaluation-process"></a>Processo di valutazione delle espressioni
 Di seguito sono riportati i passaggi di base necessari per la valutazione di un'espressione:

1. Gestione debug sessione (SDM) chiama [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere un'interfaccia del contesto dell'espressione, [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

2. SDM chiama quindi [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la stringa da analizzare.

3. Se ParseText non restituisce S_OK, viene restituito il motivo dell'errore.

     -in caso contrario,

     Se ParseText restituisce S_OK, SDM può quindi chiamare [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere un valore finale dall'espressione analizzata.

    - Quando si `IDebugExpression2::EvaluateSync` usa , l'interfaccia di callback specificata comunica il processo in corso della valutazione. Il valore finale viene restituito in [un'interfaccia IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md)

    - Quando si `IDebugExpression2::EvaluateAsync` usa , l'interfaccia di callback specificata comunica il processo in corso della valutazione. Al termine della valutazione, EvaluateAsync invia [un'interfaccia IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) tramite il callback. Con questa interfaccia eventi, il valore finale viene restituito con [GetResult.](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)

## <a name="see-also"></a>Vedi anche
- [Chiamare eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
