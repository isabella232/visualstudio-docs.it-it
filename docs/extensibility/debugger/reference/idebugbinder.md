---
title: Proprietà IDebugBinder . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcdec19c4667356edaf9e057c86ddc24baf747b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735966"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)espressioni gestite .

 Questa interfaccia associa un campo simbolo, in genere restituito dal provider di simboli, a un contesto di memoria o a un oggetto che contiene il valore corrente del simbolo.

## <a name="syntax"></a>Sintassi

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia supporta la valutazione delle espressioni e deve essere implementata dal motore di debug (DE).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene utilizzata nel processo di valutazione delle espressioni e viene in genere utilizzata nell'implementazione di [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugBinder`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[Associare](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Ottiene il contesto di memoria o l'oggetto che contiene il valore corrente del simbolo.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina il tipo in fase di esecuzione di un oggetto.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Converte la posizione di un oggetto o un indirizzo di memoria in un contesto di memoria.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Ottiene un [oggetto IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) utilizzato per creare i parametri della funzione.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Ottiene il tipo esatto per una variabile.|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia restituisce gli oggetti utilizzati dall'analizzatore di espressioni negli alberi di analisi. L'analizzatore di espressioni analizza un'espressione utilizzando il provider di simboli per convertire i simboli nell'espressione in istanze di [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), che descrivono ogni simbolo in termini di tipo e posizione nel codice sorgente. Il [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) metodo `IDebugField` converte gli oggetti [in IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetti che connettono o associano un tipo di simbolo a un valore effettivo in memoria. Questi `IDebugObject` oggetti vengono quindi archiviati in un albero di analisi per una valutazione successiva.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
