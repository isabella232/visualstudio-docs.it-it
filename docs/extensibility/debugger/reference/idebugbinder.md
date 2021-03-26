---
description: Questa interfaccia associa un campo di simboli, in genere restituito dal provider di simboli, a un contesto di memoria o a un oggetto che contiene il valore corrente del simbolo.
title: IDebugBinder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4fdfe0cffce209880d870cde7b70cc1e02252413
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089082"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia associa un campo di simboli, in genere restituito dal provider di simboli, a un contesto di memoria o a un oggetto che contiene il valore corrente del simbolo.

## <a name="syntax"></a>Sintassi

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia supporta la valutazione delle espressioni e deve essere implementata dal motore di debug (DE).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene utilizzata nel processo di valutazione delle espressioni e viene in genere utilizzata nell'implementazione di [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugBinder` .

|Metodo|Descrizione|
|------------|-----------------|
|[Associare](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Ottiene il contesto di memoria o l'oggetto che contiene il valore corrente del simbolo.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina il tipo in fase di esecuzione di un oggetto.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Converte un indirizzo di memoria o un percorso dell'oggetto in un contesto di memoria.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Ottiene un oggetto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) usato per creare i parametri della funzione.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Ottiene il tipo esatto per una variabile.|

## <a name="remarks"></a>Commenti
 Questa interfaccia restituisce gli oggetti utilizzati dall'analizzatore di espressioni negli alberi di analisi. L'analizzatore di espressioni analizza un'espressione utilizzando il provider di simboli per convertire i simboli nell'espressione in istanze di [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), che descrivono ogni simbolo in termini di tipo e posizione nel codice sorgente. Il metodo [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) converte `IDebugField` gli oggetti in oggetti [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che si connettono o associano un tipo di simbolo a un valore effettivo in memoria. Questi `IDebugObject` oggetti vengono quindi archiviati in un albero di analisi per una valutazione successiva.

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
