---
title: Implementazione di esempio della valutazione dell'espressione | Microsoft Docs
description: Informazioni su come Visual Studio chiama ParseText per produrre un oggetto IDebugExpression2 per un'espressione Windows Watch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec7ddd5270fdac3513c3f63673e5a5f3d05464b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960949"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Implementazione di esempio della valutazione dell'espressione
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Per un'espressione della finestra **espressioni di controllo** , Visual Studio chiama [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per produrre un oggetto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . `IDebugExpressionContext2::ParseText` Crea un'istanza di un analizzatore di espressioni (EE) e chiama [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per ottenere un oggetto [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .

 `IDebugExpressionEvaluator::Parse`Esegue le attività seguenti:

1. [Solo C++] Analizza l'espressione per cercare gli errori.

2. Crea un'istanza di una classe (denominata `CParsedExpression` in questo esempio) che esegue l' `IDebugParsedExpression` interfaccia e archivia nella classe l'espressione da analizzare.

3. Restituisce l' `IDebugParsedExpression` interfaccia dell' `CParsedExpression` oggetto.

> [!NOTE]
> Negli esempi che seguono e nell'esempio MyCEE, l'analizzatore di espressioni non separa l'analisi dalla valutazione.

## <a name="managed-code"></a>Codice gestito
 Nel codice seguente viene illustrata un'implementazione di `IDebugExpressionEvaluator::Parse` nel codice gestito. Questa versione del metodo rinvia l'analisi a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) poiché anche il codice per l'analisi restituisce contemporaneamente (vedere [valutare un'espressione Watch](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Codice non gestito
Il codice seguente è un'implementazione di `IDebugExpressionEvaluator::Parse` nel codice non gestito. Questo metodo chiama una funzione helper, `Parse` , per analizzare l'espressione e verificare la presenza di errori, ma questo metodo ignora il valore risultante. La valutazione formale viene rinviata a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , in cui l'espressione viene analizzata mentre viene valutata (vedere [valutare un'espressione Watch](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>Vedi anche
- [Valutare un'espressione finestra Espressioni di controllo](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Valutare un'espressione Watch](../../extensibility/debugger/evaluating-a-watch-expression.md)
