---
title: Valutazione delle espressioni (Visual Studio Debugging SDK) Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e41179fd530818f5ac59aa54420ede1b4eafa1ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738706"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Valutazione delle espressioni (Visual Studio Debugging SDK)
Durante la modalità di interruzione, l'IDE deve valutare espressioni semplici che coinvolgono diverse variabili di programma. Per eseguire la valutazione, il motore di debug (DE) deve analizzare e valutare un'espressione immessa in una delle finestre dell'IDE.

 Le espressioni vengono create con il [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metodo e rappresentate dal [risultante IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia.

 Il **IDebugExpression2** interfaccia viene implementata dal DE e chiama il relativo **EvalAsync** metodo per restituire un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia all'IDE, al fine di visualizzare i risultati della valutazione dell'espressione nell'IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) restituisce una struttura utilizzata per inserire il valore di un'espressione in una finestra **Espressioni** di controllo o nella finestra **Variabili locali.**

 Il gestore di debug (SDM) del pacchetto di debug o della sessione chiama [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per ottenere un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta il risultato della valutazione. `IDebugProperty2`dispone di metodi che restituiscono il nome, il tipo e il valore dell'espressione. Queste informazioni vengono visualizzate in varie finestre del debugger.

## <a name="using-expression-evaluation"></a>Utilizzo della valutazione delle espressioniUsing expression evaluation
 Per utilizzare la valutazione delle espressioni, è necessario implementare il [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metodo e tutti i metodi del [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia, come illustrato nella tabella seguente.

|Metodo|Descrizione|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Valuta un'espressione in modo asincrono.|
|[Interrompere](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina la valutazione asincrona dell'espressione.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Valuta un'espressione in modo sincrono.|

 La valutazione sincrona e asincrona richiede l'implementazione del metodo [IDebugProperty2::GetPropertyInfo.Synchronous](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) and asynchronous evaluation require implementing the IDebugProperty2::GetPropertyInfo method. La valutazione asincrona dell'espressione richiede l'implementazione di [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Vedere anche
- [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
