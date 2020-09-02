---
title: IPropertyProxyEESide | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 660c792d9e13fabbd433aee46c57474fb824453f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684679"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia fornisce i metodi per visualizzare i dati nell'oggetto associato. Questa interfaccia è parte del supporto per i visualizzatori di tipi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un analizzatore di espressioni implementa questa interfaccia per supportare i visualizzatori di tipi.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) per ottenere questa interfaccia. Chiamare [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) su un'interfaccia [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) per ottenere l'interfaccia [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable  
 Questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inizializza un provider dell'origine dati in modo che sia possibile accedere ai dati dell'oggetto.|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Recupera le informazioni sull'assembly dell'oggetto.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Ottiene i dati iniziali per l'oggetto.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Crea una copia di un'archiviazione dati esistente.|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Crea un riferimento a un archivio dati esistente.|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Recupera informazioni su un assembly specifico nel contesto dell'assembly contenente questo oggetto.|  
  
## <a name="remarks"></a>Osservazioni  
 Un visualizzatore di tipi usa questa interfaccia per accedere ai valori associati all'oggetto di cui fa parte l'interfaccia. L'accesso ai dati viene eseguito tramite l'interfaccia [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) , che fornisce una visualizzazione di sola lettura dei dati.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
