---
title: Proprietà IEEVisualizerServiceProvider::CreateVisualizerService . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
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
[in] Oggetto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) passato a [EvaluateSync.](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)

`pSymProv`\
[in] L'oggetto [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) passato a `IDebugParsedExpression::EvaluateSync`.

`pAddress`\
[in] L'oggetto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) passato a `IDebugParsedExression::EvaluateSync`.

`dataProvider`\
[in] Oggetto che implementa l'interfaccia [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (fornita dall'analizzatore di espressioni).

`ppService`\
[fuori] Servizio creato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 I `binder` `pSymProv`parametri `pAddress` , e sono `IDebugParsedExpression::EvaluateSync` stati tutti passati al metodo. `CreateVisualizerService`deve essere chiamato `IDebugParsedExpression::EvaluateSync` solo da come parte del supporto di un analizzatore di espressioni per i visualizzatori di tipo.

## <a name="see-also"></a>Vedere anche
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
