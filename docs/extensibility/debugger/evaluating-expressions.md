---
title: Valutazione delle espressioni Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18e342704cbb4abd7de9667576ce331ef8fbf60a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738824"
---
# <a name="evaluate-expressions"></a>Valutare le espressioni
Le espressioni vengono create da stringhe passate dalle finestre **Autos**, **Watch**, **QuickWatch**o **Immediate** . Quando un'espressione viene valutata, genera una stringa stampabile che contiene il nome e il tipo della variabile o dell'argomento e il relativo valore. Questa stringa viene visualizzata nella finestra dell'IDE corrispondente.

## <a name="implementation"></a>Implementazione
 Le espressioni vengono valutate quando un programma si è arrestato in corrispondenza di un punto di interruzione. L'espressione stessa è rappresentata da un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia, che rappresenta un'espressione analizzata che è pronto per l'associazione e la valutazione all'interno del contesto di valutazione dell'espressione specificato. Lo stack frame determina il contesto di valutazione dell'espressione, che il motore di debug (DE) fornisce implementando il [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia.

 Dato una stringa utente e un [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia, un motore di debug (DE) può ottenere un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia passando la stringa utente per il [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metodo. Il IDebugExpression2 interfaccia restituita contiene l'espressione analizzata pronta per la valutazione.

 Con `IDebugExpression2` l'interfaccia, il DE può ottenere il valore dell'espressione tramite la valutazione sincrona o asincrona dell'espressione, utilizzando [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Questo valore, insieme al nome e al tipo della variabile o dell'argomento, viene inviato all'IDE per la visualizzazione. Il valore, il nome e il tipo sono rappresentati da un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia.

 Per abilitare la valutazione delle espressioni, un DE deve implementare il [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfacce. Sia la valutazione sincrona che la valutazione asincrona richiedono l'implementazione del [metodo IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)

## <a name="see-also"></a>Vedere anche
- [Stack frame](../../extensibility/debugger/stack-frames.md)
- [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
