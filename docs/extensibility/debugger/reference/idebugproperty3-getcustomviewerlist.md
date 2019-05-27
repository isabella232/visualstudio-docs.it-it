---
title: IDebugProperty3::GetCustomViewerList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78060933846d60d1e8721cda676ac837ea2bff06
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200189"
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
Ottiene un elenco di visualizzatori personalizzati associati a questa proprietà.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCustomViewerList(
    ULONG                celtSkip,
    ULONG                celtRequested,
    DEBUG_CUSTOM_VIEWER* rgViewers,
    ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
    uint                  celtSkip,
    uint                  celtRequested,
    DEBUG_CUSTOM_VIEWER[] rgViewers,
    out uint              pceltFetched
);
```

## <a name="parameters"></a>Parametri
`celtSkip`\
[in] Il numero di visualizzatori di ignorare.

`celtRequested`\
[in] Il numero di visualizzatori da recuperare (specifica anche la dimensione del `rgViewers` matrice).

`rgViewers`\
[in, out] Matrice di [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) strutture da compilare.

`pceltFetched`\
[out] Il numero effettivo di visualizzatori restituito.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
Per supportare i visualizzatori di tipo, questo metodo inoltra la chiamata per il [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) (metodo). Se l'analizzatore di espressioni supporta anche i visualizzatori personalizzati per questo tipo di proprietà, questo metodo può aggiungere i visualizzatori personalizzati appropriati all'elenco.

Visualizzare [Visualizzatore di tipi e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) per informazioni dettagliate sulle differenze tra i visualizzatori di tipi e visualizzatori personalizzati.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un **CProperty** oggetto che espone le [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia.

```cpp
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
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
