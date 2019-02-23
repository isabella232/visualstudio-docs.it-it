---
title: IDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b5ea1a18495e1660044001b6b4d45de1f07bc3e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680555"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia rappresenta un oggetto che lo strumento di associazione crea per incapsulare i valori dei simboli ed espressioni.

## <a name="syntax"></a>Sintassi

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare un oggetto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia è la classe base per tutti gli oggetti che usa l'analizzatore di espressioni nelle espressioni analizzate. Viene restituito da una chiamata per il [associare](../../../extensibility/debugger/reference/idebugbinder-bind.md) (metodo). [QueryInterface](/cpp/atl/queryinterface) Ottiene le interfacce più specializzate da questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugObject`.

|Metodo|Descrizione|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Ottiene le dimensioni dell'oggetto.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Ottiene il valore dell'oggetto come una serie consecutiva di byte.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Imposta il valore dell'oggetto da una serie consecutiva di byte.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Imposta il valore di riferimento di questo oggetto.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Ottiene il contesto di memoria che rappresenta l'indirizzo del valore dell'oggetto.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Crea una copia dell'oggetto gestito nello spazio degli indirizzi del motore di debug.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Verifica se questo oggetto è un riferimento null.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Confronta un oggetto alla seguente.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Determina se questo oggetto è di sola lettura.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Determina se l'oggetto è un proxy trasparente.|

## <a name="remarks"></a>Note
 L'analizzatore di espressioni usa questa interfaccia come classe base per rappresentare gli oggetti in un albero di analisi.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)