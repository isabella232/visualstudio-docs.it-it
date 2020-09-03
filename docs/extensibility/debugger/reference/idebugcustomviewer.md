---
title: IDebugCustomViewer | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732425"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Questa interfaccia consente a un analizzatore di espressioni (EE) di visualizzare il valore di una proprietà in qualsiasi formato necessario.

## <a name="syntax"></a>Sintassi

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
Un EE implementa questa interfaccia per visualizzare il valore di una proprietà in un formato personalizzato.

## <a name="notes-for-callers"></a>Note per i chiamanti
Una chiamata alla funzione COM `CoCreateInstance` Crea un'istanza di questa interfaccia. Il `CLSID` passato a `CoCreateInstance` viene ottenuto dal registro di sistema. Una chiamata a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) ottiene la posizione nel registro di sistema. Vedere la sezione Osservazioni per i dettagli e l'esempio.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Esegue tutte le informazioni necessarie per visualizzare un determinato valore.|

## <a name="remarks"></a>Osservazioni
Questa interfaccia viene utilizzata quando il valore di una proprietà non può essere visualizzato in modo normale, ad esempio con una tabella di dati o un altro tipo di proprietà complessa. Un visualizzatore personalizzato, come rappresentato dall' `IDebugCustomViewer` interfaccia, è diverso da un visualizzatore di tipi, ovvero un programma esterno per la visualizzazione di dati di un tipo specifico indipendentemente dall'EE. EE implementa un visualizzatore personalizzato specifico di EE. Un utente seleziona il tipo di visualizzatore da usare, ovvero un visualizzatore di tipi o un visualizzatore personalizzato. Per informazioni dettagliate su questo processo, vedere [visualizzazione e visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

Un visualizzatore personalizzato viene registrato allo stesso modo di EE e, pertanto, richiede un GUID del linguaggio e un GUID del fornitore. La metrica esatta (o il nome della voce del registro di sistema) è nota solo al EE. Questa metrica viene restituita nella struttura di [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) , che a sua volta viene restituita da una chiamata a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Il valore archiviato nella metrica è l'oggetto `CLSID` che viene passato alla funzione com `CoCreateInstance` (vedere l'esempio).

Gli [Helper SDK per](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) la funzione di debug, `SetEEMetric` , possono essere usati per registrare un visualizzatore personalizzato. Vedere la sezione del registro di sistema "analizzatori di espressioni" di `Debugging SDK Helpers` per le chiavi specifiche del registro di sistema necessarie per un visualizzatore personalizzato. Si noti che per un visualizzatore personalizzato è necessaria una sola metrica, definita dall'implementatore di EE, mentre un analizzatore di espressioni richiede diverse metriche predefinite.

In genere, un visualizzatore personalizzato fornisce una visualizzazione di sola lettura dei dati, perché l'interfaccia [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) fornita a [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) non dispone di metodi per la modifica del valore della proprietà, ad eccezione di una stringa. Per supportare la modifica di blocchi di dati arbitrari, EE implementa un'interfaccia personalizzata nello stesso oggetto che implementa l' `IDebugProperty3` interfaccia. Questa interfaccia personalizzata fornirebbe quindi i metodi necessari per modificare un blocco di dati arbitrario.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Esempio
Questo esempio Mostra come ottenere il primo visualizzatore personalizzato da una proprietà se tale proprietà ha visualizzatori personalizzati.

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
