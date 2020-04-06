---
title: Proprietà IDebugArrayObject . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 709273b89d89759163acb725220d1092d33ad72f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736221"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)espressioni gestite .

 Questa interfaccia rappresenta un oggetto matrice.

## <a name="syntax"></a>Sintassi

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni implementa questa interfaccia per rappresentare una matrice.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia può ottenere questa interfaccia utilizzando [QueryInterface](/cpp/atl/queryinterface) se l'oggetto rappresenta una matrice.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi `IDebugObject` sull'interfaccia, sull'interfaccia `IDebugArrayObject` vengono implementati i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Ottiene il conteggio degli elementi nella matrice.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Ottiene un elemento della matrice.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Ottiene tutti gli elementi della matrice.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Ottiene il rango della matrice.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Ottiene le dimensioni della matrice.|

## <a name="remarks"></a>Osservazioni
 Un analizzatore di espressioni utilizza questa interfaccia per rappresentare le matrici in un albero di analisi.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
