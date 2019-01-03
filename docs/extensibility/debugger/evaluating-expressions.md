---
title: La valutazione di espressioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7df128995c114c724c7a25ebe4949be935a3c496
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53929737"
---
# <a name="evaluate-expressions"></a>Valutare le espressioni
Le espressioni vengono create dalle stringhe passate dal **Auto**, **Watch**, **controllo immediato**, oppure **immediato** windows. Quando viene valutata un'espressione, viene generata una stringa stampabile che contiene il nome e il tipo di variabile o argomento e il relativo valore. Questa stringa viene visualizzata nella finestra dell'IDE corrispondente.  
  
## <a name="implementation"></a>Implementazione  
 Le espressioni vengono valutate quando un programma viene arrestata in corrispondenza di un punto di interruzione. L'espressione stessa è rappresentata da un' [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia che rappresenta un'espressione analizzata che è pronta per l'associazione e di valutazione all'interno del contesto di valutazione di espressione specificata. Lo stack frame determina il contesto di valutazione di espressioni, che fornisce il motore di debug (DE) implementando la [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia.  
  
 Data una stringa di utente e un [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia, un motore di debug (DE) può ottenere un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia passando la stringa di utente per il [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) (metodo). L'interfaccia IDebugExpression2 restituita contiene l'espressione analizzata pronto per la valutazione.  
  
 Con il `IDebugExpression2` interfaccia, la Germania possa ottenere il valore dell'espressione tramite valutazione dell'espressione sincrone o asincrone, usando [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Questo valore, insieme al nome e tipo della variabile o argomento, viene inviato all'IDE per la visualizzazione. Il valore di nome e tipo sono rappresentate da un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia.  
  
 Per abilitare la valutazione dell'espressione, è necessario implementare un CRI il [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfacce. Valutazione sincrona e asincrona è necessaria l'implementazione del [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [Stack frame](../../extensibility/debugger/stack-frames.md)   
 [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md)   
 [Eseguire il debug di attività](../../extensibility/debugger/debugging-tasks.md)