---
description: Questo metodo restituisce un servizio richiesto.
title: 'IDebugBinder3:: GetEEService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ccc4d28a06d87d7c17d16470e10f259657083cc9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094302"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Questo metodo restituisce un servizio richiesto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>Parametri
`vendor`\
[in] `GUID` di un fornitore (un valore null è accettabile).

`language`\
[in] `GUID` di un linguaggio (un valore null è accettabile).

`iid`\
[in] `IID` del servizio da ottenere.

`ppService`\
out Interfaccia per il servizio richiesto.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Passare l'oggetto `IID` per l'interfaccia [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) ( `IID_IEEVisualizerServiceProvider` ) per verificare se il servizio del Visualizzatore di tipi è disponibile. In tal caso, l'analizzatore di espressioni può ottenere l'interfaccia [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) per supportare i visualizzatori di tipi. Per informazioni dettagliate, vedere [visualizzazione e visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
