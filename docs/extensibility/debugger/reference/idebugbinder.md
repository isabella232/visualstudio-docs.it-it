---
description: Questa interfaccia associa un campo simbolo, in genere restituito dal provider di simboli, a un contesto di memoria o a un oggetto che contiene il valore corrente del simbolo.
title: Interfaccia IDebugBinder | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 16b18bb8a1208d6f6a9c4a0c87a73f35b66dec1d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072837"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> In Visual Studio 2015 questa modalità di implementazione degli analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Questa interfaccia associa un campo simbolo, in genere restituito dal provider di simboli, a un contesto di memoria o a un oggetto che contiene il valore corrente del simbolo.

## <a name="syntax"></a>Sintassi

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia supporta la valutazione delle espressioni e deve essere implementata dal motore di debug.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene usata nel processo di valutazione delle espressioni e viene in genere usata nell'implementazione di [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) [e EvaluateAsync.](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugBinder` .

|Metodo|Descrizione|
|------------|-----------------|
|[Associare](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Ottiene il contesto di memoria o l'oggetto che contiene il valore corrente del simbolo.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina il tipo di run-time di un oggetto .|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Converte la posizione di un oggetto o un indirizzo di memoria in un contesto di memoria.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Ottiene un [oggetto IDebugFunctionObject usato](../../../extensibility/debugger/reference/idebugfunctionobject.md) per creare i parametri della funzione.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Ottiene il tipo esatto per una variabile.|

## <a name="remarks"></a>Commenti
 Questa interfaccia restituisce gli oggetti utilizzati dall'analizzatore di espressioni negli alberi di analisi. L'analizzatore di espressioni analizza un'espressione usando il provider di simboli per convertire i simboli nell'espressione in istanze di [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md)che descrivono ogni simbolo in termini di tipo e posizione nel codice sorgente. Il [metodo Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) converte gli oggetti in oggetti `IDebugField` [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che si connettono o associano un tipo di simbolo a un valore effettivo in memoria. Questi `IDebugObject` oggetti vengono quindi archiviati in un albero di analisi per una valutazione successiva.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
