---
description: Questa interfaccia fornisce un'interfaccia proxy per visualizzare e modificare i dati di un oggetto.
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 838bffb792d709dc237aae279f3af754d4e7873d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029216"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Questa interfaccia fornisce un'interfaccia proxy per visualizzare e modificare i dati di un oggetto.

## <a name="syntax"></a>Sintassi

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni (edizione Enterprise) implementa questa interfaccia sullo stesso oggetto che implementa l'interfaccia [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) come parte del supporto del edizione Enterprise di visualizzatori di tipi.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su `IDebugProperty3` un'interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 `IPropertyProxyProvider`L'interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Recupera un'interfaccia proxy di proprietà per visualizzare i dati in un oggetto .|

## <a name="remarks"></a>Commenti
 Anche se edizione Enterprise implementa questa interfaccia, l'implementazione di [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) viene in genere gestita [da GetPropertyProxy.](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) Per [informazioni dettagliate su come](../../../extensibility/debugger/visualizing-and-viewing-data.md) ottenere l'interfaccia IEEVisualizerService, vedere Visualizzazione e visualizzazione dei dati.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
