---
description: Questa interfaccia rappresenta l'analizzatore di espressioni.
title: Interfaccia IDebugExpressionEvaluator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 41128445dca38d6d735d3dd4f83b84363bcb4989
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138679"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [Clr Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Questa interfaccia rappresenta l'analizzatore di espressioni.

## <a name="syntax"></a>Sintassi

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
L'analizzatore di espressioni deve implementare questa interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
Per ottenere questa interfaccia, creare un'istanza dell'analizzatore di espressioni tramite il metodo usando `CoCreateInstance` l'ID di classe (CLSID) dell'analizzatore. Vedere l'esempio.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Nella tabella seguente vengono illustrati i metodi di `IDebugExpressionEvaluator` .

|Metodo|Descrizione|
|------------|-----------------|
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md).|Converte una stringa di espressione in un'espressione analizzata.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Ottiene le variabili locali, gli argomenti e altre proprietà di un metodo.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Converte la posizione e l'offset di un metodo in un indirizzo di memoria.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Determina la lingua da usare per creare risultati stampabili.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Imposta la radice del Registro di sistema. Usato per il debug side-by-side.|

## <a name="remarks"></a>Commenti
In una situazione tipica, il motore di debug (DE) crea un'istanza dell'analizzatore di espressioni (edizione Enterprise) come risultato di una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Poiché il de conosce il linguaggio e il fornitore del edizione Enterprise che vuole usare, il de ottiene il CLSID del edizione Enterprise dal Registro di sistema (la funzione [HELPER SDK](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) per il debug, , consente il `GetEEMetric` recupero).

Dopo la edizione Enterprise viene creata un'istanza di , la funzione DE chiama [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per analizzare l'espressione e archiviarla in un [oggetto IDebugParsedExpression.](../../../extensibility/debugger/reference/idebugparsedexpression.md) Successivamente, una chiamata a [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) valuta l'espressione.

## <a name="requirements"></a>Requisiti
Intestazione: ee.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Esempio
Questo esempio illustra come creare un'istanza dell'analizzatore di espressioni in base a un provider di simboli e a un indirizzo nel codice sorgente. In questo esempio viene utilizzata una funzione `GetEEMetric` , dalla libreria sdk [Helpers for Debugging,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) dbgmetric.lib.

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

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
