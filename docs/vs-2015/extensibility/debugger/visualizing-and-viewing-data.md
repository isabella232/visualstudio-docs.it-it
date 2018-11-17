---
title: Visualizzazione di tipi e i dati | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f26ed20eccbff52afdc4f8b5060ad426cc100b71
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737416"
---
# <a name="visualizing-and-viewing-data"></a>Visualizzazione di tipi e dati
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visualizzatori di tipi e visualizzatori personalizzati presentano i dati in un modo rapido significativo per gli sviluppatori. L'analizzatore di espressioni (EE) può supportare visualizzatori di tipi di terze parti, nonché fornire i propri visualizzatori personalizzati.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Determina il numero di visualizzatori di tipi e visualizzatori personalizzati associati al tipo dell'oggetto chiamando il [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) (metodo). Se si verifica il Visualizzatore di almeno un tipo o il visualizzatore personalizzato disponibile, Visual Studio chiama il [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metodo per recuperare un elenco dei visualizzatori e visualizzatori (in realtà, un elenco di `CLSID`s che implementano il i visualizzatori e visualizzatori) e li presenta all'utente.  
  
## <a name="supporting-type-visualizers"></a>Visualizzatori di tipi di supporto  
 Esistono una serie di interfacce che l'analizzatore di Espressioni deve implementare per supportare i visualizzatori di tipo. Queste interfacce possono essere suddivisa in due ampie categorie: quelli che sono elencati i visualizzatori di tipi e quelli che accedono ai dati di proprietà.  
  
### <a name="listing-type-visualizers"></a>Visualizzatori di tipo elenco  
 L'analizzatore di Espressioni supporta visualizzatori dei tipi nella propria implementazione di listato `IDebugProperty3::GetCustomViewerCount` e `IDebugProperty3::GetCustomViewerList`. Questi metodi passano la chiamata ai metodi corrispondenti [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 Il [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) viene recuperato chiamando [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Questo metodo richiede la [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) interfaccia, che viene ottenuto dalle [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfaccia passata al [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` richiede anche il [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) e [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfacce che sono state trasmesse a `IDebugParsedExpression::EvaluateSync`. L'interfaccia finale necessario per creare il `IEEVisualizerService` interfaccia è il [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfaccia che implementa l'analizzatore di Espressioni. Questa interfaccia consente modifiche da apportare alla proprietà visualizzata. Tutti i dati della proprietà è incapsulato in un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) interfaccia, che viene inoltre implementata dal motore di esecuzione.  
  
### <a name="accessing-property-data"></a>L'accesso ai dati di proprietà  
 L'accesso ai dati della proprietà viene eseguita tramite il [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaccia. Per ottenere questa interfaccia, Visual Studio chiama [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sull'oggetto di proprietà per ottenere il [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaccia (implementato nello stesso oggetto che implementa il [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interface) e quindi chiama il [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) metodo per ottenere il `IPropertyProxyEESide` interfaccia.  
  
 Tutti i dati passati in e dal `IPropertyProxyEESide` interfaccia è incapsulata nel [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) interfaccia. Questa interfaccia rappresenta una matrice di byte e viene implementata da Visual Studio e l'analizzatore di Espressioni. Quando i dati della proprietà deve essere modificato, Visual Studio crea un `IEEDataStorage` oggetto che contiene i nuovi dati e chiama [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) con tale oggetto dati per ottenere un nuovo `IEEDataStorage` oggetto, a sua volta, passato a [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) per aggiornare i dati della proprietà. `IPropertyProxyEESide::CreateReplacementObject` Consente l'analizzatore di Espressioni creare un'istanza di una propria classe che implementa il `IEEDataStorage` interfaccia.  
  
## <a name="supporting-custom-viewers"></a>Supporto di visualizzatori personalizzati  
 Il flag `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` è impostato `dwAttrib` campo il [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struttura (restituito da una chiamata a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) per indicare che l'oggetto dispone di un visualizzatore personalizzato associato con esso. Quando questo flag è impostato, Visual Studio Ottiene i [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) dell'interfaccia dal [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia utilizzando [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3).  
  
 Se l'utente seleziona un visualizzatore personalizzato, Visual Studio crea il visualizzatore personalizzato utilizzando il visualizzatore `CLSID` fornito dal `IDebugProperty3::GetCustomViewerList` (metodo). Visual Studio chiama quindi [disponibili DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) per mostrare il valore per l'utente.  
  
 In genere, `IDebugCustomViewer::DisplayValue` presenta una visualizzazione di sola lettura dei dati. Per consentire la modifica dei dati, l'analizzatore di Espressioni deve implementare un'interfaccia personalizzata che supporta la modifica dei dati su un oggetto proprietà. Il `IDebugCustomViewer::DisplayValue` metodo Usa questa interfaccia personalizzata per supportare la modifica dei dati. Il metodo è analogo per l'interfaccia personalizzata `IDebugProperty2` interfaccia passato come il `pDebugProperty` argomento.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Che supportano entrambi digitare visualizzatori e visualizzatori personalizzati  
 Un EE può supportare i visualizzatori di tipi e visualizzatori personalizzati disponibili nel [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metodi. In primo luogo, l'analizzatore di Espressioni aggiunge il numero di visualizzatori personalizzati che fornisce il valore restituito dal [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) (metodo). In secondo luogo, l'analizzatore di Espressioni aggiunge il `CLSID`s di propri visualizzatori personalizzati per l'elenco restituito dal [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)   
 [Visualizzatore di tipi e visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

