---
title: IDebugFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6433c1f2c540b040a3b3beccc264377e69592387
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728496"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia rappresenta una funzione.

## <a name="syntax"></a>Sintassi

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare una funzione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia è una specializzazione dell'interfaccia [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ed è ottenuta utilizzando [QueryInterface](/cpp/atl/queryinterface) sull' `IDebugObject` interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), l' `IDebugFunctionObject` interfaccia espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Crea un oggetto dati primitivo.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Crea un oggetto usando un costruttore.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Crea un oggetto senza costruttore.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Crea un oggetto Array.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Crea un oggetto String.|
|[Valuta](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Chiama la funzione e restituisce il valore risultante come un oggetto.|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia consente all'analizzatore di espressioni di rappresentare le funzioni in un albero di analisi. I `Create` metodi in questa interfaccia vengono usati per costruire oggetti che rappresentano i parametri di input per il metodo. La funzione può quindi essere eseguita chiamando il metodo [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) , che restituisce un oggetto che rappresenta il valore restituito della funzione.

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
