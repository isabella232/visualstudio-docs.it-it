---
title: Recupero delle proprietà locali | Microsoft Docs
description: Informazioni su Visual Studio usa EnumChildren per ottenere proprietà locali con questi esempi per codice gestito e non gestito.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: cd174da02a52a86a29494f4edeaf13714b2d5758
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057863"
---
# <a name="get-local-properties"></a>Ottenere le proprietà locali
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio chiama [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) per ottenere un [oggetto IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) che fornisce l'accesso a tutte le variabili locali da visualizzare nella **finestra** Variabili locali. Visual Studio quindi chiama [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) per ottenere le informazioni da visualizzare per ogni locale. In questo esempio la classe `CEnumPropertyInfo` implementa `IEnumDebugPropertyInfo2` l'interfaccia .

Questa implementazione `IEnumDebugPropertyInfo2::Next` di esegue le attività seguenti:

1. Cancella la matrice in cui archiviare le informazioni.

2. Chiama [Next](../../extensibility/debugger/reference/ienumdebugfields-next.md) per ogni variabile locale, archiviando il [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) restituito nella matrice da restituire. [L'oggetto IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) è stato fornito quando è stata creata un'istanza `CEnumPropertyInfo` di questa classe.

## <a name="managed-code"></a>Codice gestito
In questo esempio viene illustrata un'implementazione di per le variabili locali di `IEnumDebugPropertyInfo2::EnumChildren` un metodo nel codice gestito.

```csharp
namespace EEMC
{
    public class CEnumMethodField : IEnumDebugFields
    {
        public HRESULT Next(
                uint                  count,
                DEBUG_PROPERTY_INFO[] properties,
            out uint                  fetched)
        {
            if (count > properties.Length)
                throw new COMException();

            // Zero out the array.
            for (int i= 0; i < count; i++)
            {
                properties[i].bstrFullName = "";
                properties[i].bstrName = "";
                properties[i].bstrType = "";
                properties[i].bstrValue = "";
                properties[i].dwAttrib = 0;
                properties[i].dwFields = 0;
                properties[i].pProperty = null;
            }
            fetched = 0;

            // COM interop.
            HRESULT hr;
            uint innerFetched;
            IDebugField[] field = new IDebugField[1];

            while (fetched < count)
            {
                field[0] = null;
                innerFetched = 0;

                // Get next field.
                if (fetched < fieldCount)
                    hr = fields.Next(1, field, ref innerFetched);
                // No more fields.
                else return COM.S_FALSE;

                if (hr != COM.S_OK || innerFetched != 1 || field[0] == null)
                    throw new COMException("CEnumPropertyInfo.Next");

                // Get property from field.
                CFieldProperty fieldProperty =
                        new CFieldProperty(provider, address, binder, field[0]);

                DEBUG_PROPERTY_INFO[] property =
                        new DEBUG_PROPERTY_INFO[1];
                fieldProperty.GetPropertyInfo((uint) infoFlags, radix, 0, null, 0, property);
                properties[fetched++] = property[0];
            }
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Codice non gestito
 In questo esempio viene illustrata un'implementazione di per le variabili locali di un `IEnumDebugPropertyInfo2::EnumChildren` metodo nel codice non gestito.

```cpp
STDMETHODIMP CEnumPropertyInfo::Next(
    in  ULONG                count,
    out DEBUG_PROPERTY_INFO* pelements,
    out ULONG*               pfetched )
{
    if (pfetched)
        *pfetched = 0;
    if (!pelements)
        return E_INVALIDARG;
    else
        memset( pelements, 0, count * sizeof(DEBUG_PROPERTY_INFO));

    HRESULT hr  = S_OK;
    ULONG   idx = 0;
    while (idx < count)
    {
        ULONG        fetchedFields;
        IDebugField* pfield;

        //get the next field
        hr = m_fields->Next( 1, &pfield, &fetchedFields );
        if (FAILED(hr))
            return hr;
        if (fetchedFields != 1)
            return E_FAIL;
        idx++;

        //create a CFieldProperty to retrieve the DEBUG_PROPERTY_INFO
        CFieldProperty* pproperty =
            new CFieldProperty( m_provider, m_address, m_binder, pfield );
        pfield->Release();
        if (!pproperty)
            return E_OUTOFMEMORY;

        hr = pproperty->Init();
        if (FAILED(hr))
        {
            pproperty->Release();
            return hr;
        }

        hr = pproperty->GetPropertyInfo( m_infoFlags,
                                         m_radix,
                                         0,
                                         NULL,
                                         0,
                                         pelements + idx - 1);
        pproperty->Release();
        if (FAILED(hr))
            return hr;
    }

    if (pfetched)
        *pfetched = idx;
    return hr;
}
```

## <a name="see-also"></a>Vedi anche
- [Implementazione di esempio di variabili locali](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Enumerazione delle variabili locali](../../extensibility/debugger/enumerating-locals.md)
