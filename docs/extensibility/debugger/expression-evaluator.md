---
title: Analizzatore di espressioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a477aaceb57e6ccd2eb5125fcf9d8af9be59472b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738683"
---
# <a name="expression-evaluator"></a>Analizzatore di espressioni
Gli analizzatori di espressioni (EE) esaminano la sintassi di un linguaggio per analizzare e valutare variabili ed espressioni in fase di esecuzione, in modo che vengano visualizzate dall'utente quando l'IDE è in modalità di interruzioni.

## <a name="use-expression-evaluators"></a>Usare gli analizzatori di espressioni
 Le espressioni vengono create usando il metodo [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , come indicato di seguito:

1. Il motore di debug (DE) implementa l'interfaccia [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .

2. Il pacchetto di debug ottiene un `IDebugExpressionContext2` oggetto da un'interfaccia [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) e quindi chiama il `IDebugStackFrame2::ParseText` metodo su di esso per ottenere un oggetto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .

3. Il pacchetto di debug chiama il metodo [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o il metodo [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere il valore dell'espressione. `IDebugExpression2::EvaluateAsync` viene chiamato dalla finestra comando/controllo immediato. Tutti gli altri componenti dell'interfaccia utente chiamano `IDebugExpression2::EvaluateSync` .

4. Il risultato della valutazione dell'espressione è un oggetto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , che contiene il nome, il tipo e il valore del risultato della valutazione dell'espressione.

   Durante la valutazione dell'espressione, EE richiede informazioni dal componente del provider di simboli. Il provider di simboli fornisce le informazioni simboliche utilizzate per identificare e comprendere l'espressione analizzata.

   Quando viene completata la valutazione delle espressioni asincrone, un evento asincrono viene inviato da DE tramite Gestione debug sessione (SDM) per notificare all'IDE che la valutazione dell'espressione è stata completata. Il risultato della valutazione viene quindi restituito dalla chiamata al `IDebugExpression2::EvaluateSync` metodo.

## <a name="implementation-notes"></a>Note sull'implementazione
 I [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug si aspettano di comunicare con l'analizzatore di espressioni usando le interfacce CLR (Common Language Runtime). Di conseguenza, un analizzatore di espressioni che interagisce con i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug deve supportare CLR (un elenco completo di tutte le interfacce di debug CLR si trova in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] ).

## <a name="see-also"></a>Vedere anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
