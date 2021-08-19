---
description: Ottiene il numero di visualizzatori personalizzati che potrebbero essere disponibili per questa proprietà.
title: IDebugProperty3::GetCustomViewerCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9482b1f2fcf594de5f9ba33b902e35eda6010168
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063941"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Ottiene il numero di visualizzatori personalizzati che potrebbero essere disponibili per questa proprietà.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCustomViewerCount(
    ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
    out uint pcelt
);
```

## <a name="parameters"></a>Parametri
`pcelt`\
[out] Numero di visualizzatori personalizzati disponibili per questa proprietà.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
Per supportare i visualizzatori di tipo, questo metodo inoltra la chiamata al [metodo GetCustomViewerCount.](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) Se l'analizzatore di espressioni supporta anche visualizzatori personalizzati per il tipo di questa proprietà, questo metodo aggiunge il numero di visualizzatori personalizzati al valore restituito.

Per informazioni dettagliate sulle differenze tra i visualizzatori di tipi e i visualizzatori personalizzati, vedere [Visualizzatore di tipi e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).

## <a name="example"></a>Esempio
L'esempio seguente illustra come implementare questo metodo per un **oggetto CProperty** che espone [l'interfaccia IDebugProperty3.](../../../extensibility/debugger/reference/idebugproperty3.md)

```cpp
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)
{
    if (pcelt == NULL)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
