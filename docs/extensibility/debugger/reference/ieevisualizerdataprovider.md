---
description: Questa interfaccia consente di modificare il valore di un oggetto tramite un visualizzatore di tipi.
title: IEEVisualizerDataProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d52f90e0fe2dc33fd8d790bfce5ef9304f6df745
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103507"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [Clr Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia consente di modificare il valore di un oggetto tramite un visualizzatore di tipi.

## <a name="syntax"></a>Sintassi

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni implementa questa interfaccia per supportare la modifica dei dati in un oggetto proprietà tramite un visualizzatore di tipi.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene usata nella creazione [dell'oggetto IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) tramite una chiamata a [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Per [altri dettagli, vedere Visualizzazione e visualizzazione](../../../extensibility/debugger/visualizing-and-viewing-data.md) dei dati.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable

|Metodo|Descrizione|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Determina se è possibile aggiornare l'oggetto (e successivamente il relativo valore) rappresentato da questo visualizzatore.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Forza una nuova valutazione dell'oggetto per questo visualizzatore.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Ottiene un oggetto esistente per questo visualizzatore (non viene eseguita alcuna valutazione).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aggiorna l'oggetto per questo visualizzatore, modificando così il valore visualizzato dal visualizzatore.|

## <a name="remarks"></a>Commenti
 Il servizio visualizzatore ( rappresentato [dall'interfaccia IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) e restituito da [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) mantiene un riferimento all'oggetto che implementa l'interfaccia. `IEEVisualizerDataProvider` Di conseguenza, l'interfaccia non deve essere implementata nello stesso oggetto che implementa `IEEVisualizerDataProvider` [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) se tale oggetto mantiene un riferimento all'oggetto: viene generato un riferimento circolare e si verifica un deadlock quando gli oggetti vengono `IEEVisualizerService` distrutti. L'approccio consigliato consiste nell'implementare in un oggetto separato a `IEEVisualizerDataProvider` cui `IDebugProperty2` l'oggetto delega senza chiamare su di `IUnknown::AddRef` esso.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
