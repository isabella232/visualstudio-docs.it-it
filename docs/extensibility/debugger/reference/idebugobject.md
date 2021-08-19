---
description: Questa interfaccia rappresenta un oggetto creato dal binder per incapsulare i valori di simboli ed espressioni.
title: Interfaccia IDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 8d7fdb6e4cbb3a5491a34f404bc7c903de85a147
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133107"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [Clr Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia rappresenta un oggetto creato dal binder per incapsulare i valori di simboli ed espressioni.

## <a name="syntax"></a>Sintassi

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare un oggetto .

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia è la classe di base per tutti gli oggetti utilizzati dall'analizzatore di espressioni nelle espressioni analizzate. Viene restituito da una chiamata al [metodo Bind.](../../../extensibility/debugger/reference/idebugbinder-bind.md) [QueryInterface](/cpp/atl/queryinterface) ottiene le interfacce più specializzate da questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugObject` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Ottiene le dimensioni dell'oggetto .|
|[Getvalue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Ottiene il valore dell'oggetto come una serie consecutiva di byte.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Imposta il valore dell'oggetto da una serie consecutiva di byte.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Imposta il valore di riferimento di questo oggetto.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Ottiene il contesto di memoria che rappresenta l'indirizzo del valore dell'oggetto .|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Crea una copia dell'oggetto gestito nello spazio indirizzi del motore di debug.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Verifica se questo oggetto è un riferimento Null.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Confronta un oggetto con questo oggetto .|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Determina se questo oggetto è di sola lettura.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Determina se l'oggetto è un proxy trasparente.|

## <a name="remarks"></a>Commenti
 L'analizzatore di espressioni usa questa interfaccia come classe di base per rappresentare gli oggetti in un albero di analisi.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Associare](../../../extensibility/debugger/reference/idebugbinder-bind.md)
