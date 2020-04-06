---
title: Proprietà IDebugBinder3::GetEEService . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c08d7df4a6b05be489f6b9ab06569c085f3b1f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735820"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Questo metodo restituisce un servizio richiesto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>Parametri
`vendor`\
[in] `GUID` di un fornitore (un valore nullo è accettabile).

`language`\
[in] `GUID` di una lingua (un valore null è accettabile).

`iid`\
[in] `IID` del servizio da ottenere.

`ppService`\
[fuori] Interfaccia al servizio richiesto.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Passare `IID` l'interfaccia [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) (`IID_IEEVisualizerServiceProvider`) per verificare se il servizio Visualizzatore tipi è disponibile. In tal caso, l'analizzatore di espressioni può ottenere l'interfaccia [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) per supportare i visualizzatori di tipo. Per informazioni dettagliate, vedere [Visualizzazione e visualizzazione dei dati.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="see-also"></a>Vedere anche
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
