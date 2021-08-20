---
description: Questa interfaccia consente a un analizzatore di espressioni (edizione Enterprise) di visualizzare il valore di una proprietà in qualsiasi formato sia necessario.
title: Interfaccia IDebugCustomViewer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: deb9e1e50ee8b63e29a409756bdcc09cb4ecc8e7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111424"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Questa interfaccia consente a un analizzatore di espressioni (edizione Enterprise) di visualizzare il valore di una proprietà in qualsiasi formato sia necessario.

## <a name="syntax"></a>Sintassi

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
Un edizione Enterprise implementa questa interfaccia per visualizzare il valore di una proprietà in un formato personalizzato.

## <a name="notes-for-callers"></a>Note per i chiamanti
Una chiamata alla funzione com `CoCreateInstance` crea un'istanza di questa interfaccia. `CLSID`L'oggetto passato a viene ottenuto dal Registro di `CoCreateInstance` sistema. Una chiamata a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) ottiene il percorso nel Registro di sistema. Per informazioni dettagliate e l'esempio, vedere Note.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Esegue tutte le operazioni necessarie per visualizzare un valore specificato.|

## <a name="remarks"></a>Commenti
Questa interfaccia viene usata quando il valore di una proprietà non può essere visualizzato in modo normale, ad esempio con una tabella di dati o un altro tipo di proprietà complessa. Un visualizzatore personalizzato, rappresentato dall'interfaccia , è diverso da un visualizzatore di tipi, ovvero un programma esterno per la visualizzazione di dati di un tipo specifico indipendentemente dal `IDebugCustomViewer` edizione Enterprise. Il edizione Enterprise implementa un visualizzatore personalizzato specifico per tale edizione Enterprise. Un utente seleziona il tipo di visualizzatore da usare, sia esso un visualizzatore di tipi o un visualizzatore personalizzato. Per [informazioni dettagliate su questo processo,](../../../extensibility/debugger/visualizing-and-viewing-data.md) vedere Visualizzazione e visualizzazione dei dati.

Un visualizzatore personalizzato viene registrato allo stesso modo di un edizione Enterprise e, pertanto, richiede un GUID della lingua e un GUID del fornitore. La metrica esatta (o nome della voce del Registro di sistema) è nota solo al edizione Enterprise. Questa metrica viene restituita [nella struttura DEBUG_CUSTOM_VIEWER,](../../../extensibility/debugger/reference/debug-custom-viewer.md) che a sua volta viene restituita da una chiamata a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Il valore archiviato nella metrica è `CLSID` l'oggetto passato alla funzione di COM `CoCreateInstance` (vedere l'esempio).

Gli [helper SDK per la funzione debug,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , possono essere usati per `SetEEMetric` registrare un visualizzatore personalizzato. Vedere la sezione del Registro di sistema "Analizzatori di espressioni" di per le chiavi del Registro di `Debugging SDK Helpers` sistema specifiche necessarie per un visualizzatore personalizzato. Si noti che un visualizzatore personalizzato necessita di una sola metrica (definita dall'implementatore del edizione Enterprise), mentre un analizzatore di espressioni richiede diverse metriche predefinite.

In genere, un visualizzatore personalizzato fornisce una visualizzazione di sola lettura dei dati, poiché l'interfaccia [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) fornita a [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) non dispone di metodi per modificare il valore della proprietà, ad eccezione di una stringa. Per supportare la modifica di blocchi arbitrari di dati, il edizione Enterprise implementa un'interfaccia personalizzata nello stesso oggetto che implementa `IDebugProperty3` l'interfaccia . Questa interfaccia personalizzata fornisce quindi i metodi necessari per modificare un blocco arbitrario di dati.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Esempio
Questo esempio illustra come ottenere il primo visualizzatore personalizzato da una proprietà se tale proprietà dispone di visualizzatori personalizzati.

```cpp
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)
{
    // This string is typically defined globally.  For this example, it
    // is defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugCustomViewer *pViewer = NULL;
    if (pProperty != NULL) {
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);
        if (pProperty3 != NULL) {
            HRESULT hr;
            ULONG viewerCount = 0;
            hr = pProperty3->GetCustomViewerCount(&viewerCount);
            if (viewerCount > 0) {
                ULONG viewersFetched = 0;
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };
                hr = pProperty3->GetCustomViewerList(0,
                                                     1,
                                                     &viewerInfo,
                                                     &viewersFetched);
                if (viewersFetched == 1) {
                    CLSID clsidViewer = { 0 };
                    CComPtr<IDebugCustomViewer> spCustomViewer;
                    // Get the viewer's CLSID from the registry.
                    ::GetEEMetric(viewerInfo.guidLang,
                                  viewerInfo.guidVendor,
                                  viewerInfo.bstrMetric,
                                  &clsidViewer,
                                  strRegistrationRoot);
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {
                        // Instantiate the custom viewer.
                        spCustomViewer.CoCreateInstance(clsidViewer);
                        if (spCustomViewer != NULL) {
                            pViewer = spCustomViewer.Detach();
                        }
                    }
                }
            }
        }
    }
    return(pViewer);
}
```

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
