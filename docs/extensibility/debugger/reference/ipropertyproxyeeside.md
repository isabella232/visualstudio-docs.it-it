---
description: Questa interfaccia fornisce i metodi per visualizzare i dati nell'oggetto associato.
title: IPropertyProxyEESide | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 80a295ad68341cfa4675d36b22d5de042078a0a3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222608"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Questa interfaccia fornisce i metodi per visualizzare i dati nell'oggetto associato. Questa interfaccia è parte del supporto per i visualizzatori di tipi.

## <a name="syntax"></a>Sintassi

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un analizzatore di espressioni implementa questa interfaccia per supportare i visualizzatori di tipi.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) per ottenere questa interfaccia. Chiamare [QueryInterface](/cpp/atl/queryinterface) su un'interfaccia [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) per ottenere l'interfaccia [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .

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

## <a name="remarks"></a>Commenti
 Un visualizzatore di tipi usa questa interfaccia per accedere ai valori associati all'oggetto di cui fa parte l'interfaccia. L'accesso ai dati viene eseguito tramite l'interfaccia [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) , che fornisce una visualizzazione di sola lettura dei dati.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
