---
description: Questa interfaccia implementa i metodi chiave che forniscono funzionalità alle interfacce IDebugProperty3 e IPropertyProxyEESide.
title: Interfaccia IEEVisualizerService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: dce24bb341c4b84fb91b6deedf83c96b67520831
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125868"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [Clr Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia implementa i metodi chiave che forniscono funzionalità alle [interfacce IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) e [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)

## <a name="syntax"></a>Sintassi

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa questa interfaccia per consentire a un analizzatore di espressioni (edizione Enterprise) di supportare i visualizzatori di tipi.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il edizione Enterprise chiama [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) per ottenere questa interfaccia come parte del supporto per i visualizzatori di tipi.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable

|Metodo|Descrizione|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Recupera il numero di visualizzatori personalizzati a cui il servizio è a conoscenza.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Recupera l'elenco di visualizzatori personalizzati.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Restituisce un oggetto proxy per una proprietà.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Recupera il numero di stringhe valore da visualizzare per la proprietà o il campo specificato.|

## <a name="remarks"></a>Commenti
 L'IDE usa [l'interfaccia IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) per determinare se sono presenti visualizzatori personalizzati o visualizzatori di tipi per la proprietà. Creando un servizio visualizzatore (con [CreateVisualizerService),](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)il edizione Enterprise può fornire la funzionalità alle interfacce e `IDebugProperty3` [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (che supporta la visualizzazione e la modifica del valore di una proprietà) e quindi supportare i visualizzatori di tipi.

 Se un edizione Enterprise dispone di visualizzatori personalizzati che implementa, il edizione Enterprise può aggiungere le proprietà di tali visualizzatori personalizzati alla fine dell'elenco restituito `CLSID` da [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Ciò consente a un edizione Enterprise di supportare sia i visualizzatori di tipi che i propri visualizzatori personalizzati. Assicurarsi solo che [GetCustomViewerCount rifletta](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) l'aggiunta di tutti i visualizzatori personalizzati.

 Per [una descrizione della](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) differenza tra visualizzatori e visualizzatori, vedere Visualizzatore di tipi e Visualizzatore personalizzato.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
