---
title: Valutazione di un'espressione di controllo Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a239e430338e88a0be4bc35ad1c357925f7d8f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738849"
---
# <a name="evaluate-a-watch-expression"></a>Valutare un'espressione di controlloEvaluate a watch expression
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Quando Visual Studio è pronto per visualizzare il valore di un'espressione di controllo, chiama [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md), che a sua volta chiama [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Questo processo produce un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che contiene il valore e il tipo dell'espressione.

In questa `IDebugParsedExpression::EvaluateSync`implementazione di , l'espressione viene analizzata e valutata contemporaneamente. Questa implementazione esegue le attività seguenti:This implementation performs the following tasks:

1. Analizza e valuta l'espressione per produrre un oggetto generico che contiene il valore e il relativo tipo. Nel linguaggio C, questo `object` è rappresentato come un'estensione `VARIANT`in C, questo viene rappresentato come un oggetto .

2. Crea una istanza `CValueProperty` di una classe (chiamata in questo esempio) che implementa l'interfaccia `IDebugProperty2` e archivia nella classe il valore da restituire.

3. Restituisce `IDebugProperty2` l'interfaccia dall'oggetto. `CValueProperty`

## <a name="managed-code"></a>Codice gestito
Si tratta di `IDebugParsedExpression::EvaluateSync` un'implementazione del codice gestito in. Il metodo `Tokenize` helper analizza l'espressione in un albero di analisi. La funzione `EvalToken` di supporto converte il token in un valore. La funzione `FindTerm` di supporto attraversa in modo ricorsivo l'albero di analisi, chiamando `EvalToken` ogni nodo che rappresenta un valore e applicando qualsiasi operazione (addizione o sottrazione) nell'espressione.

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
Si tratta di `IDebugParsedExpression::EvaluateSync` un'implementazione del codice in codice non gestito. La funzione `Evaluate` di supporto analizza e valuta `VARIANT` l'espressione, restituendo un valore che contiene il valore risultante. La funzione `VariantValueToProperty` di `VARIANT` supporto `CValueProperty` raggruppa l'oggetto in un oggetto.

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

## <a name="see-also"></a>Vedere anche
- [Valutare un'espressione della finestra Espressioni di controlloEvaluate a watch window expression](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Esempio di implementazione della valutazione dell'espressione](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
