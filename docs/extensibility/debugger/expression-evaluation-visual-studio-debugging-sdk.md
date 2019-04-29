---
title: Valutazione delle espressioni (Visual Studio Debugging SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b100ccac042aeed3ed8211c56fc1129311d850b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889853"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Expression evaluation (Visual Studio Debugging SDK)
Durante la modalità di interruzione, l'IDE deve valutare espressioni semplici che interessa diverse variabili di programma. Per portare a termine la sua valutazione, il motore di debug (DE) deve analizzare e valutare un'espressione che viene immesso in una delle finestre dell'IDE.

 Le espressioni vengono create con il [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metodo e rappresentati da risultante [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia.

 Il **IDebugExpression2** interfaccia viene implementata per la Germania e chiama relativo **EvalAsync** metodo restituisca un' [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia all'IDE, per visualizzare il risultati della valutazione dell'espressione nell'IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) restituisce una struttura che consente di inserire il valore di un'espressione in un **Watch** finestra o nel **variabili locali** finestra.

 Gestione del debug del pacchetto o sessione di debug (SDM) chiama [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) oppure [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per ottenere un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta il risultato della valutazione. `IDebugProperty2` dispone di metodi che restituiscono il nome, tipo e valore dell'espressione. Queste informazioni vengono visualizzate nelle varie finestre del debugger.

## <a name="using-expression-evaluation"></a>Tramite valutazione dell'espressione
 Per usare la valutazione dell'espressione, è necessario implementare il [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metodo e tutti i metodi delle [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia, come illustrato nella tabella seguente.

|Metodo|Descrizione|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Valuta un'espressione in modo asincrono.|
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina la valutazione dell'espressione asincrona.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Valuta un'espressione in modo sincrono.|

 Valutazione sincrona e asincrona necessaria implementa il [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (metodo). Valutazione delle espressioni asincrone richiede l'implementazione di [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Vedere anche
- [Valutazione di controllo e lo stato di esecuzione](../../extensibility/debugger/execution-control-and-state-evaluation.md)