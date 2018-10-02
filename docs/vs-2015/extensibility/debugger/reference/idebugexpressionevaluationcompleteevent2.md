---
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
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
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 166e9a7d9c2be76dbaf677bfa08aa1dfe1351a1a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540914"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugExpressionEvaluationCompleteEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2).  
  
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di sessione di debug (SDM) quando la valutazione dell'espressione asincrona è stata completata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per il completamento di report di valutazione di un'espressione avviato da una chiamata a [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata per lo stesso oggetto di questa interfaccia. Usa il modello SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) per l'accesso di `IDebugEvent2` interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento per segnalare il completamento della valutazione di un'espressione. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito per il modello SDM quando associato al programma in fase di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugExpressionEvaluationCompleteEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Ottiene l'espressione originale.|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Ottiene il risultato della valutazione dell'espressione.|  
  
## <a name="remarks"></a>Note  
 La Germania deve inviare questo evento, se la versione di valutazione esito positivo o negativo.  
  
 Se la versione di valutazione non eseguita correttamente, il `DEBUG_PROPINFO_VALUE` e `DEBUG_PROPINFO_ATTRIB` flag non verranno impostati [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struttura restituito da [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (il [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto viene creato per la Germania e restituito nella `IDebugExpressionEvaluationCompleteEvent2` evento se la valutazione non riuscita).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

