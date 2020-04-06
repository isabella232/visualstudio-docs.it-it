---
title: Proprietà IEEVisualizerServiceProvider . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44d8a73589a4248736ac6c4d73814166056a1f90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717881"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)espressioni gestite .

 Questa interfaccia consente di accedere a un metodo che può creare un servizio visualizzatore, che viene utilizzato per gestire le attività del visualizzatore di tipo per l'IDE.

## <a name="syntax"></a>Sintassi

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa questa interfaccia per creare un oggetto servizio visualizzatore, che`CLSID`a sua volta viene utilizzato per fornire gli ID di classe ( s) dei visualizzatori di tipo per l'IDE di Visual Studio.Visual Studio implements this interface to create a visualizer service object, which in turn is used to supply class IDs ( s) of type visualizers to the Visual Studio IDE.

## <a name="notes-for-callers"></a>Note per i chiamanti
 L'analizzatore di espressioni (EE) chiama [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable

|Metodo|Descrizione|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Crea il servizio visualizzatore|

## <a name="remarks"></a>Osservazioni
 L'interfaccia `IEEVisualizerServiceProvider` viene ottenuta durante l'implementazione di [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Il servizio visualizzatore creato da questa interfaccia viene utilizzato per fornire funzionalità a un [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia, che eE è responsabile per l'implementazione. L'eE è anche responsabile per l'implementazione di un [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfaccia che consente ai visualizzatori di tipo visualizzare e modificare il valore di una proprietà.

 Per informazioni dettagliate sull'interazione di queste interfacce, vedere [Visualizzazione e visualizzazione dei dati.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
