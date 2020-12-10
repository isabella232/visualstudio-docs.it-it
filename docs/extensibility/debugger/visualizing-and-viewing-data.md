---
title: Visualizzazione e visualizzazione dei dati | Microsoft Docs
description: Informazioni su come i visualizzatori di tipi e i visualizzatori personalizzati presentano dati a uno sviluppatore. L'analizzatore di espressioni supporta i visualizzatori di tipi di terze parti.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 856788546e10e69a8bb7e2787558505937f9effd
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995460"
---
# <a name="visualizing-and-viewing-data"></a>Visualizzazione e visualizzazione dei dati
I visualizzatori di tipi e i visualizzatori personalizzati presentano dati in modo rapido e significativo per uno sviluppatore. L'analizzatore di espressioni (EE) può supportare i visualizzatori di tipi di terze parti e fornire i propri visualizzatori personalizzati.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina il numero di visualizzatori di tipi e visualizzatori personalizzati associati al tipo di oggetto chiamando il metodo [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) . Se è disponibile almeno un visualizzatore di tipi o un visualizzatore personalizzato, Visual Studio chiama il metodo [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) per recuperare un elenco di visualizzatori e visualizzatori (in realtà, un elenco di che implementa i visualizzatori e i visualizzatori) e li presenta all'utente.

## <a name="supporting-type-visualizers"></a>Supporto di visualizzatori di tipi
 Sono disponibili numerose interfacce che devono essere implementate da EE per supportare i visualizzatori dei tipi. Queste interfacce possono essere suddivise in due ampie categorie: interfacce che elencano i visualizzatori e le interfacce dei tipi che accedono ai dati della proprietà.

### <a name="listing-type-visualizers"></a>Elenco di visualizzatori di tipi
 EE supporta l'elenco dei visualizzatori di tipi nell'implementazione di `IDebugProperty3::GetCustomViewerCount` e `IDebugProperty3::GetCustomViewerList` . Questi metodi passano la chiamata ai metodi [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)corrispondenti.

 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) viene ottenuto chiamando [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Questo metodo richiede l'interfaccia [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) , ottenuta dall'interfaccia [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) passata a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` richiede anche le interfacce [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) e [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) , che sono state passate a `IDebugParsedExpression::EvaluateSync` . L'interfaccia finale necessaria per creare l' `IEEVisualizerService` interfaccia è l'interfaccia [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , implementata da EE. Questa interfaccia consente di apportare modifiche alla proprietà visualizzata. Tutti i dati delle proprietà vengono incapsulati in un'interfaccia [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) , che viene anche implementata da EE.

### <a name="accessing-property-data"></a>Accesso ai dati delle proprietà
 L'accesso ai dati delle proprietà viene eseguito tramite l'interfaccia [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Per ottenere questa interfaccia, Visual Studio chiama [QueryInterface](/cpp/atl/queryinterface) sull'oggetto Property per ottenere l'interfaccia [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (implementata nello stesso oggetto che implementa l'interfaccia [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) ), quindi chiama il metodo [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) per ottenere l' `IPropertyProxyEESide` interfaccia.

 Tutti i dati passati all'interno e all'esterno dell' `IPropertyProxyEESide` interfaccia sono incapsulati nell'interfaccia [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) . Questa interfaccia rappresenta una matrice di byte e viene implementata sia da Visual Studio che da EE. Quando i dati di una proprietà devono essere modificati, Visual Studio crea un `IEEDataStorage` oggetto che contiene i nuovi dati e chiama [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) con tale oggetto dati per ottenere un nuovo `IEEDataStorage` oggetto che, a sua volta, viene passato a [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) per aggiornare i dati della proprietà. `IPropertyProxyEESide::CreateReplacementObject` consente a EE di creare un'istanza della propria classe che implementa l' `IEEDataStorage` interfaccia.

## <a name="supporting-custom-viewers"></a>Supporto di visualizzatori personalizzati
 Il flag `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` viene impostato nel `dwAttrib` campo della struttura [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) (restituito da una chiamata a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) per indicare che all'oggetto è associato un visualizzatore personalizzato. Quando questo flag è impostato, Visual Studio Ottiene l'interfaccia [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) dall'interfaccia [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) usando [QueryInterface](/cpp/atl/queryinterface).

 Se l'utente seleziona un visualizzatore personalizzato, Visual Studio crea un'istanza del visualizzatore personalizzato usando il visualizzatore `CLSID` fornito dal `IDebugProperty3::GetCustomViewerList` metodo. Visual Studio chiama quindi [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) per visualizzare il valore dell'utente.

 In genere, `IDebugCustomViewer::DisplayValue` presenta una visualizzazione di sola lettura dei dati. Per consentire le modifiche ai dati, EE deve implementare un'interfaccia personalizzata che supporta la modifica dei dati in un oggetto proprietà. Il `IDebugCustomViewer::DisplayValue` metodo usa questa interfaccia personalizzata per supportare la modifica dei dati. Il metodo cerca l'interfaccia personalizzata sull' `IDebugProperty2` interfaccia passata come `pDebugProperty` argomento.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Supporto di visualizzatori di tipi e visualizzatori personalizzati
 Un EE può supportare sia i visualizzatori di tipi che i visualizzatori personalizzati nei metodi [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) . In primo luogo, EE aggiunge il numero di visualizzatori personalizzati che fornisce al valore restituito dal metodo [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) . In secondo luogo, EE aggiunge gli oggetti `CLSID` dei propri visualizzatori personalizzati all'elenco restituito dal metodo [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) .

## <a name="see-also"></a>Vedere anche
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
