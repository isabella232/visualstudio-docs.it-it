---
description: Questa interfaccia rappresenta un'espressione analizzata pronta per l'associazione e la valutazione.
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e9f9772b808181a0049d335bc850faaecacdadf5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088991"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Questa interfaccia rappresenta un'espressione analizzata pronta per l'associazione e la valutazione.

## <a name="syntax"></a>Sintassi

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per rappresentare un'espressione analizzata pronta per la valutazione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) restituisce questa interfaccia. [GetExpressionContext restituisce](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) [l'interfaccia IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Queste interfacce sono accessibili solo quando il programma in fase di debug è stato sospeso ed è stack frame disponibile un programma.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugExpression2` .

|Metodo|Descrizione|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Valuta questa espressione in modo asincrono.|
|[Interrompere](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina la valutazione asincrona dell'espressione.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Valuta questa espressione in modo sincrono.|

## <a name="remarks"></a>Commenti
 Quando un programma si arresta, gestione debug sessione (SDM) ottiene un stack frame da DE con una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). SDM chiama quindi [GetExpressionContext per](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) ottenere l'interfaccia [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Questa operazione è seguita da una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per creare l'interfaccia , che rappresenta `IDebugExpression2` l'espressione analizzata pronta per la valutazione.

 SDM chiama [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync per](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) valutare effettivamente l'espressione e produrre un valore.

 In un'implementazione di , de usa la funzione di COM per creare un'istanza di un analizzatore di espressioni e ottenere `IDebugExpressionContext2::ParseText` `CoCreateInstance` [un'interfaccia IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) (vedere l'esempio nell'interfaccia `IDebugExpressionEvaluator` ). De chiama quindi [Parse per](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) ottenere [un'interfaccia IDebugParsedExpression.](../../../extensibility/debugger/reference/idebugparsedexpression.md) Questa interfaccia viene utilizzata nell'implementazione `IDebugExpression2::EvaluateSync` di e per eseguire la `IDebugExpression2::EvaluateAsync` valutazione.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
