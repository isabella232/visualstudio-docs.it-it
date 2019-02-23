---
title: IDebugBinder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48c82abb170f5002c8c08f1e3010b18587f42678
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716831"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia viene associata a un campo di simboli, in genere restituito dal provider di simboli, per un contesto in memoria o un oggetto che contiene valore corrente del simbolo.

## <a name="syntax"></a>Sintassi

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia supporta la valutazione dell'espressione e deve essere implementata dal motore di debug (DE).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia verrà usata durante la valutazione dell'espressione e viene in genere usata nell'implementazione di [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugBinder`.

|Metodo|Descrizione|
|------------|-----------------|
|[Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Ottiene il contesto in memoria o un oggetto che contiene valore corrente del simbolo.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina il tipo di fase di esecuzione di un oggetto.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Converte un indirizzo di memoria o percorso oggetto in un contesto in memoria.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Ottiene un' [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) oggetto utilizzato per creare parametri di funzione.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Ottiene il tipo esatto di una variabile.|

## <a name="remarks"></a>Note
 Questa interfaccia restituisce gli oggetti utilizzati dall'analizzatore di espressioni nelle strutture di analisi. L'analizzatore di espressioni analizza un'espressione tramite il provider di simboli per convertire i simboli nell'espressione alle istanze del [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), che descrivono ogni simbolo per quanto riguarda la posizione nel codice sorgente e il tipo. Il [associare](../../../extensibility/debugger/reference/idebugbinder-bind.md) metodo converte `IDebugField` oggetti [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetti connessi o associare un simbolo di tipo a un valore effettivo in memoria. Questi `IDebugObject` gli oggetti vengono quindi archiviati in un albero di analisi per la valutazione successiva.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)