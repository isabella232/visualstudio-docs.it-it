---
title: Visualizzazione e visualizzazione dei dati | Microsoft Docs
description: Informazioni su come i visualizzatori di tipi e i visualizzatori personalizzati presentano i dati a uno sviluppatore. L'analizzatore di espressioni supporta visualizzatori di tipi di terze parti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: bd0fa59cec59e27949bf9d8d209bc66221d3505d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095114"
---
# <a name="visualizing-and-viewing-data"></a>Visualizzazione e visualizzazione dei dati
I visualizzatori di tipi e i visualizzatori personalizzati presentano i dati in modo rapido significativo per uno sviluppatore. L'analizzatore di espressioni (edizione Enterprise) può supportare visualizzatori di tipi di terze parti e fornire visualizzatori personalizzati.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]determina il numero di visualizzatori di tipi e visualizzatori personalizzati associati al tipo dell'oggetto chiamando il [metodo GetCustomViewerCount.](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) Se è disponibile almeno un visualizzatore di tipi o un visualizzatore personalizzato, Visual Studio chiama il metodo [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) per recuperare un elenco di tali visualizzatori e visualizzatori (in realtà, un elenco di oggetti che implementano i visualizzatori e i visualizzatori) e li presenta all'utente.

## <a name="supporting-type-visualizers"></a>Supporto dei visualizzatori di tipi
 Esistono alcune interfacce che il edizione Enterprise implementare per supportare i visualizzatori di tipi. Queste interfacce possono essere suddivise in due ampie categorie: interfacce che elencano i visualizzatori di tipi e interfacce che accedono ai dati delle proprietà.

### <a name="listing-type-visualizers"></a>Visualizzatori dei tipi di elenco
 Il edizione Enterprise supporta l'elenco dei visualizzatori di tipi nell'implementazione di `IDebugProperty3::GetCustomViewerCount` e `IDebugProperty3::GetCustomViewerList` . Questi metodi passano la chiamata ai metodi [corrispondenti GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) viene ottenuto chiamando [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Questo metodo richiede [l'interfaccia IDebugBinder3,](../../extensibility/debugger/reference/idebugbinder3.md) ottenuta [dall'interfaccia IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) passata a [EvaluateSync.](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) `IEEVisualizerServiceProvider::CreateVisualizerService` richiede anche [le interfacce IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) e [IDebugAddress,](../../extensibility/debugger/reference/idebugaddress.md) passate a `IDebugParsedExpression::EvaluateSync` . L'interfaccia finale necessaria per creare l'interfaccia `IEEVisualizerService` [è l'interfaccia IEEVisualizerDataProvider,](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) implementata edizione Enterprise interfaccia. Questa interfaccia consente di apportare modifiche alla proprietà da visualizzare. Tutti i dati delle proprietà sono incapsulati in [un'interfaccia IDebugObject,](../../extensibility/debugger/reference/idebugobject.md) implementata anche dal edizione Enterprise.

### <a name="accessing-property-data"></a>Accesso ai dati delle proprietà
 L'accesso ai dati delle proprietà viene eseguito tramite [l'interfaccia IPropertyProxyEESide.](../../extensibility/debugger/reference/ipropertyproxyeeside.md) Per ottenere questa interfaccia, Visual Studio chiama [QueryInterface](/cpp/atl/queryinterface) sull'oggetto proprietà per ottenere [l'interfaccia IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (implementata nello stesso oggetto che implementa l'interfaccia [IDebugProperty3)](../../extensibility/debugger/reference/idebugproperty3.md) e quindi chiama il [metodo GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) per ottenere l'interfaccia. `IPropertyProxyEESide`

 Tutti i dati passati all'interno e all'uscita `IPropertyProxyEESide` dall'interfaccia vengono incapsulati nell'interfaccia [IEEDataStorage.](../../extensibility/debugger/reference/ieedatastorage.md) Questa interfaccia rappresenta una matrice di byte e viene implementata sia da Visual Studio che dal edizione Enterprise. Quando i dati di una proprietà devono essere modificati, Visual Studio crea un oggetto che contiene i nuovi dati e chiama `IEEDataStorage` [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) con tale oggetto dati per ottenere un nuovo oggetto che, a sua volta, viene passato a `IEEDataStorage` [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) per aggiornare i dati della proprietà. `IPropertyProxyEESide::CreateReplacementObject`consente al edizione Enterprise di creare un'istanza della propria classe che implementa `IEEDataStorage` l'interfaccia .

## <a name="supporting-custom-viewers"></a>Supporto di visualizzatori personalizzati
 Il flag viene impostato nel campo della struttura DEBUG_PROPERTY_INFO (restituita da una chiamata `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` `dwAttrib` a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) [](../../extensibility/debugger/reference/debug-property-info.md) per indicare che all'oggetto è associato un visualizzatore personalizzato. Quando questo flag è impostato, Visual Studio'interfaccia [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) [dall'interfaccia IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) usando [QueryInterface](/cpp/atl/queryinterface).

 Se l'utente seleziona un visualizzatore personalizzato, Visual Studio crea un'istanza del visualizzatore personalizzato usando il visualizzatore `CLSID` fornito dal `IDebugProperty3::GetCustomViewerList` metodo . Visual Studio quindi chiama [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) per visualizzare il valore all'utente.

 In `IDebugCustomViewer::DisplayValue` genere, presenta una visualizzazione di sola lettura dei dati. Per consentire le modifiche ai dati, il edizione Enterprise deve implementare un'interfaccia personalizzata che supporti la modifica dei dati in un oggetto proprietà. Il `IDebugCustomViewer::DisplayValue` metodo usa questa interfaccia personalizzata per supportare la modifica dei dati. Il metodo cerca l'interfaccia personalizzata `IDebugProperty2` nell'interfaccia passata come `pDebugProperty` argomento.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Supporto di visualizzatori di tipi e visualizzatori personalizzati
 Un edizione Enterprise può supportare sia visualizzatori di tipi che visualizzatori personalizzati nei [metodi GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) [e GetCustomViewerList.](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) In primo luogo, edizione Enterprise il numero di visualizzatori personalizzati forniti al valore restituito dal [metodo GetCustomViewerCount.](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) In secondo edizione Enterprise aggiunge le proprietà dei propri visualizzatori personalizzati all'elenco `CLSID` restituito dal [metodo GetCustomViewerList.](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)

## <a name="see-also"></a>Vedi anche
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
