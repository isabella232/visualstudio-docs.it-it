---
title: Visualizzazione e visualizzazione dei dati Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b5f984e6c6a3c1c8f3835dfa93a8679ae16680a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712368"
---
# <a name="visualizing-and-viewing-data"></a>Visualizzazione e visualizzazione dei dati
I visualizzatori di tipo e i visualizzatori personalizzati presentano i dati in modo significativo per uno sviluppatore. L'analizzatore di espressioni (EE) può supportare visualizzatori di tipo di terze parti e fornire i propri visualizzatori personalizzati.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]determina il numero di visualizzatori di tipo e visualizzatori personalizzati associati al tipo dell'oggetto chiamando il [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) metodo. Se è disponibile almeno un visualizzatore di tipo o un visualizzatore personalizzato, Visual Studio chiama il [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metodo per recuperare un elenco di tali visualizzatori e visualizzatori (in realtà, un elenco di s che implementa i visualizzatori e visualizzatori) e li presenta all'utente.

## <a name="supporting-type-visualizers"></a>Supporto dei visualizzatori di tipoSupporting type visualizers
 Esistono diverse interfacce che l'eE deve implementare per supportare i visualizzatori di tipo. Queste interfacce possono essere suddivise in due categorie generali: interfacce che elencano i visualizzatori di tipo e le interfacce che accedono ai dati delle proprietà.

### <a name="listing-type-visualizers"></a>Elenco dei visualizzatori di tipoListing type visualizers
 L'EE supporta l'elenco dei visualizzatori di tipo nella relativa implementazione di `IDebugProperty3::GetCustomViewerCount` e `IDebugProperty3::GetCustomViewerList`. Questi metodi passano la chiamata ai metodi corrispondenti [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 Il [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) viene ottenuto chiamando [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Questo metodo richiede il [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) interfaccia, che viene ottenuta dal [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfaccia passata a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService`richiede anche le interfacce [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) e [IDebugAddress,](../../extensibility/debugger/reference/idebugaddress.md) che sono state passate a `IDebugParsedExpression::EvaluateSync`. L'interfaccia finale necessaria `IEEVisualizerService` per creare l'interfaccia è l'interfaccia [IEEVisualizerDataProvider,](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) implementata dall'interfaccia utente. Questa interfaccia consente di apportare modifiche alla proprietà visualizzata. Tutti i dati delle proprietà sono incapsulati in un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) interfaccia, che viene implementata anche da EE.

### <a name="accessing-property-data"></a>Accesso ai dati delle proprietà
 L'accesso ai dati delle proprietà viene eseguito tramite l'interfaccia IPropertyProxyEESide.Accessing property data is done through the [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface. Per ottenere questa interfaccia, Visual Studio chiama [QueryInterface](/cpp/atl/queryinterface) sull'oggetto proprietà per ottenere il [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaccia (implementata sullo stesso oggetto che `IPropertyProxyEESide` implementa il [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interfaccia) e quindi chiama il [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) metodo per ottenere l'interfaccia.

 Tutti i dati passati `IPropertyProxyEESide` all'esterno e all'esterno dell'interfaccia vengono incapsulati nell'interfaccia [IEEDataStorage.](../../extensibility/debugger/reference/ieedatastorage.md) Questa interfaccia rappresenta una matrice di byte e viene implementata da Visual Studio e EE. Quando i dati di una proprietà devono essere `IEEDataStorage` modificati, Visual Studio crea un oggetto contenente i nuovi `IEEDataStorage` dati e chiama [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) con tale oggetto dati per ottenere un nuovo oggetto che, a sua volta, viene passato a [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) per aggiornare i dati della proprietà. `IPropertyProxyEESide::CreateReplacementObject`consente a EE di creare un'istanza della propria classe che implementa l'interfaccia. `IEEDataStorage`

## <a name="supporting-custom-viewers"></a>Supporto di visualizzatori personalizzatiSupporting custom viewers
 Il `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` flag viene `dwAttrib` impostato nel campo della struttura [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) (restituito da una chiamata a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) per indicare che all'oggetto è associato un visualizzatore personalizzato. Quando questo flag è impostato, Visual Studio ottiene il [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interfaccia dal [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia utilizzando [QueryInterface](/cpp/atl/queryinterface).

 Se l'utente seleziona un visualizzatore personalizzato, Visual Studio crea `CLSID` un'istanza `IDebugProperty3::GetCustomViewerList` del visualizzatore personalizzato utilizzando il visualizzatore fornito dal metodo . Visual Studio chiama quindi [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) per mostrare il valore all'utente.

 In `IDebugCustomViewer::DisplayValue` genere, presenta una visualizzazione di sola lettura dei dati. Per consentire modifiche ai dati, EE deve implementare un'interfaccia personalizzata che supporta la modifica dei dati in un oggetto proprietà. Il `IDebugCustomViewer::DisplayValue` metodo utilizza questa interfaccia personalizzata per supportare la modifica dei dati. Il metodo cerca l'interfaccia `IDebugProperty2` personalizzata sull'interfaccia passata come `pDebugProperty` argomento.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Supporto sia dei visualizzatori di tipo che dei visualizzatori personalizzatiSupporting both type visualizers and custom viewers
 Un EE può supportare sia visualizzatori di tipo che visualizzatori personalizzati nei metodi [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList.](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) In primo luogo, l'EE aggiunge il numero di visualizzatori personalizzati che fornisce al valore restituito dal [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) metodo. In secondo luogo, l'EE aggiunge le `CLSID`s dei propri visualizzatori personalizzati all'elenco restituito dal [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) metodo.

## <a name="see-also"></a>Vedere anche
- [Attività di debugDebugging tasks](../../extensibility/debugger/debugging-tasks.md)
- [Visualizzatore di tipo e visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
