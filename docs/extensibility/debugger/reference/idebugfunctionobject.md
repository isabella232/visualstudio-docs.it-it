---
description: Questa interfaccia rappresenta una funzione.
title: Interfaccia IDebugFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 11f344111565263a30e0f20d44309392211873c1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138185"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [Clr Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia rappresenta una funzione.

## <a name="syntax"></a>Sintassi

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare una funzione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia è una specializzazione [dell'interfaccia IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) e viene ottenuta usando [QueryInterface](/cpp/atl/queryinterface) nell'interfaccia `IDebugObject` .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugFunctionObject` l'interfaccia espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Crea un oggetto dati primitivo.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Crea un oggetto utilizzando un costruttore.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Crea un oggetto senza costruttore.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Crea un oggetto matrice.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Crea un oggetto stringa.|
|[Valuta](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Chiama la funzione e restituisce il valore risultante come oggetto .|

## <a name="remarks"></a>Commenti
 Questa interfaccia consente all'analizzatore di espressioni di rappresentare le funzioni in un albero di analisi. I `Create` metodi in questa interfaccia vengono usati per costruire oggetti che rappresentano i parametri di input per il metodo . La funzione può quindi essere eseguita chiamando il [metodo Evaluate,](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) che restituisce un oggetto che rappresenta il valore restituito della funzione.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
