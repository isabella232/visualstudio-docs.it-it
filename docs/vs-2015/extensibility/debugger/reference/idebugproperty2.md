---
title: IDebugProperty2 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c728c2e4955d35e2954fbda0a4a4432c550666d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531564"
---
# <a name="idebugproperty2"></a>IDebugProperty2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugProperty2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty2).  
  
Questa interfaccia rappresenta una proprietà frame dello stack, una proprietà del documento programma o un'altra proprietà. La proprietà è in genere il risultato della valutazione di un'espressione.  
  
> [!NOTE]
>  Questo uso di "property" non deve essere confuso con tale vale a dire una variabile membro di una classe, anche se un `IDebugProperty2` può rappresentare tale entità.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per rappresentare un particolare tipo di valore. Ad esempio, il valore può essere un valore numerico come risultato di valutazione di un'espressione, un contesto di memoria utilizzata per la visualizzazione di memoria o un elenco di registri e i relativi valori.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oppure [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere questa interfaccia, che rappresenta il risultato di una versione di valutazione. `IDebugExpression2::EvaluateAsync` Restituisce questa interfaccia per l'invio di un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfaccia per il modello SDM, che a sua volta chiama [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) per recuperare la proprietà.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) restituisce questa interfaccia per fornire il documento di script associati.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) restituisce questa interfaccia per rappresentare il valore restituito di una funzione.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) restituisce questa interfaccia per rappresentare diverse proprietà del programma, ad esempio un nome o un contesto in memoria.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) restituisce questa interfaccia per rappresentare diverse proprietà del frame dello stack, ad esempio le variabili locali.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProperty2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Viene compilato un [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struttura che descrive una proprietà.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Imposta il valore di una proprietà da una stringa.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Imposta il valore della proprietà dal valore di un riferimento specificato.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Enumera gli elementi figlio di una proprietà.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Restituisce l'elemento padre di una proprietà.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Restituisce la proprietà che descrivono la proprietà più derivato di una proprietà.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Restituisce i byte di memoria che compongono il valore di una proprietà.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Restituisce il contesto di memoria per un valore della proprietà.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Restituisce la dimensione, espressa in byte, del valore della proprietà.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Restituisce un riferimento al valore di questa proprietà.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Restituisce le informazioni estese di una proprietà.|  
  
## <a name="remarks"></a>Note  
 Una proprietà, come rappresentato da un `IDebugProperty2` interfaccia, può essere considerato un valore con un nome, un tipo e un indirizzo. In termini più generali, un `IDebugProperty2` può rappresentare qualsiasi elemento che ha una struttura gerarchica, con gli elementi padre e nodi figlio.  
  
 È in genere transitoria, che durano solo fino a quando lo stack frame corrente, ad esempio una proprietà. D'altra parte, un riferimento, come rappresentato da un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interfaccia, viene mantenuto fino a quando il valore rimane in memoria.  
  
 L'IDE può utilizzare il `IDebugProperty2` interfaccia per consentire agli utenti di esplorare e modificare le proprietà in fase di esecuzione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

