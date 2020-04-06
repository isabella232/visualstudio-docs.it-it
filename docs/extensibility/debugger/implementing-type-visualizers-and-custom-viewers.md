---
title: Implementazione di visualizzatori di tipi e visualizzatori personalizzati . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2ebbb5c8e27df4ae4baf2d9a9f1c3314188e2b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738503"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implementare visualizzatori di tipo e visualizzatori personalizzati
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 I visualizzatori di tipo e i visualizzatori personalizzati consentono a un utente di visualizzare i dati di un determinato tipo in modo più significativo rispetto a un semplice dump esadecimale di numeri. Un analizzatore di espressioni (EE) può associare visualizzatori personalizzati a tipi specifici di dati o variabili. Questi visualizzatori personalizzati vengono implementati da EE. EE può anche supportare visualizzatori di tipo esterno, che potrebbero provenire da un altro fornitore di terze parti o anche l'utente finale.

## <a name="discussion"></a>Discussione

### <a name="type-visualizers"></a>Visualizzatori di tipo
 Visual Studio richiede un elenco di visualizzatori di tipo e visualizzatori personalizzati per ogni oggetto da visualizzare in una finestra di controllo. Un analizzatore di espressioni (EE) fornisce un elenco di questo tipo per ogni tipo per il quale desidera supportare visualizzatori di tipo e visualizzatori personalizzati. Le chiamate a [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) avviano l'intero processo di accesso ai visualizzatori di tipo e ai visualizzatori personalizzati (vedere [Visualizzazione e visualizzazione dei dati](../../extensibility/debugger/visualizing-and-viewing-data.md) per informazioni dettagliate sulla sequenza di chiamata).

### <a name="custom-viewers"></a>Visualizzatori personalizzati
 I visualizzatori personalizzati vengono implementati in EE per un tipo di dati specifico e sono rappresentati dall'interfaccia [IDebugCustomViewer.](../../extensibility/debugger/reference/idebugcustomviewer.md) Un visualizzatore personalizzato non è flessibile come un visualizzatore di tipo, poiché è disponibile solo quando l'eE che implementa quel particolare visualizzatore personalizzato è in esecuzione. L'implementazione di un visualizzatore personalizzato è più semplice rispetto all'implementazione del supporto per i visualizzatori di tipo. Tuttavia, il supporto dei visualizzatori di tipo offre la massima flessibilità all'utente finale per la visualizzazione dei dati. Il resto di questa discussione riguarda solo i visualizzatori di tipo.

## <a name="interfaces"></a>Interfacce
 L'eE implementa le interfacce seguenti per supportare i visualizzatori di tipo, che devono essere utilizzati da Visual Studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE utilizza le interfacce seguenti per supportare i visualizzatori di tipo:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Vedere anche
- [Scrittura di un analizzatore di espressioni CLRWriting a CLR expression evaluator](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizzazione e visualizzazione dei dati](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
