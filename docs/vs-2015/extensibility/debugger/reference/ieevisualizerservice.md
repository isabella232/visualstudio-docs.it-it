---
title: IEEVisualizerService | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76e0ea47c1bfaea9bac96b3faacc3a01403f829d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530230"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IEEVisualizerService](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ieevisualizerservice).  
  
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia implementa i metodi principali che rendono disponibili funzionalità per la [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) e [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfacce.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa questa interfaccia per consentire un analizzatore di espressioni (EE) per supportare i visualizzatori di tipo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Le chiamate EE [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) per ottenere questa interfaccia come parte del supporto per i visualizzatori di tipo.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Recupera il numero di visualizzatori personalizzati intorno al quale questo servizio è in grado.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Recupera l'elenco di visualizzatori personalizzati.|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Restituisce un oggetto proxy per una proprietà.|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Recupera il numero di stringhe di valori da visualizzare per la proprietà specificata o il campo.|  
  
## <a name="remarks"></a>Note  
 L'IDE Usa il [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia per determinare se sono presenti eventuali visualizzatori personalizzati o digitare i visualizzatori per la proprietà. Tramite la creazione di un servizio del visualizzatore (con [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)), l'analizzatore di Espressioni può fornire la funzionalità per il `IDebugProperty3` e [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (che supporta la visualizzazione e modifica di un valore della proprietà) in tal modo supportare visualizzatori di tipi e interfacce.  
  
 Se un EE include visualizzatori personalizzati che a sua volta implementa, l'analizzatore di Espressioni è possibile aggiungere il `CLSID`s di tali visualizzatori personalizzati per la fine dell'elenco restituito da [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). In questo modo un EE supportare i visualizzatori di tipo e i proprio visualizzatori personalizzati. Accertarsi che [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) riflette l'aggiunta di eventuali visualizzatori personalizzati.  
  
 Visualizzare [Visualizzatore di tipi e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) per una descrizione della differenza tra i visualizzatori e visualizzatori.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

