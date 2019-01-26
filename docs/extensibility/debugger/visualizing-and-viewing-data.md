---
title: Visualizzazione di tipi e i dati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41075bf41b63377ad6522b1be9602fe184b52217
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929679"
---
# <a name="visualizing-and-viewing-data"></a>Visualizzazione di tipi e i dati
Visualizzatori di tipi e visualizzatori personalizzati presentano i dati in un modo rapido significativo per gli sviluppatori. L'analizzatore di espressioni (EE) può supportare visualizzatori di tipi di terze parti, nonché fornire i propri visualizzatori personalizzati.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Determina il numero di visualizzatori di tipi e visualizzatori personalizzati associati al tipo dell'oggetto chiamando il [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) (metodo). Se si verifica il Visualizzatore di almeno un tipo o il visualizzatore personalizzato disponibile, Visual Studio chiama il [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metodo per recuperare un elenco dei visualizzatori e visualizzatori (in realtà, un elenco di valori che implementa i visualizzatori e visualizzatori) e li presenta all'utente.  
  
## <a name="supporting-type-visualizers"></a>Visualizzatori di tipi di supporto  
 Esistono una serie di interfacce che l'analizzatore di Espressioni deve implementare per supportare i visualizzatori di tipo. Queste interfacce possono essere suddivisa in due ampie categorie: le interfacce che sono elencati i visualizzatori di tipi e interfacce che accedono ai dati di proprietà.  
  
### <a name="listing-type-visualizers"></a>Visualizzatori di tipo elenco  
 L'analizzatore di Espressioni supporta visualizzatori dei tipi nella propria implementazione di listato `IDebugProperty3::GetCustomViewerCount` e `IDebugProperty3::GetCustomViewerList`. Questi metodi passano la chiamata ai metodi corrispondenti [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 Il [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) viene recuperato chiamando [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Questo metodo richiede la [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) interfaccia, che viene ottenuto dalle [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfaccia passata al [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` richiede anche il [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) e [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfacce che sono state passate a `IDebugParsedExpression::EvaluateSync`. L'interfaccia finale necessario per creare il `IEEVisualizerService` interfaccia è il [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfaccia che implementa l'analizzatore di Espressioni. Questa interfaccia consente modifiche da apportare alla proprietà visualizzata. Tutti i dati della proprietà è incapsulato in un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) interfaccia, che viene inoltre implementata dal motore di esecuzione.  
  
### <a name="accessing-property-data"></a>L'accesso ai dati di proprietà  
 L'accesso ai dati della proprietà viene eseguita tramite il [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaccia. Per ottenere questa interfaccia, Visual Studio chiama [QueryInterface](/cpp/atl/queryinterface) sull'oggetto di proprietà per ottenere il [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaccia (implementato nello stesso oggetto che implementa il [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interface) e quindi chiama il [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) metodo per ottenere il `IPropertyProxyEESide` interfaccia.  
  
 Tutti i dati passati in e dal `IPropertyProxyEESide` interfaccia è incapsulata nel [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) interfaccia. Questa interfaccia rappresenta una matrice di byte e viene implementata da Visual Studio e l'analizzatore di Espressioni. Quando i dati della proprietà deve essere modificato, Visual Studio crea un `IEEDataStorage` oggetto che contiene i nuovi dati e chiama [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) con tale oggetto dati per ottenere un nuovo `IEEDataStorage` oggetto, a sua volta, passato a [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) per aggiornare i dati della proprietà. `IPropertyProxyEESide::CreateReplacementObject` Consente l'analizzatore di Espressioni creare un'istanza di una propria classe che implementa il `IEEDataStorage` interfaccia.  
  
## <a name="supporting-custom-viewers"></a>Supporto di visualizzatori personalizzati  
 Il flag `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` è impostato `dwAttrib` campo il [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struttura (restituito da una chiamata a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) per indicare che l'oggetto dispone di un visualizzatore personalizzato associato con esso. Quando questo flag è impostato, Visual Studio Ottiene i [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) dell'interfaccia dal [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia utilizzando [QueryInterface](/cpp/atl/queryinterface).  
  
 Se l'utente seleziona un visualizzatore personalizzato, Visual Studio crea il visualizzatore personalizzato utilizzando il visualizzatore `CLSID` fornito dal `IDebugProperty3::GetCustomViewerList` (metodo). Visual Studio chiama quindi [disponibili DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) per mostrare il valore per l'utente.  
  
 In genere, `IDebugCustomViewer::DisplayValue` presenta una visualizzazione di sola lettura dei dati. Per consentire la modifica dei dati, l'analizzatore di Espressioni deve implementare un'interfaccia personalizzata che supporta la modifica dei dati su un oggetto proprietà. Il `IDebugCustomViewer::DisplayValue` metodo Usa questa interfaccia personalizzata per supportare la modifica dei dati. Il metodo è analogo per l'interfaccia personalizzata `IDebugProperty2` interfaccia passato come il `pDebugProperty` argomento.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Che supportano i visualizzatori di tipi e visualizzatori personalizzati  
 Un EE può supportare i visualizzatori di tipi e visualizzatori personalizzati disponibili nel [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metodi. In primo luogo, l'analizzatore di Espressioni aggiunge il numero di visualizzatori personalizzati che fornisce il valore restituito dal [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) (metodo). In secondo luogo, l'analizzatore di Espressioni aggiunge il `CLSID`s di propri visualizzatori personalizzati per l'elenco restituito dal [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)   
 [Visualizzatore di tipi e Visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)