---
title: Esempio di implementazione della valutazione delle espressioni | Microsoft Docs
description: Informazioni su Visual Studio parsetext per produrre un oggetto IDebugExpression2 per un'espressione di espressioni di controllo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de0e052fd42f1603889f7521a1e45e50b0f36eea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902306"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Implementazione di esempio della valutazione delle espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Per **un'espressione della** finestra Espressione di controllo, Visual Studio [chiama ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per produrre un [oggetto IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md) `IDebugExpressionContext2::ParseText`Crea un'istanza di un analizzatore di espressioni (EE) e chiama [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per ottenere un [oggetto IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

 Esegue `IDebugExpressionEvaluator::Parse` le attività seguenti:

1. [Solo C++] Analizza l'espressione per cercare gli errori.

2. Crea un'istanza di una classe (chiamata in questo esempio) che esegue l'interfaccia e archivia nella classe `CParsedExpression` `IDebugParsedExpression` l'espressione da analizzare.

3. Restituisce `IDebugParsedExpression` l'interfaccia `CParsedExpression` dall'oggetto .

> [!NOTE]
> Negli esempi che seguono e nell'esempio MyCEE, l'analizzatore di espressioni non separa l'analisi dalla valutazione.

## <a name="managed-code"></a>Codice gestito
 Il codice seguente illustra un'implementazione `IDebugExpressionEvaluator::Parse` di nel codice gestito. Questa versione del metodo rinvia l'analisi a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) perché anche il codice per l'analisi valuta contemporaneamente (vedere Valutare [un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
Il codice seguente è un'implementazione `IDebugExpressionEvaluator::Parse` di nel codice non gestito. Questo metodo chiama una funzione helper, , per analizzare l'espressione e verificare la presenza di errori, ma questo `Parse` metodo ignora il valore risultante. La valutazione formale viene posticipata a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) in cui l'espressione viene analizzata durante la valutazione (vedere [Valutare un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
- [Valutare un'finestra Espressioni di controllo personalizzata](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Valutare un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md)
