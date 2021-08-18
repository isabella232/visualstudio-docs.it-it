---
description: Questa interfaccia consente di accedere a un metodo in grado di creare un servizio visualizzatore, usato per gestire le attività del visualizzatore di tipi per l'IDE.
title: IEEVisualizerServiceProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: acaa7071d2b204fead807f9fb2e36ec0d5abff2b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125816"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [Clr Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia consente di accedere a un metodo in grado di creare un servizio visualizzatore, usato per gestire le attività del visualizzatore di tipi per l'IDE.

## <a name="syntax"></a>Sintassi

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio questa interfaccia per creare un oggetto servizio del visualizzatore, che a sua volta viene usato per fornire gli ID di classe (s) dei visualizzatori di tipo `CLSID` all'IDE Visual Studio.

## <a name="notes-for-callers"></a>Note per i chiamanti
 L'analizzatore di espressioni (edizione Enterprise) chiama [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable

|Metodo|Descrizione|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Crea il servizio visualizzatore|

## <a name="remarks"></a>Commenti
 `IEEVisualizerServiceProvider`L'interfaccia viene ottenuta durante l'implementazione [di EvaluateSync.](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) Il servizio visualizzatore creato da questa interfaccia viene usato per fornire funzionalità a un'interfaccia [IDebugProperty3,](../../../extensibility/debugger/reference/idebugproperty3.md) che il edizione Enterprise è responsabile dell'implementazione. Il edizione Enterprise è anche responsabile dell'implementazione di [un'interfaccia IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) che consente ai visualizzatori di tipi di visualizzare e modificare il valore di una proprietà.

 Per [informazioni dettagliate sull'interazione](../../../extensibility/debugger/visualizing-and-viewing-data.md) di queste interfacce, vedere Visualizzazione e visualizzazione dei dati.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
