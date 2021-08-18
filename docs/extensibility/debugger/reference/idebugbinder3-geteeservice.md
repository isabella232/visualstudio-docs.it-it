---
description: Questo metodo restituisce un servizio richiesto.
title: Interfaccia IDebugBinder3::GetEEService | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 539a61fc6e1967b779ad2eccc6349e7fbbe00ee0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104365"
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
[in] `GUID` di un fornitore (un valore Null è accettabile).

`language`\
[in] `GUID` di una lingua (un valore Null è accettabile).

`iid`\
[in] `IID` del servizio da ottenere.

`ppService`\
[out] Interfaccia per il servizio richiesto.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Passare per `IID` [l'interfaccia IEEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) ( ) per `IID_IEEVisualizerServiceProvider` verificare se il servizio visualizzatore di tipi è disponibile. In tal caso, l'analizzatore di espressioni può ottenere [l'interfaccia IEEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) per supportare i visualizzatori di tipi. Per [informazioni dettagliate, vedere Visualizzazione e visualizzazione dei](../../../extensibility/debugger/visualizing-and-viewing-data.md) dati.

## <a name="see-also"></a>Vedi anche
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
