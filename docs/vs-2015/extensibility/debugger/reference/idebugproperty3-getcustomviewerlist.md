---
title: IDebugProperty3::GetCustomViewerList | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d709c9897aa80bdf18f06ae52147198323fcfef7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193394"
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene un elenco di visualizzatori personalizzati associati a questa proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celtSkip`  
 [in] Il numero di visualizzatori di ignorare.  
  
 `celtRequested`  
 [in] Il numero di visualizzatori da recuperare (specifica anche la dimensione del `rgViewers` matrice).  
  
 `rgViewers`  
 [in, out] Matrice di [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) strutture da compilare.  
  
 `pceltFetched`  
 [out] Il numero effettivo di visualizzatori restituito.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Per supportare i visualizzatori di tipo, questo metodo inoltra la chiamata per il [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) (metodo). Se l'analizzatore di espressioni supporta anche i visualizzatori personalizzati per questo tipo di proprietà, questo metodo può aggiungere i visualizzatori personalizzati appropriati all'elenco.  
  
 Visualizzare [Visualizzatore di tipi e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) per informazioni dettagliate sulle differenze tra i visualizzatori di tipi e visualizzatori personalizzati.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CProperty** oggetto che espone le [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia.  
  
```cpp#  
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)  
{  
    if (NULL == prgViewers)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)   
 [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
