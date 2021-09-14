---
title: Valutazione di un'espressione della finestra Espressioni di controllo | Microsoft Docs
description: Informazioni su Visual Studio chiama il motore di debug per determinare il valore corrente di ogni espressione nell'elenco di controllo quando l'esecuzione viene sospesa.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: fbd9ad916b034158f21f909d9895629db74e0718
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627648"
---
# <a name="evaluate-a-watch-window-expression"></a>Valutare un'espressione della finestra Espressioni di controllo
> [!IMPORTANT]
> In Visual Studio 2015 questa modalità di implementazione degli analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Quando l'esecuzione viene sospesa, Visual Studio chiama il motore di debug per determinare il valore corrente di ogni espressione nell'elenco di controllo. De valuta ogni espressione usando un analizzatore di espressioni (edizione Enterprise) e Visual Studio il relativo valore nella **finestra Espressioni di** controllo.

 Di seguito è riportata una panoramica della modalità di valutazione di un'espressione di elenco di controllo:

1. Visual Studio chiama [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) di DE per ottenere un contesto di espressione che può essere usato per valutare le espressioni.

2. Per ogni espressione nell'elenco di controllo, Visual Studio [chiama ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per convertire il testo dell'espressione in un'espressione analizzata.

3. `IDebugExpressionContext2::ParseText`chiama [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per eseguire le operazioni effettive di analisi del testo e produrre un [oggetto IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

4. `IDebugExpressionContext2::ParseText` crea un [oggetto IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e vi `IDebugParsedExpression` inserisce l'oggetto. Questo oggetto I `DebugExpression2` viene quindi restituito Visual Studio.

5. Visual Studio chiama [EvaluateSync per](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) valutare l'espressione analizzata.

6. `IDebugExpression2::EvaluateSync`passa la chiamata a [EvaluateSync per](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) eseguire la valutazione effettiva e produrre un oggetto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) restituito a Visual Studio.

7. Visual Studio chiama [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) per ottenere il valore dell'espressione che viene quindi visualizzata nell'elenco di controllo.

## <a name="parse-then-evaluate"></a>Analizza e quindi valuta
 Poiché l'analisi di un'espressione complessa può richiedere molto più tempo rispetto alla valutazione, il processo di valutazione di un'espressione viene suddiviso in due passaggi: 1) analizzare l'espressione e 2) valutare l'espressione analizzata. In questo modo, la valutazione può verificarsi più volte, ma l'espressione deve essere analizzata una sola volta. L'espressione analizzata intermedia viene restituita dal edizione Enterprise in un oggetto [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) incapsulato e restituito da DE come oggetto [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md) `IDebugExpression`L'oggetto rinvia tutte le valutazioni all'oggetto `IDebugParsedExpression` .

> [!NOTE]
> Non è necessario che un edizione Enterprise aderisca a questo processo in due passaggi anche se Visual Studio presuppone questo; Il edizione Enterprise può analizzare e valutare nello stesso passaggio quando viene chiamato [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (ad esempio, il funzionamento dell'esempio MyCEE). Se il linguaggio può formare espressioni complesse, è possibile separare il passaggio di analisi dal passaggio di valutazione. Ciò può migliorare le prestazioni nel debugger Visual Studio quando vengono visualizzate molte espressioni di controllo.

## <a name="in-this-section"></a>Contenuto della sezione
 [Implementazione di esempio della valutazione delle espressioni](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) Usa l'esempio MyCEE per eseguire il processo di valutazione delle espressioni.

 [Valutazione di un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md) Spiega cosa accade dopo un'analisi dell'espressione riuscita.

## <a name="related-sections"></a>Sezioni correlate
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md) Fornisce gli argomenti passati quando il motore di debug chiama l'analizzatore di espressioni (edizione Enterprise).

## <a name="see-also"></a>Vedi anche
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
