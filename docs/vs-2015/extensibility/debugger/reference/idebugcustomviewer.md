---
title: IDebugCustomViewer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f94fe0301777a615fa6dc567311c493ff55a90a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969183"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia consente a un analizzatore di espressioni (EE) per visualizzare un valore della proprietà in qualsiasi formato è necessario.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un EE implementa questa interfaccia per visualizzare un valore della proprietà in un formato personalizzato.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a COM `CoCreateInstance` funzione crea un'istanza di questa interfaccia. Il `CLSID` passato a `CoCreateInstance` viene ottenuto dal Registro di sistema. Una chiamata a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Ottiene il percorso del Registro di sistema. Per informazioni dettagliate, così come nell'esempio, vedere la sezione Osservazioni.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Esegue tutte le operazioni necessarie per visualizzare un determinato valore.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene utilizzata quando un valore della proprietà non può essere visualizzato in modo normale, ad esempio, con una tabella di dati o un altro tipo di proprietà complessa. Un visualizzatore personalizzato, come rappresentate dal `IDebugCustomViewer` interfaccia, è diverso da un visualizzatore di tipo, che è un programma esterno per visualizzare i dati di un tipo specifico indipendentemente dal motore di esecuzione. L'analizzatore di Espressioni implementa un visualizzatore personalizzato specifico per tale EE. L'utente seleziona il tipo di Visualizzatore da utilizzare, sia esso un visualizzatore di tipo o un visualizzatore personalizzato. Visualizzare [visualizzazione di dati e visualizzare](../../../extensibility/debugger/visualizing-and-viewing-data.md) per informazioni dettagliate su questo processo.  
  
 Un visualizzatore personalizzato registrato nello stesso modo come un EE e, pertanto, è necessario un GUID del linguaggio e un fornitore di GUID. La metrica esatta (o nome della voce del Registro di sistema) è noto solo al motore di esecuzione. Questa metrica viene restituita nel [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) struttura, che a sua volta, viene restituito da una chiamata a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Il valore archiviato nella metrica è la `CLSID` passato a COM `CoCreateInstance` funzione (vedere l'esempio).  
  
 Il [helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) funzione `SetEEMetric`, può essere utilizzato per registrare un visualizzatore personalizzato. Vedere la sezione del Registro di sistema "Analizzatori di espressioni" `Debugging SDK Helpers` per il Registro di sistema specifico tasti che è necessario un visualizzatore personalizzato. Si noti che un visualizzatore personalizzato deve solo una metrica (che viene definita dal responsabile dell'implementazione del motore di esecuzione), mentre un analizzatore di espressioni per diverse metriche predefinite.  
  
 In genere, un visualizzatore personalizzato offre una visualizzazione di sola lettura dei dati, poiché il [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia forniti al [disponibili DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) dispone di alcun metodo per modificare il valore della proprietà tranne sotto forma di stringa. Per supportare la modifica arbitrari blocchi di dati, l'analizzatore di Espressioni implementa un'interfaccia personalizzata sullo stesso oggetto che implementa il `IDebugProperty3` interfaccia. Questa interfaccia personalizzata fornirebbe quindi i metodi necessari per modificare un blocco di dati arbitrario.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come ottenere il primo visualizzatore personalizzato da una proprietà se tale proprietà è qualsiasi visualizzatori personalizzati.  
  
```cpp#  
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
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Helper SDK per eseguire il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
