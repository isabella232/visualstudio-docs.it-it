---
title: Proprietà IDebugCustomViewer . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c44d2289180ece35725b9258e9d20abeb3a4cac3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732425"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Questa interfaccia consente a un analizzatore di espressioni (EE) di visualizzare il valore di una proprietà in qualsiasi formato sia necessario.

## <a name="syntax"></a>Sintassi

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
Un EE implementa questa interfaccia per visualizzare il valore di una proprietà in un formato personalizzato.

## <a name="notes-for-callers"></a>Note per i chiamanti
Una chiamata alla `CoCreateInstance` funzione COM crea un'istanza di questa interfaccia. `CLSID` L'operazione `CoCreateInstance` passata a viene ottenuta dal Registro di sistema. Una chiamata a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) ottiene il percorso nel Registro di sistema. Vedere Osservazioni per i dettagli e l'esempio.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Questa interfaccia implementa il metodo seguente:This interface implements the following method:

|Metodo|Descrizione|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Esegue tutto il necessario per visualizzare un determinato valore.|

## <a name="remarks"></a>Osservazioni
Questa interfaccia viene utilizzata quando il valore di una proprietà non può essere visualizzato con mezzi normali, ad esempio con una tabella dati o un altro tipo di proprietà complessa. Un visualizzatore personalizzato, `IDebugCustomViewer` rappresentato dall'interfaccia, è diverso da un visualizzatore di tipo, ovvero un programma esterno per la visualizzazione di dati di un tipo specifico indipendentemente dall'EE. EE implementa un visualizzatore personalizzato specifico di tale EE. Un utente seleziona il tipo di visualizzatore da utilizzare, sia esso un visualizzatore di tipo o un visualizzatore personalizzato. Per informazioni dettagliate su questo processo, vedere [Visualizzazione e visualizzazione dei dati.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

Un visualizzatore personalizzato viene registrato nello stesso modo di un EE e, pertanto, richiede un GUID di lingua e un GUID del fornitore. La metrica esatta (o il nome della voce del Registro di sistema) è nota solo all'EE. Questa metrica viene restituita nel [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) struttura, che a sua volta viene restituita da una chiamata a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Il valore archiviato nella `CLSID` metrica è quello `CoCreateInstance` che viene passato alla funzione di COM (vedere l'esempio).

Gli helper SDK per `SetEEMetric`la funzione debugging, , possono essere [utilizzati](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) per registrare un visualizzatore personalizzato. Vedere la sezione del Registro `Debugging SDK Helpers` di sistema "Analizzatori di espressioni" di per le chiavi del Registro di sistema specifiche necessarie per un visualizzatore personalizzato. Si noti che un visualizzatore personalizzato richiede una sola metrica (definita dall'implementatore di EE) mentre un analizzatore di espressioni richiede diverse metriche predefinite.

In genere, un visualizzatore personalizzato fornisce una visualizzazione di sola lettura dei dati, poiché il [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia fornita a [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) non dispone di metodi per modificare il valore della proprietà tranne come stringa. Per supportare la modifica di blocchi arbitrari di dati, EE implementa `IDebugProperty3` un'interfaccia personalizzata sullo stesso oggetto che implementa l'interfaccia. Questa interfaccia personalizzata fornirebbe quindi i metodi necessari per modificare un blocco arbitrario di dati.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Esempio
In questo esempio viene illustrato come ottenere il primo visualizzatore personalizzato da una proprietà se tale proprietà dispone di visualizzatori personalizzati.

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

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
