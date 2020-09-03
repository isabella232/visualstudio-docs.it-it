---
title: IEEVisualizerServiceProvider | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717881"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia consente di accedere a un metodo che può creare un servizio del visualizzatore, che viene usato per gestire le attività del Visualizzatore di tipi per l'IDE.

## <a name="syntax"></a>Sintassi

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa questa interfaccia per creare un oggetto del servizio del visualizzatore, che a sua volta viene usato per fornire `CLSID` gli ID di classe dei visualizzatori di tipo all'IDE di Visual Studio.

## <a name="notes-for-callers"></a>Note per i chiamanti
 L'analizzatore di espressioni (EE) chiama [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable

|Metodo|Descrizione|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Crea il servizio del Visualizzatore|

## <a name="remarks"></a>Osservazioni
 L' `IEEVisualizerServiceProvider` interfaccia viene ottenuta durante l'implementazione di [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Il servizio del visualizzatore creato da questa interfaccia viene usato per fornire funzionalità a un'interfaccia [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , che è responsabile dell'implementazione di EE. EE è anche responsabile dell'implementazione di un'interfaccia [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) che consente ai visualizzatori di tipi di visualizzare e modificare il valore di una proprietà.

 Per informazioni dettagliate sul modo in cui queste interfacce interagiscono, vedere [visualizzazione e visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
