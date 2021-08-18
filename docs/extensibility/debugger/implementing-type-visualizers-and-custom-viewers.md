---
title: Implementazione di visualizzatori di tipi e visualizzatori personalizzati | Microsoft Docs
description: Informazioni sull'implementazione di visualizzatori di tipi e visualizzatori personalizzati, che consentono a un utente di visualizzare i dati in modo più significativo rispetto a un dump di numeri.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: b42afdc165540360d8d8c1c458e1c044dbcbcddd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138757"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implementare visualizzatori di tipi e visualizzatori personalizzati
> [!IMPORTANT]
> In Visual Studio 2015 questa modalità di implementazione degli analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 I visualizzatori di tipi e i visualizzatori personalizzati consentono a un utente di visualizzare i dati di un particolare tipo in modo più significativo rispetto a un semplice dump esadecimale di numeri. Un analizzatore di espressioni (edizione Enterprise) può associare visualizzatori personalizzati a tipi specifici di dati o variabili. Questi visualizzatori personalizzati vengono implementati dal edizione Enterprise. Il edizione Enterprise può supportare anche visualizzatori di tipi esterni, che possono essere provenienti da un altro fornitore di terze parti o anche dall'utente finale.

## <a name="discussion"></a>Discussione

### <a name="type-visualizers"></a>Visualizzatori di tipi
 Visual Studio richiede un elenco di visualizzatori di tipo e visualizzatori personalizzati per ogni oggetto da visualizzare in una finestra Espressioni di controllo. Un analizzatore di espressioni (edizione Enterprise) fornisce un elenco di questo tipo per ogni tipo per cui vuole supportare visualizzatori di tipi e visualizzatori personalizzati. Le chiamate [a GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) avviano l'intero processo [](../../extensibility/debugger/visualizing-and-viewing-data.md) di accesso ai visualizzatori di tipi e ai visualizzatori personalizzati. Per informazioni dettagliate sulla sequenza di chiamata, vedere Visualizzazione e visualizzazione dei dati.

### <a name="custom-viewers"></a>Visualizzatori personalizzati
 I visualizzatori personalizzati vengono implementati edizione Enterprise per un tipo di dati specifico e sono rappresentati [dall'interfaccia IDebugCustomViewer.](../../extensibility/debugger/reference/idebugcustomviewer.md) Un visualizzatore personalizzato non è flessibile quanto un visualizzatore di tipi, perché è disponibile solo quando è in esecuzione il edizione Enterprise che implementa tale visualizzatore personalizzato specifico. L'implementazione di un visualizzatore personalizzato è più semplice rispetto all'implementazione del supporto per i visualizzatori di tipi. Tuttavia, il supporto dei visualizzatori di tipi offre la massima flessibilità all'utente finale per la visualizzazione dei dati. Il resto di questa discussione riguarda solo i visualizzatori di tipi.

## <a name="interfaces"></a>Interfacce
 Il edizione Enterprise implementa le interfacce seguenti per supportare i visualizzatori di tipi, che devono essere utilizzati da Visual Studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  Il edizione Enterprise utilizza le interfacce seguenti per supportare i visualizzatori di tipi:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Vedi anche
- [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizzazione e visualizzazione dei dati](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
