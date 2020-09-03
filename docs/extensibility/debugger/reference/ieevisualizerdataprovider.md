---
title: IEEVisualizerDataProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a10f306b6c507f6db7add17931b8a38d926a37d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718060"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia offre la possibilità di modificare il valore di un oggetto tramite un visualizzatore di tipi.

## <a name="syntax"></a>Sintassi

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni implementa questa interfaccia per supportare la modifica dei dati in un oggetto proprietà tramite un visualizzatore di tipi.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene utilizzata per la creazione dell'oggetto [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) tramite una chiamata a [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Per altri dettagli, vedere [visualizzazione e visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable

|Metodo|Descrizione|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Determina se è possibile aggiornare l'oggetto (e successivamente il relativo valore) che questo visualizzatore sta rappresentando.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Impone una nuova valutazione dell'oggetto per questo visualizzatore.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Ottiene un oggetto esistente per il Visualizzatore (non viene eseguita alcuna valutazione).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aggiorna l'oggetto per questo visualizzatore, modificando in tal modo il valore presentato dal visualizzatore.|

## <a name="remarks"></a>Osservazioni
 Il servizio del Visualizzatore (come rappresentato dall'interfaccia [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) e restituito da [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) mantiene un riferimento all'oggetto che implementa l' `IEEVisualizerDataProvider` interfaccia. Di conseguenza, l' `IEEVisualizerDataProvider` interfaccia non deve essere implementata nello stesso oggetto che implementa [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) se tale oggetto mantiene un riferimento all' `IEEVisualizerService` oggetto: risultati circolari di riferimento e un deadlock si verifica quando gli oggetti vengono eliminati definitivamente. L'approccio consigliato consiste nell'implementare `IEEVisualizerDataProvider` su un oggetto separato a cui `IDebugProperty2` delegare l'oggetto senza chiamarlo `IUnknown::AddRef` .

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
