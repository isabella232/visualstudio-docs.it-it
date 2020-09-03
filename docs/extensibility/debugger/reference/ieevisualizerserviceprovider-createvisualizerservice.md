---
title: 'IEEVisualizerServiceProvider:: CreateVisualizerService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e05677122b7d4e4eb025a9382ede1509374de894
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717914"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Questo metodo crea un servizio visualizzatore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>Parametri
`binder`\
in Oggetto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) passato a [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).

`pSymProv`\
in Oggetto [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) passato a `IDebugParsedExpression::EvaluateSync` .

`pAddress`\
in Oggetto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) passato a `IDebugParsedExression::EvaluateSync` .

`dataProvider`\
in Oggetto che implementa l'interfaccia [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (fornita dall'analizzatore di espressioni).

`ppService`\
out Il servizio creato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 I `binder` `pSymProv` parametri, e `pAddress` sono stati tutti passati al `IDebugParsedExpression::EvaluateSync` metodo. `CreateVisualizerService` deve essere chiamato solo da `IDebugParsedExpression::EvaluateSync` come parte del supporto dell'analizzatore di espressioni per i visualizzatori di tipi.

## <a name="see-also"></a>Vedere anche
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
