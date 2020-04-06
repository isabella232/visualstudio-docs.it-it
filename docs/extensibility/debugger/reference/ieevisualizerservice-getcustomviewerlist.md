---
title: Proprietà IEEVisualizerService::GetCustomViewerList . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f3808ad6fb511270ee3825601c476f10a8b77124
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718011"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Questo metodo restituisce un elenco di visualizzatori di tipo che questo servizio conosce.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCustomViewerList(
   ULONG                celtSkip,
   ULONG                celtRequested,
   DEBUG_CUSTOM_VIEWER* rgViewers,
   ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
   uint                  celtSkip,
   uint                  celtRequested,
   DEBUG_CUSTOM_VIEWER[] rgViewers,
   out uint              pceltFetched
);
```

## <a name="parameters"></a>Parametri
`celtSkip`\
[in] Numero di visualizzatori da ignorare.

`celRequested`\
[in] Numero di visualizzatori da recuperare (specifica `rgViewers` anche le dimensioni della matrice).

`rgViewers`\
[in, out] Matrice di [strutture DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) da compilare.

`pceltFetched`\
[fuori] Numero di visualizzatori effettivamente recuperati.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) passa la richiesta a questo metodo come parte del relativo supporto per i visualizzatori di tipo. Se l'analizzatore di espressioni fornisce anche visualizzatori personalizzati per lo stesso tipo, può aggiungere all'elenco strutture [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) compilate in modo appropriato per tali visualizzatori personalizzati. Assicurarsi che [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) rifletta tali visualizzatori aggiuntivi.

 Per informazioni dettagliate sulle differenze tra visualizzatori e visualizzatori, vedere Visualizzatore di [tipi e Visualizzatore personalizzato.](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

## <a name="see-also"></a>Vedere anche
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
