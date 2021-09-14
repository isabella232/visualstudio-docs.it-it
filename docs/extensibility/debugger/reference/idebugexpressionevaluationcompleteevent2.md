---
description: Questa interfaccia viene inviata dal motore di debug (DE) a Gestione debug sessione (SDM) al termine della valutazione asincrona delle espressioni.
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f6690c2bd598b0662cc5ef54170726ac8efe99e2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709720"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Questa interfaccia viene inviata dal motore di debug (DE) a Gestione debug sessione (SDM) al termine della valutazione asincrona delle espressioni.

## <a name="syntax"></a>Sintassi

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 De implementa questa interfaccia per segnalare il completamento di una valutazione di espressione avviata da una chiamata a [EvaluateAsync.](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM usa [QueryInterface per](/cpp/atl/queryinterface) accedere all'interfaccia. `IDebugEvent2`

## <a name="notes-for-callers"></a>Note per i chiamanti
 De crea e invia questo oggetto evento per segnalare il completamento di una valutazione dell'espressione. L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma di cui è in corso il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugExpressionEvaluationCompleteEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Ottiene l'espressione originale.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Ottiene il risultato della valutazione dell'espressione.|

## <a name="remarks"></a>Commenti
 De deve inviare questo evento, indipendentemente dal fatto che la valutazione sia riuscita o meno.

 Se la valutazione non riesce, i flag e non verranno impostati nella struttura DEBUG_PROPERTY_INFO restituita da `DEBUG_PROPINFO_VALUE` `DEBUG_PROPINFO_ATTRIB` [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (l'oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) [](../../../extensibility/debugger/reference/debug-property-info.md) viene creato da DE e restituito nell'evento se la valutazione non è `IDebugExpressionEvaluationCompleteEvent2` riuscita).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
