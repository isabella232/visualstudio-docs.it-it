---
title: Valutazione di espressioni (SDK per il debug di Visual Studio) | Microsoft Docs
description: Durante la modalità di rottura, l'IDE valuta le espressioni che coinvolgono variabili di programma. Informazioni sul modo in cui il motore di debug analizza e valuta un'espressione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 772d38b328eca1e0afb6ff48a5ad580d01939527
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921480"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Valutazione di espressioni (Visual Studio Debugging SDK)
Durante la modalità di rottura, l'IDE deve valutare espressioni semplici che coinvolgono diverse variabili di programma. Per eseguire la valutazione, il motore di debug (DE) deve analizzare e valutare un'espressione immessa in una delle finestre dell'IDE.

 Le espressioni vengono create con il metodo [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e rappresentate dall'interfaccia [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) risultante.

 L'interfaccia **IDebugExpression2** viene implementata da de e chiama il relativo metodo **EvalAsync** per restituire un'interfaccia [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) all'IDE, in modo da visualizzare i risultati della valutazione dell'espressione nell'IDE. [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) restituisce una struttura utilizzata per inserire il valore di un'espressione in una finestra **espressioni di controllo** o nella finestra **variabili locali** .

 Il pacchetto di debug o il gestore di debug della sessione (SDM) chiama [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per ottenere un'interfaccia [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta il risultato della valutazione. `IDebugProperty2` dispone di metodi che restituiscono il nome, il tipo e il valore dell'espressione. Queste informazioni vengono visualizzate in diverse finestre del debugger.

## <a name="using-expression-evaluation"></a>Uso della valutazione delle espressioni
 Per usare la valutazione delle espressioni, è necessario implementare il metodo [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e tutti i metodi dell'interfaccia [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , come illustrato nella tabella seguente.

|Metodo|Descrizione|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Valuta un'espressione in modo asincrono.|
|[Interruzione](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina la valutazione dell'espressione asincrona.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Valuta un'espressione in modo sincrono.|

 Per la valutazione sincrona e asincrona è necessario implementare il metodo [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Per la valutazione di espressioni asincrone è necessaria l'implementazione di [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Vedi anche
- [Controllo di esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
