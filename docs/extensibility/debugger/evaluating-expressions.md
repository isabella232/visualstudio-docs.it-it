---
title: Valutazione di espressioni | Microsoft Docs
description: Informazioni sulla valutazione delle espressioni create dalle stringhe passate dalle finestre auto, espressioni di controllo, controllo immediato o immediato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4a9b8db832207eff93e08f123db57b4beef4eb7f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840600"
---
# <a name="evaluate-expressions"></a>Espressioni di valutazione
Le espressioni vengono create dalle stringhe passate dalle finestre **auto**, **espressioni di controllo, controllo** **immediato** o **immediate** . Quando viene valutata un'espressione, viene generata una stringa stampabile che contiene il nome e il tipo di variabile o argomento e il relativo valore. Questa stringa viene visualizzata nella finestra IDE corrispondente.

## <a name="implementation"></a>Implementazione
 Le espressioni vengono valutate quando un programma si arresta in corrispondenza di un punto di interruzione. L'espressione stessa è rappresentata da un'interfaccia [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , che rappresenta un'espressione analizzata pronta per l'associazione e la valutazione all'interno del contesto di valutazione dell'espressione specificato. Il stack frame determina il contesto di valutazione dell'espressione, che il motore di debug (DE) fornisce implementando l'interfaccia [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .

 Data una stringa utente e un'interfaccia [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) , un motore di debug (de) può ottenere un'interfaccia [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) passando la stringa utente al metodo [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . L'interfaccia IDebugExpression2 restituita contiene l'espressione analizzata pronta per la valutazione.

 Con l' `IDebugExpression2` interfaccia, il de può ottenere il valore dell'espressione tramite la valutazione di espressioni sincrone o asincrone, usando [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Questo valore, insieme al nome e al tipo della variabile o dell'argomento, viene inviato all'IDE per la visualizzazione. Il valore, il nome e il tipo sono rappresentati da un'interfaccia [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .

 Per abilitare la valutazione dell'espressione, un DE deve implementare le interfacce [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Per la valutazione sincrona e asincrona è richiesta l'implementazione del metodo [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .

## <a name="see-also"></a>Vedi anche
- [Stack frame](../../extensibility/debugger/stack-frames.md)
- [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
