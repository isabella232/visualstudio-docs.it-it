---
title: Analizzatore di espressioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9f990225cbff539281122d21d4773f6611f694f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353757"
---
# <a name="expression-evaluator"></a>Analizzatore di espressioni
Analizzatori di espressioni (EE), esaminare la sintassi di una lingua per analizzare e valutare variabili ed espressioni in fase di esecuzione, consentendo loro di essere visualizzato dall'utente quando l'IDE è in modalità di interruzione.

## <a name="use-expression-evaluators"></a>Usare gli analizzatori di espressioni
 Le espressioni vengono create usando il [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) (metodo), come indicato di seguito:

1. Il motore di debug (DE) implementa il [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia.

2. Ottiene il pacchetto di debug un' `IDebugExpressionContext2` dell'oggetto da un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia e quindi chiama il `IDebugStackFrame2::ParseText` metodo su di essa per ottenere un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto.

3. Le chiamate di debug del pacchetto di [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) metodo o il [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metodo per ottenere il valore dell'espressione. `IDebugExpression2::EvaluateAsync` viene chiamato dalla finestra di comando/controllo immediato. Tutti gli altri componenti dell'interfaccia utente chiamano `IDebugExpression2::EvaluateSync`.

4. Il risultato della valutazione dell'espressione è un' [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che contiene il nome, tipo e valore del risultato della valutazione dell'espressione.

   Durante la valutazione dell'espressione, l'analizzatore di Espressioni richiede informazioni dal componente di provider di simboli. Il provider di simboli fornisce le informazioni sui simboli usate per identificare e comprendere l'espressione analizzata.

   Al termine della valutazione dell'espressione asincrona, viene inviato un evento asincrono per la Germania tramite Gestore di sessione di debug (SDM) per notificare all'IDE che la valutazione dell'espressione è stata completata. E, il risultato della valutazione viene quindi restituito dalla chiamata al `IDebugExpression2::EvaluateSync` (metodo).

## <a name="implementation-notes"></a>Note di implementazione
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug che prevede di comunicare con l'analizzatore di espressioni utilizzando le interfacce di Common Language Runtime (CLR). Di conseguenza, un analizzatore di espressioni che interagisce con il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug devono supportare Common Language Runtime (un elenco completo di tutte le interfacce di debug di CLR è reperibile in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).

## <a name="see-also"></a>Vedere anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)