---
title: Proprietà IEEVisualizerDataProvider . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718060"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)espressioni gestite .

 Questa interfaccia consente di modificare il valore di un oggetto tramite un visualizzatore di tipo.

## <a name="syntax"></a>Sintassi

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni implementa questa interfaccia per supportare la modifica dei dati in un oggetto proprietà tramite un visualizzatore di tipo.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene utilizzata nella creazione dell'oggetto [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) tramite una chiamata a [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Per ulteriori informazioni, vedere [Visualizzazione e visualizzazione dei dati.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable

|Metodo|Descrizione|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Determina se è possibile aggiornare l'oggetto (e successivamente il relativo valore) rappresentato da questo visualizzatore.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Forza una nuova valutazione dell'oggetto per questo visualizzatore.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Ottiene un oggetto esistente per questo visualizzatore (non viene eseguita alcuna valutazione).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aggiorna l'oggetto per questo visualizzatore, modificando in tal modo il valore presente dal visualizzatore.|

## <a name="remarks"></a>Osservazioni
 Il servizio visualizzatore (rappresentato dall'interfaccia [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) e restituito da [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) `IEEVisualizerDataProvider` ) mantiene un riferimento all'oggetto che implementa l'interfaccia. Di conseguenza, `IEEVisualizerDataProvider` l'interfaccia non deve essere implementata sullo stesso oggetto che implementa il `IEEVisualizerService` [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) se tale oggetto mantiene un riferimento all'oggetto: un riferimento circolare risultati e un deadlock si verifica quando gli oggetti vengono eliminati. L'approccio consigliato `IEEVisualizerDataProvider` consiste nell'implementare `IDebugProperty2` su un `IUnknown::AddRef` oggetto separato a cui l'oggetto delega senza chiamarlo.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
