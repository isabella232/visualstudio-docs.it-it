---
description: Questo metodo restituisce un elenco di visualizzatori di tipo noti a questo servizio.
title: Interfaccia IEEVisualizerService::GetCustomViewerList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42a42c36eef04f1e858f2025703a74501e3c785a0bb5f2e17cd3b4e891ecf793
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401895"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Questo metodo restituisce un elenco di visualizzatori di tipo noti a questo servizio.

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

`celRequested`\
[in] Numero di visualizzatori da recuperare (specifica anche le dimensioni della `rgViewers` matrice).

`rgViewers`\
[in, out] Matrice di [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) da riempire.

`pceltFetched`\
[out] Numero di visualizzatori effettivamente recuperati.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) passa la richiesta a questo metodo come parte del supporto per i visualizzatori di tipi. Se l'analizzatore di espressioni fornisce anche visualizzatori personalizzati per lo stesso [](../../../extensibility/debugger/reference/debug-custom-viewer.md) tipo, può aggiungere all'elenco strutture DEBUG_CUSTOM_VIEWER compilate in modo appropriato per tali visualizzatori personalizzati. Assicurarsi che [GetCustomViewerCount rifletta](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) gli altri visualizzatori.

 Per [informazioni dettagliate sulle differenze tra visualizzatori e visualizzatori,](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) vedere Visualizzatore di tipi e Visualizzatore personalizzato.

## <a name="see-also"></a>Vedi anche
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
