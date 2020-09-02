---
title: IDebugExpressionEvaluator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8dd910e4edc110abb40dde14b4cb85ff54a70a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729379"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Questa interfaccia rappresenta l'analizzatore di espressioni.

## <a name="syntax"></a>Sintassi

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
L'analizzatore di espressioni deve implementare questa interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
Per ottenere questa interfaccia, creare un'istanza dell'analizzatore di espressioni tramite il `CoCreateInstance` metodo utilizzando l'ID di classe (CLSID) dell'analizzatore. Vedere l'esempio.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
La tabella seguente illustra i metodi di `IDebugExpressionEvaluator` .

|Metodo|Descrizione|
|------------|-----------------|
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md).|Converte una stringa di espressione in un'espressione analizzata.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Ottiene le variabili locali, gli argomenti e altre proprietà di un metodo.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Converte il percorso e l'offset di un metodo in un indirizzo di memoria.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Determina il linguaggio da utilizzare per creare risultati stampabili.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Imposta la radice del registro di sistema. Usato per il debug side-by-side.|

## <a name="remarks"></a>Osservazioni
In una situazione tipica, il motore di debug (DE) crea un'istanza dell'analizzatore di espressioni (EE) in seguito a una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Poiché conosce la lingua e il fornitore dell'EE che vuole usare, il DE ottiene il CLSID di EE dal registro di sistema (gli [Helper SDK per](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) la funzione di debug, `GetEEMetric` , contribuisce a questo recupero).

Una volta creata un'istanza di EE, il DE chiama [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per analizzare l'espressione e archiviarla in un oggetto [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) . Successivamente, una chiamata a [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) valuta l'espressione.

## <a name="requirements"></a>Requisiti
Intestazione: EE. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Esempio
In questo esempio viene illustrato come creare un'istanza dell'analizzatore di espressioni dato un provider di simboli e un indirizzo nel codice sorgente. In questo esempio viene usata una funzione, `GetEEMetric` , dagli [Helper SDK per la libreria di debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) dbgmetric. lib.

```cpp
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,
                                                 IDebugAddress *pSourceAddress)
{
    // This is typically defined globally but is specified here just
    // for this example.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";

    IDebugExpressionEvaluator *pEE = NULL;
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {
        HRESULT hr         = S_OK;
        GUID  languageGuid = { 0 };
        GUID  vendorGuid   = { 0 };

        hr = pSymbolProvider->GetLanguage(pSourceAddress,
                                          &languageGuid,
                                          &vendorGuid);
        if (SUCCEEDED(hr)) {
            CLSID clsidEE = { 0 };
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;
            // Get the expression evaluator's CLSID from the registry.
            ::GetEEMetric(languageGuid,
                          vendorGuid,
                          metricCLSID,
                          &clsidEE,
                          strRegistrationRoot);
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {
                // Instantiate the expression evaluator.
                spExpressionEvaluator.CoCreateInstance(clsidEE);
            }
            if (spExpressionEvaluator != NULL) {
                pEE = spExpressionEvaluator.Detach();
            }
        }
    }
    return pEE;
}
```

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
