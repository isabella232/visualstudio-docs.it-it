---
title: IDebugArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be1f65e3814cbd88d32a63169234a42f76db4e6d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337582"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia rappresenta un oggetto matrice.

## <a name="syntax"></a>Sintassi

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni implementa questa interfaccia per rappresentare una matrice.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia può ottenere questa interfaccia tramite [QueryInterface](/cpp/atl/queryinterface) se l'oggetto rappresenta una matrice.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi nel `IDebugObject` interfaccia, i metodi seguenti vengono implementati nel `IDebugArrayObject` interfaccia.

|Metodo|Descrizione|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Ottiene il numero di elementi nella matrice.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Ottiene un elemento della matrice.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Ottiene tutti gli elementi della matrice.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Ottiene il rango della matrice.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Ottiene le dimensioni della matrice.|

## <a name="remarks"></a>Note
 Un analizzatore di espressioni usa questa interfaccia per rappresentare le matrici in un albero di analisi.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)