---
title: Valutazione di un'espressione della finestra espressioni di controllo | Microsoft Docs
description: Informazioni su come Visual Studio chiama il motore di debug per determinare il valore corrente di ogni espressione nell'elenco di controllo quando l'esecuzione viene sospesa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e72a89a6d3b51a328294d5bfa56e1699ead5498a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097071"
---
# <a name="evaluate-a-watch-window-expression"></a>Valutare un'espressione della finestra espressioni di controllo
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Quando l'esecuzione viene sospesa, Visual Studio chiama il motore di debug (DE) per determinare il valore corrente di ogni espressione nell'elenco di controllo. Il DE valuta ogni espressione usando un analizzatore di espressioni (EE) e Visual Studio ne Visualizza il valore nella finestra **espressioni di controllo** .

 Di seguito viene riportata una panoramica del modo in cui viene valutata un'espressione di elenco di controllo:

1. Visual Studio chiama il [GETEXPRESSIONCONTEXT](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) de di per ottenere un contesto dell'espressione che può essere usato per valutare le espressioni.

2. Per ogni espressione nell'elenco di controllo, Visual Studio chiama [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per convertire il testo dell'espressione in un'espressione analizzata.

3. `IDebugExpressionContext2::ParseText` chiama [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per eseguire il lavoro effettivo di analisi del testo e produrre un oggetto [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .

4. `IDebugExpressionContext2::ParseText` Crea un oggetto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e lo inserisce all' `IDebugParsedExpression` interno dell'oggetto. Questo `DebugExpression2` oggetto I viene quindi restituito a Visual Studio.

5. Visual Studio chiama [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per valutare l'espressione analizzata.

6. `IDebugExpression2::EvaluateSync` passa la chiamata a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) per eseguire la valutazione effettiva e produrre un oggetto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) restituito a Visual Studio.

7. Visual Studio chiama [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) per ottenere il valore dell'espressione che viene quindi visualizzata nell'elenco di controllo.

## <a name="parse-then-evaluate"></a>Analizza quindi valuta
 Poiché l'analisi di un'espressione complessa può richiedere molto più tempo rispetto alla valutazione, il processo di valutazione di un'espressione è suddiviso in due passaggi: 1) analizza l'espressione e 2) valuta l'espressione analizzata. In questo modo, la valutazione può essere eseguita molte volte, ma l'espressione deve essere analizzata una sola volta. L'espressione analizzata intermedia viene restituita da EE in un oggetto [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) che viene a sua volta incapsulato e restituito da de come oggetto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . L' `IDebugExpression` oggetto rinvia tutta la valutazione all' `IDebugParsedExpression` oggetto.

> [!NOTE]
> Non è necessario che un EE rispetti questo processo in due passaggi anche se Visual Studio presuppone questo problema; EE può analizzare e valutare nello stesso passaggio quando viene chiamato [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (ad esempio, l'esempio MyCEE funziona). Se il linguaggio può formare espressioni complesse, è consigliabile separare il passaggio di analisi dal passaggio di valutazione. Questo può migliorare le prestazioni nel debugger di Visual Studio quando vengono visualizzate molte espressioni di controllo.

## <a name="in-this-section"></a>Contenuto della sezione
 [Implementazione di esempio della valutazione dell'espressione](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) Usa l'esempio MyCEE per eseguire il processo di valutazione dell'espressione.

 [Valutazione di un'espressione Watch](../../extensibility/debugger/evaluating-a-watch-expression.md) Viene illustrato cosa accade dopo un'analisi dell'espressione riuscita.

## <a name="related-sections"></a>Sezioni correlate
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md) Fornisce gli argomenti che vengono passati quando il motore di debug (DE) chiama l'analizzatore di espressioni (EE).

## <a name="see-also"></a>Vedi anche
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
