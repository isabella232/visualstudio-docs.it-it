---
title: Valutazione delle espressioni (Visual Studio Debugging SDK) | Microsoft Docs
description: Durante la modalità di interruzione, l'IDE valuta le espressioni che coinvolgono variabili di programma. Informazioni su come il motore di debug analizza e valuta un'espressione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3c362b03dd6da91630b324fd659f0977c15a96c0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043583"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Valutazione delle espressioni (Visual Studio Debugging SDK)
Durante la modalità di interruzione, l'IDE deve valutare espressioni semplici che coinvolgono diverse variabili di programma. Per eseguire la valutazione, il motore di debug deve analizzare e valutare un'espressione immessa in una delle finestre dell'IDE.

 Le espressioni vengono create con il [metodo IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e rappresentate dall'interfaccia [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) risultante.

 **L'interfaccia IDebugExpression2** viene implementata dal de e chiama il relativo metodo **EvalAsync** per restituire un'interfaccia [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) all'IDE, in modo da visualizzare i risultati della valutazione dell'espressione nell'IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) restituisce una struttura usata per inserire il valore di un'espressione in una finestra **Espressione** di controllo o nella **finestra** Variabili locali.

 Il pacchetto di debug o la gestione del debug di sessione (SDM) chiama [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per ottenere [un'interfaccia IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta il risultato della valutazione. `IDebugProperty2` dispone di metodi che restituiscono il nome, il tipo e il valore dell'espressione. Queste informazioni vengono visualizzate in diverse finestre del debugger.

## <a name="using-expression-evaluation"></a>Uso della valutazione delle espressioni
 Per usare la valutazione delle espressioni, è necessario implementare il metodo [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e tutti i metodi dell'interfaccia [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) come illustrato nella tabella seguente.

|Metodo|Descrizione|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Valuta un'espressione in modo asincrono.|
|[Interrompere](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina la valutazione asincrona delle espressioni.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Valuta un'espressione in modo sincrono.|

 La valutazione sincrona e asincrona richiede l'implementazione del [metodo IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) La valutazione asincrona delle espressioni richiede [l'implementazione di IDebugExpressionEvaluationCompleteEvent2.](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)

## <a name="see-also"></a>Vedi anche
- [Controllo di esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
