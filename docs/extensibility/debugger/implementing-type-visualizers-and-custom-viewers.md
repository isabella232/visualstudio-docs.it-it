---
title: Implementazione di visualizzatori di tipi e visualizzatori personalizzati | Microsoft Docs
description: Informazioni sull'implementazione di visualizzatori di tipi e visualizzatori personalizzati che consentono a un utente di visualizzare i dati in modo più significativo rispetto a un dump di numeri.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 79df5f6c7bf11c791f8de415f7cf1532321ed57a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059782"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implementare visualizzatori di tipi e visualizzatori personalizzati
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 I visualizzatori di tipi e i visualizzatori personalizzati consentono a un utente di visualizzare i dati di un determinato tipo in modo più significativo rispetto a un semplice dump esadecimale di numeri. Un analizzatore di espressioni (EE) può associare visualizzatori personalizzati a tipi specifici di dati o variabili. Questi visualizzatori personalizzati sono implementati da EE. EE può inoltre supportare i visualizzatori di tipi esterni, che possono provenire da un altro fornitore di terze parti o persino dall'utente finale.

## <a name="discussion"></a>Discussione

### <a name="type-visualizers"></a>Visualizzatori di tipi
 Visual Studio richiede un elenco di visualizzatori di tipi e visualizzatori personalizzati per ogni oggetto da visualizzare in una finestra espressioni di controllo. Un analizzatore di espressioni (EE) fornisce tale elenco per ogni tipo per il quale desidera supportare i visualizzatori dei tipi e i visualizzatori personalizzati. Le chiamate a [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) avviano l'intero processo di accesso ai visualizzatori di tipi e ai visualizzatori personalizzati. per informazioni dettagliate sulla sequenza chiamante, vedere [visualizzazione e visualizzazione dei dati](../../extensibility/debugger/visualizing-and-viewing-data.md) .

### <a name="custom-viewers"></a>Visualizzatori personalizzati
 I visualizzatori personalizzati sono implementati in EE per un tipo di dati specifico e sono rappresentati dall'interfaccia [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) . Un visualizzatore personalizzato non è flessibile come visualizzatore di tipi, perché è disponibile solo quando è in esecuzione l'EE che implementa quel particolare visualizzatore personalizzato. L'implementazione di un visualizzatore personalizzato è più semplice rispetto all'implementazione del supporto per i visualizzatori di tipi. Tuttavia, i visualizzatori di tipi di supporto offrono la massima flessibilità all'utente finale per la visualizzazione dei dati. Il resto di questa discussione riguarda solo i visualizzatori dei tipi.

## <a name="interfaces"></a>Interfacce
 EE implementa le interfacce seguenti per supportare i visualizzatori di tipi, che devono essere utilizzati da Visual Studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE utilizza le interfacce seguenti per supportare i visualizzatori dei tipi:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Vedi anche
- [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizzazione e visualizzazione dei dati](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
