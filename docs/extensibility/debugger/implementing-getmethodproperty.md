---
title: Implementazione di GetMethodProperty | Microsoft Docs
description: Informazioni su Visual Studio ottenere informazioni sul metodo corrente nel stack frame usando GetDebugProperty del motore di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 17f846e9dcb70300b27aa7248c4c4c2783b02887f6ba9d6071f636cbf48b78b0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121361106"
---
# <a name="implement-getmethodproperty"></a>Implementare GetMethodProperty
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio chiama [getDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)(DE) del motore di debug, che a sua volta chiama [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) per ottenere informazioni sul metodo corrente nell'stack frame.

Questa implementazione `IDebugExpressionEvaluator::GetMethodProperty` di esegue le attività seguenti:

1. Chiama [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), passando [l'oggetto IDebugAddress.](../../extensibility/debugger/reference/idebugaddress.md) Il provider di simboli (SP) restituisce [un oggetto IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) che rappresenta il metodo che contiene l'indirizzo specificato.

2. Ottiene [L'oggetto IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) da `IDebugContainerField` .

3. Crea un'istanza di una classe (chiamata in questo esempio) che `CFieldProperty` implementa l'interfaccia [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) e contiene l'oggetto `IDebugMethodField` restituito da SP.

4. Restituisce `IDebugProperty2` l'interfaccia `CFieldProperty` dall'oggetto .

## <a name="managed-code"></a>Codice gestito
In questo esempio viene illustrata `IDebugExpressionEvaluator::GetMethodProperty` un'implementazione di nel codice gestito.

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        public HRESULT GetMethodProperty(
                IDebugSymbolProvider symbolProvider,
                IDebugAddress        address,
                IDebugBinder         binder,
                int                  includeHiddenLocals,
            out IDebugProperty2      property)
        {
            IDebugContainerField containerField = null;
            IDebugMethodField methodField       = null;
            property = null;

            // Get the containing method field.
            symbolProvider.GetContainerField(address, out containerField);
            methodField = (IDebugMethodField) containerField;

            // Return the property of method field.
            property = new CFieldProperty(symbolProvider, address, binder, methodField);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Codice non gestito
In questo esempio viene illustrata `IDebugExpressionEvaluator::GetMethodProperty` un'implementazione di nel codice non gestito.

```
[CPP]
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(
        in IDebugSymbolProvider *pprovider,
        in IDebugAddress        *paddress,
        in IDebugBinder         *pbinder,
        in BOOL                  includeHiddenLocals,
        out IDebugProperty2    **ppproperty
    )
{
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    IDebugContainerField* pcontainer = NULL;

    hr = pprovider->GetContainerField(paddress, &pcontainer);
    if (FAILED(hr))
        return hr;

    IDebugMethodField*    pmethod    = NULL;
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,
            reinterpret_cast<void**>(&pmethod));
    pcontainer->Release();
    if (FAILED(hr))
        return hr;

    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,
                                                         paddress,
                                                         pbinder,
                                                         pmethod );
    pmethod->Release();
    if (!pfieldProperty)
        return E_OUTOFMEMORY;

    hr = pfieldProperty->Init();
    if (FAILED(hr))
    {
        pfieldProperty->Release();
        return hr;
    }

    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,
            reinterpret_cast<void**>(ppproperty));
    pfieldProperty->Release();

    return hr;
}
```

## <a name="see-also"></a>Vedi anche
- [Implementazione di esempio di variabili locali](../../extensibility/debugger/sample-implementation-of-locals.md)
