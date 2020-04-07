---
title: Valutazione di un'espressione della finestra Espressioni di controllo Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cef2f27eec095ee7b136153ecb764feba9effbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738846"
---
# <a name="evaluate-a-watch-window-expression"></a>Valutare un'espressione della finestra Espressioni di controlloEvaluate a watch window expression
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Quando l'esecuzione viene sospesa, Visual Studio chiama il motore di debug (DE) per determinare il valore corrente di ogni espressione nel relativo elenco di controllo. Il DE valuta ogni espressione utilizzando un analizzatore di espressioni (EE) e Visual Studio visualizza il relativo valore nella finestra **Espressioni di controllo.**

 Di seguito è riportata una panoramica di come viene valutata un'espressione della lista di controllo:

1. Visual Studio chiama il DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere un contesto di espressione che può essere utilizzato per valutare le espressioni.

2. Per ogni espressione nell'elenco di controllo, Visual Studio chiama [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per convertire il testo dell'espressione in un'espressione analizzata.

3. `IDebugExpressionContext2::ParseText`chiama [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per eseguire il lavoro effettivo di analisi del testo e produrre un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) oggetto.

4. `IDebugExpressionContext2::ParseText`crea un [oggetto IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e vi inserisce l'oggetto. `IDebugParsedExpression` Questo`DebugExpression2` oggetto I viene quindi restituito a Visual Studio.This I object is then returned to Visual Studio.

5. Visual Studio chiama [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per valutare l'espressione analizzata.

6. `IDebugExpression2::EvaluateSync`passa la chiamata a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) per eseguire la valutazione effettiva e produrre un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che viene restituito a Visual Studio.

7. Visual Studio chiama [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) per ottenere il valore dell'espressione che viene quindi visualizzata nell'elenco di controllo.

## <a name="parse-then-evaluate"></a>Analizzare quindi valutare
 Poiché l'analisi di un'espressione complessa può richiedere molto più tempo rispetto alla valutazione di un'espressione, il processo di valutazione di un'espressione viene suddiviso in due passaggi: 1) analizzare l'espressione e 2) valutare l'espressione analizzata. In questo modo, la valutazione può verificarsi più volte, ma l'espressione deve essere analizzata una sola volta. L'espressione analizzata intermedia viene restituita da EE in un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) oggetto che a sua volta è incapsulato e restituito dal DE come un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto. L'oggetto `IDebugExpression` rinvia tutta `IDebugParsedExpression` la valutazione all'oggetto.

> [!NOTE]
> Non è necessario che un EE aderisca a questo processo in due passaggi anche se Visual Studio presuppone questo; L'analizzatore di informazioni può analizzare e valutare nello stesso passaggio quando [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) viene chiamato (ad esempio, è il funzionamento dell'esempio MyCEE). Se il linguaggio può formare espressioni complesse, è possibile separare il passaggio di analisi dal passaggio di valutazione. Ciò può migliorare le prestazioni nel debugger di Visual Studio quando vengono visualizzate molte espressioni di controllo.

## <a name="in-this-section"></a>Contenuto della sezione
 [Esempio di implementazione della valutazione dell'espressione](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) Utilizza l'esempio MyCEE per eseguire il processo di valutazione dell'espressione.

 [Valutazione di un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md) Viene illustrato cosa accade dopo un'analisi dell'espressione riuscita.

## <a name="related-sections"></a>Sezioni correlate
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md) Fornisce gli argomenti che vengono passati quando il motore di debug (DE) chiama l'analizzatore di espressioni (EE).

## <a name="see-also"></a>Vedere anche
 [Scrittura di un analizzatore di espressioni CLRWriting a CLR expression evaluator](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
