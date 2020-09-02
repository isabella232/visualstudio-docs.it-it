---
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7692a06004a1f9d31a31f91c081c6168d89a8dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694386"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia viene inviata dal motore di debug (DE) al gestore di debug della sessione (SDM) quando viene completata la valutazione dell'espressione asincrona.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il DE implementa questa interfaccia per segnalare il completamento di una valutazione di un'espressione avviata da una chiamata a [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM utilizza [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) per accedere all' `IDebugEvent2` interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Il DE crea e invia questo oggetto evento per segnalare il completamento della valutazione di un'espressione. L'evento viene inviato tramite la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IDebugExpressionEvaluationCompleteEvent2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Ottiene l'espressione originale.|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Ottiene il risultato della valutazione dell'espressione.|  
  
## <a name="remarks"></a>Osservazioni  
 Il DE deve inviare questo evento, indipendentemente dal fatto che la valutazione abbia avuto esito positivo o negativo.  
  
 Se la valutazione ha esito negativo, `DEBUG_PROPINFO_VALUE` i `DEBUG_PROPINFO_ATTRIB` flag e non verranno impostati nella struttura [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) restituita da [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (l'oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) viene creato da de e restituito nell' `IDebugExpressionEvaluationCompleteEvent2` evento se la valutazione non riesce).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
