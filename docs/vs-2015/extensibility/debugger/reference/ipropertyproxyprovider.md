---
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5de601ef0266763ddd7243e4c526edca24803335
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967184"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia fornisce un'interfaccia proxy per visualizzare e modificare i dati di un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni (EE) implementa questa interfaccia nello stesso oggetto che implementa il [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia come parte del supporto del motore di esecuzione dei visualizzatori di tipi.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) su un `IDebugProperty3` interfaccia per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Il `IPropertyProxyProvider` interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Recupera un'interfaccia proxy di proprietà per visualizzare i dati in un oggetto.|  
  
## <a name="remarks"></a>Note  
 Anche se l'analizzatore di Espressioni implementa questa interfaccia, l'implementazione di [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) viene generalmente gestita dagli [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Visualizzare [visualizzazione di dati e visualizzare](../../../extensibility/debugger/visualizing-and-viewing-data.md) per informazioni dettagliate su come ottenere l'interfaccia IEEVisualizerService.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualizzatore di tipi e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
