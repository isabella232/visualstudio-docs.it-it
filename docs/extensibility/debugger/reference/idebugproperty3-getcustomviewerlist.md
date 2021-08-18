---
description: Ottiene un elenco di visualizzatori personalizzati associati a questa proprietà.
title: IDebugProperty3::GetCustomViewerList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9f8abc55fe52c48c20979f509bf626e1be697bb5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063902"
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
[in] Numero di visualizzatori da ignorare.

`celtRequested`\
[in] Numero di visualizzatori da recuperare (specifica anche le dimensioni della `rgViewers` matrice).

`rgViewers`\
[in, out] Matrice di [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) da riempite.

`pceltFetched`\
[out] Numero effettivo di visualizzatori restituiti.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
Per supportare i visualizzatori di tipi, questo metodo inoltra la chiamata al [metodo GetCustomViewerList.](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) Se l'analizzatore di espressioni supporta anche visualizzatori personalizzati per il tipo di questa proprietà, questo metodo può aggiungere i visualizzatori personalizzati appropriati all'elenco.

Per [informazioni dettagliate sulle](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) differenze tra visualizzatori di tipi e visualizzatori personalizzati, vedere Visualizzatore di tipi e Visualizzatore personalizzato.

## <a name="example"></a>Esempio
L'esempio seguente illustra come implementare questo metodo per un **oggetto CProperty** che espone [l'interfaccia IDebugProperty3.](../../../extensibility/debugger/reference/idebugproperty3.md)

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

## <a name="see-also"></a>Vedi anche
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
