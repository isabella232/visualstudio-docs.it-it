---
title: Valutazione delle espressioni | Microsoft Docs
description: Informazioni sulla valutazione delle espressioni create dalle stringhe passate dalle finestre Auto, Espressione di controllo, Controllo immediato o Controllo immediato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 7fd3f27aaf6080a853dbacc856d0b6ac258319b81560bd002a5b562ecef6a7dc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342843"
---
# <a name="evaluate-expressions"></a>Valutare le espressioni
Le espressioni vengono create dalle stringhe passate dalle **finestre Auto**, **Espressione di** controllo , **Controllo** immediato **o Controllo** immediato . Quando un'espressione viene valutata, genera una stringa stampabile che contiene il nome e il tipo della variabile o dell'argomento e il relativo valore. Questa stringa viene visualizzata nella finestra IDE corrispondente.

## <a name="implementation"></a>Implementazione
 Le espressioni vengono valutate quando un programma viene arrestato in corrispondenza di un punto di interruzione. L'espressione stessa è rappresentata da un'interfaccia [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) che rappresenta un'espressione analizzata pronta per l'associazione e la valutazione all'interno del contesto di valutazione dell'espressione specificato. Il stack frame determina il contesto di valutazione dell'espressione fornito dal motore di debug implementando [l'interfaccia IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

 Data una stringa utente e un'interfaccia [IDebugExpressionContext2,](../../extensibility/debugger/reference/idebugexpressioncontext2.md) un motore di debug (DE) può ottenere [un'interfaccia IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) passando la stringa utente al metodo [IDebugExpressionContext2::P arseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) L'interfaccia IDebugExpression2 restituita contiene l'espressione analizzata pronta per la valutazione.

 Con l'interfaccia , DE può ottenere il valore dell'espressione tramite la valutazione sincrona o asincrona dell'espressione, usando `IDebugExpression2` [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Questo valore, insieme al nome e al tipo della variabile o dell'argomento, viene inviato all'IDE per la visualizzazione. Il valore, il nome e il tipo sono rappresentati da [un'interfaccia IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md)

 Per abilitare la valutazione delle espressioni, un DE deve implementare [le interfacce IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md) La valutazione sincrona e asincrona richiedono l'implementazione del [metodo IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)

## <a name="see-also"></a>Vedi anche
- [Stack frame](../../extensibility/debugger/stack-frames.md)
- [Contesto di valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-context.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
