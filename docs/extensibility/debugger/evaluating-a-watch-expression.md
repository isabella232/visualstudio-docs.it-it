---
title: Valutazione di un'espressione Watch | Microsoft Docs
description: Informazioni su come Visual Studio USA EvaluateSync quando è pronto per visualizzare il valore di un'espressione Watch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 21a173a8c041bbaf12cb67bf90e1c4407ac5e4a7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097058"
---
# <a name="evaluate-a-watch-expression"></a>Valutare un'espressione Watch
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Quando Visual Studio è pronto per visualizzare il valore di un'espressione Watch, chiama [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md), che a sua volta chiama [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Questo processo produce un oggetto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che contiene il valore e il tipo dell'espressione.

In questa implementazione di `IDebugParsedExpression::EvaluateSync` , l'espressione viene analizzata e valutata allo stesso tempo. Questa implementazione esegue le attività seguenti:

1. Analizza e valuta l'espressione per produrre un oggetto generico che include il valore e il relativo tipo. In C#, questo è rappresentato come un `object` while in C++, questo viene rappresentato come `VARIANT` .

2. Crea un'istanza di una classe (denominata `CValueProperty` in questo esempio) che implementa l' `IDebugProperty2` interfaccia e archivia nella classe il valore da restituire.

3. Restituisce l' `IDebugProperty2` interfaccia dell' `CValueProperty` oggetto.

## <a name="managed-code"></a>Codice gestito
Si tratta di un'implementazione di `IDebugParsedExpression::EvaluateSync` nel codice gestito. Il metodo helper `Tokenize` analizza l'espressione in un albero di analisi. La funzione helper `EvalToken` converte il token in un valore. La funzione di supporto `FindTerm` attraversa in modo ricorsivo l'albero di analisi, chiamando `EvalToken` per ogni nodo che rappresenta un valore e applicando qualsiasi operazione (addizione o sottrazione) nell'espressione.

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT EvaluateSync(
            uint evalFlags,
            uint timeout,
            IDebugSymbolProvider provider,
            IDebugAddress address,
            IDebugBinder binder,
            string resultType,
            out IDebugProperty2 result)
        {
            HRESULT retval = COM.S_OK;
            this.evalFlags = evalFlags;
            this.timeout = timeout;
            this.provider = provider;
            this.address = address;
            this.binder = binder;
            this.resultType = resultType;

            try
            {
                IDebugField field = null;
                // Tokenize, then parse.
                tokens = Tokenize(expression);
                result = new CValueProperty(
                        expression,
                        (int) FindTerm(EvalToken(tokens[0], out field),1),
                        field,
                        binder);
            }
            catch (ParseException)
            {
                result = new CValueProperty(expression, "Huh?");
                retval = COM.E_INVALIDARG;
            }
            return retval;
        }
    }
}
```

## <a name="unmanaged-code"></a>Codice non gestito
Si tratta di un'implementazione di `IDebugParsedExpression::EvaluateSync` nel codice non gestito. La funzione helper `Evaluate` analizza e valuta l'espressione, restituendo un oggetto che `VARIANT` contiene il valore risultante. La funzione helper consente di `VariantValueToProperty` raggruppare `VARIANT` in un `CValueProperty` oggetto.

```cpp
STDMETHODIMP CParsedExpression::EvaluateSync(
    in  DWORD                 evalFlags,
    in  DWORD                 dwTimeout,
    in  IDebugSymbolProvider* pprovider,
    in  IDebugAddress*        paddress,
    in  IDebugBinder*         pbinder,
    in  BSTR                  bstrResultType,
    out IDebugProperty2**     ppproperty )
{
    // dwTimeout parameter is ignored in this implementation.
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (paddress == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    VARIANT value;
    BSTR    bstrErrorMessage = NULL;
    hr = ::Evaluate( pprovider,
                     paddress,
                     pbinder,
                     m_expr,
                     &bstrErrorMessage,
                     &value );
    if (hr != S_OK)
    {
        if (bstrErrorMessage == NULL)
            return hr;

        //we can display better messages ourselves.
        HRESULT hrLocal = S_OK;
        VARIANT varType;
        VARIANT varErrorMessage;

        VariantInit( &varType );
        VariantInit( &varErrorMessage );
        varErrorMessage.vt      = VT_BSTR;
        varErrorMessage.bstrVal = bstrErrorMessage;

        CValueProperty* valueProperty = new CValueProperty();
        if (valueProperty != NULL)
        {
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);
            if (SUCCEEDED(hrLocal))
            {
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,
                        reinterpret_cast<void**>(ppproperty) );
            }
        }

        VariantClear(&varType);
        VariantClear(&varErrorMessage); //frees BSTR
        if (!valueProperty)
            return hr;
        valueProperty->Release();
        if (FAILED(hrLocal))
            return hr;
    }
    else
    {
        if (bstrErrorMessage != NULL)
            SysFreeString(bstrErrorMessage);

        hr = VariantValueToProperty( pprovider,
                                     paddress,
                                     pbinder,
                                     m_radix,
                                     m_expr,
                                     value,
                                     ppproperty );
        VariantClear(&value);
        if (FAILED(hr))
            return hr;
    }

    return S_OK;
}
```

## <a name="see-also"></a>Vedi anche
- [Valutare un'espressione della finestra espressioni di controllo](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Implementazione di esempio della valutazione dell'espressione](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
