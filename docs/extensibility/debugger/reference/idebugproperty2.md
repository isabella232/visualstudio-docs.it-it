---
description: Questa interfaccia rappresenta una stack frame, una proprietà del documento di programma o un'altra proprietà.
title: Interfaccia IDebugProperty2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 7a368969251eb4f47746a1cb56491cf8f0dcf3d63664835177ea690b3ecab2b6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121306998"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Questa interfaccia rappresenta una stack frame, una proprietà del documento di programma o un'altra proprietà. La proprietà è in genere il risultato di una valutazione dell'espressione.

> [!NOTE]
> Questo uso di "proprietà" non deve essere confuso con ciò che significa una variabile membro di una classe, anche se un può `IDebugProperty2` rappresentare tale entità.

## <a name="syntax"></a>Sintassi

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 De implementa questa interfaccia per rappresentare un particolare tipo di valore. Ad esempio, il valore potrebbe essere un valore numerico come risultato di una valutazione dell'espressione, un contesto di memoria usato per la visualizzazione della memoria o un elenco di registri e dei relativi valori.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere questa interfaccia, che rappresenta il risultato di una valutazione. `IDebugExpression2::EvaluateAsync` restituisce questa interfaccia inviando [un'interfaccia IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) a SDM, che a sua volta chiama [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) per recuperare la proprietà.

- [GetDebugProperty restituisce](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) questa interfaccia per fornire il documento di script associato.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) restituisce questa interfaccia per rappresentare il valore restituito di una funzione.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) restituisce questa interfaccia per rappresentare varie proprietà del programma, ad esempio un nome o un contesto di memoria.

- [GetDebugProperty restituisce](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) questa interfaccia per rappresentare varie proprietà del stack frame, ad esempio le variabili locali.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugProperty2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Compila una struttura [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) che descrive una proprietà.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Imposta il valore di una proprietà da una stringa.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Imposta il valore della proprietà dal valore di un riferimento specificato.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Enumera gli elementi figlio di una proprietà.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Restituisce l'elemento padre di una proprietà.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Restituisce la proprietà che descrive la proprietà più derivata di una proprietà.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Restituisce i byte di memoria che costituiscono il valore di una proprietà.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Restituisce il contesto di memoria per un valore di proprietà.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Restituisce la dimensione, in byte, del valore della proprietà.|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Restituisce un riferimento al valore di questa proprietà.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Restituisce le informazioni estese di una proprietà.|

## <a name="remarks"></a>Commenti
 Una proprietà, rappresentata da un'interfaccia, può essere pensata come un valore con un nome, un `IDebugProperty2` tipo e un indirizzo. In termini più generali, un oggetto può rappresentare qualsiasi elemento con una struttura `IDebugProperty2` gerarchica, con elementi padre e nodi figlio.

 Una proprietà è in genere transitoria, durevole solo fino a quando il stack frame, ad esempio. D'altra parte, un riferimento, come rappresentato da [un'interfaccia IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) dura fino a quando il valore rimane in memoria.

 L'IDE può usare `IDebugProperty2` l'interfaccia per consentire agli utenti di esplorare e modificare le proprietà in fase di esecuzione.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
