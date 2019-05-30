---
title: IDebugBinder3::GetEEService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3afc38551dc04e7fc7f6d55df81c5b7248127acd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327128"
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
[in] `GUID` del fornitore (un valore null è accettabile).

`language`\
[in] `GUID` di un linguaggio (un valore null è accettabile).

`iid`\
[in] `IID` del servizio da ottenere.

`ppService`\
[out] Interfaccia per il servizio richiesto.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Passare il `IID` per il [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) interfaccia (`IID_IEEVisualizerServiceProvider`) per verificare se il servizio Visualizzatore di tipi è disponibile. Se, pertanto, l'analizzatore di espressioni è possibile ottenere il [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) interfaccia per supportare i visualizzatori di tipo. Visualizzare [visualizzazione di dati e visualizzare](../../../extensibility/debugger/visualizing-and-viewing-data.md) per informazioni dettagliate.

## <a name="see-also"></a>Vedere anche
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)