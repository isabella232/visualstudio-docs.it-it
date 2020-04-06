---
title: Esempio di implementazione della valutazione dell'espressione Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf994a61ed9283463cd01aa468018f6acce5e209
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713107"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Esempio di implementazione della valutazione dell'espressione
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)di espressioni gestite .

 Per un'espressione della finestra Espressioni di controllo, Visual Studio chiama ParseText per produrre un [oggetto IDebugExpression2.For](../../extensibility/debugger/reference/idebugexpression2.md) a **Watch** window expression, Visual Studio calls [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) to produce an IDebugExpression2 object. `IDebugExpressionContext2::ParseText`crea un'istanza di un analizzatore di espressioni (EE) e chiama [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per ottenere un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) oggetto.

 Esegue `IDebugExpressionEvaluator::Parse` le seguenti attività:

1. [Solo C) Analizza l'espressione per cercare gli errori.

2. Crea una istanza `CParsedExpression` di una classe (chiamata in questo esempio) che esegue l'interfaccia `IDebugParsedExpression` e archivia la classe l'espressione da analizzare.

3. Restituisce `IDebugParsedExpression` l'interfaccia dall'oggetto. `CParsedExpression`

> [!NOTE]
> Negli esempi che seguono e nel campione MyCEE, l'analizzatore di espressioni non separa l'analisi dalla valutazione.

## <a name="managed-code"></a>Codice gestito
 Il codice seguente mostra `IDebugExpressionEvaluator::Parse` un'implementazione di nel codice gestito. Questa versione del metodo rinvia l'analisi a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) poiché anche il codice per l'analisi valuta contemporaneamente (vedere [Valutare un'espressione Watch](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
Il codice seguente è `IDebugExpressionEvaluator::Parse` un'implementazione di nel codice non gestito. Questo metodo chiama una `Parse`funzione di supporto, , per analizzare l'espressione e verificare la presenza di errori, ma questo metodo ignora il valore risultante. La valutazione formale viene rinviata a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) in cui l'espressione viene analizzata durante la valutazione (vedere [Valutare un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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

## <a name="see-also"></a>Vedere anche
- [Valutare un'espressione della finestra Espressioni di controlloEvaluate a Watch window expression](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Valutare un'espressione di controlloEvaluate a Watch expression](../../extensibility/debugger/evaluating-a-watch-expression.md)
