---
title: Implementazione di visualizzatori di tipi e visualizzatori personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 99eba66a3e77ab0a2771d4a6c337040a5adde47c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531921"
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Implementazione di visualizzatori di tipi e visualizzatori personalizzati
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [implementazione di visualizzatori di tipi e visualizzatori personalizzati](https://docs.microsoft.com/visualstudio/extensibility/debugger/implementing-type-visualizers-and-custom-viewers).  
  
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visualizzatori di tipi e visualizzatori personalizzati consentono un utente di visualizzare i dati di un determinato tipo in modo da renderlo più descrittivo rispetto a un semplice dump esadecimale dei numeri. Un analizzatore di espressioni (EE) è possibile associare visualizzatori personalizzati a specifici tipi di dati o le variabili. Questi visualizzatori personalizzati vengono implementati mediante l'analizzatore di Espressioni. L'analizzatore di Espressioni può supportare anche i visualizzatori di tipo esterno, che possono provenire da un altro fornitore di terze parti o anche l'utente finale.  
  
## <a name="discussion"></a>Discussione  
  
### <a name="type-visualizers"></a>Visualizzatori di tipi  
 Visual Studio richiede un elenco di visualizzatori di tipi e visualizzatori personalizzati per tutti gli oggetti da visualizzare in una finestra Espressioni di controllo. Un analizzatore di espressioni (EE) fornisce tale elenco per ogni tipo per cui vuole supportare visualizzatori di tipi e visualizzatori personalizzati. Le chiamate a [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) avvia l'intero processo di accesso ai visualizzatori di tipi e visualizzatori personalizzati (vedere [visualizzare e visualizzazione dei dati](../../extensibility/debugger/visualizing-and-viewing-data.md)per informazioni dettagliate sulla sequenza di chiamata).  
  
### <a name="custom-viewers"></a>Visualizzatori personalizzati  
 Visualizzatori personalizzati vengono implementati nel motore di esecuzione per un tipo di dati specifico e sono rappresentati dal [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfaccia. Un visualizzatore personalizzato non è flessibile come un visualizzatore di tipo, perché è disponibile solo quando l'analizzatore di Espressioni che implementa tale particolare visualizzatore personalizzato è in esecuzione. Implementazione di un visualizzatore personalizzato è più semplice rispetto all'implementazione del supporto per i visualizzatori di tipo. Tuttavia, visualizzatori di tipi di supporto offre la massima flessibilità per l'utente finale per la visualizzazione dei dati alla propria. Nella parte restante di questa discussione riguarda solo i visualizzatori di tipi.  
  
## <a name="interfaces"></a>Interfacce  
 L'analizzatore di Espressioni implementa le interfacce seguenti per supportare i visualizzatori di tipo, deve essere utilizzato da Visual Studio:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 L'analizzatore di Espressioni Usa le interfacce seguenti per supportare i visualizzatori di tipo:  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Vedere anche  
 [La scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizzazione di tipi e i dati](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
