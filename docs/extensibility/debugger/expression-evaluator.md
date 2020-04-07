---
title: 'Analizzatore di espressioni : Documenti Microsoft'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738683"
---
# <a name="expression-evaluator"></a>Analizzatore di espressioni
Gli analizzatori di espressioni (EE) esaminano la sintassi di un linguaggio per analizzare e valutare variabili ed espressioni in fase di esecuzione, consentendone la visualizzazione da parte dell'utente quando l'IDE è in modalità di interruzione.

## <a name="use-expression-evaluators"></a>Usare gli analizzatori di espressioniUse expression evaluators
 Le espressioni vengono create utilizzando il metodo [ParseText,](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) come indicato di seguito:Expressions are created using the ParseText method, as follows:

1. Il motore di debug (DE) implementa il [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia.

2. Il pacchetto di `IDebugExpressionContext2` debug ottiene un oggetto da un `IDebugStackFrame2::ParseText` [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia e quindi chiama il metodo su di esso per ottenere un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto.

3. Il pacchetto di debug chiama il metodo [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o il metodo [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere il valore dell'espressione. `IDebugExpression2::EvaluateAsync`viene chiamato dalla finestra Comando/Immediata. Tutti gli altri `IDebugExpression2::EvaluateSync`componenti dell'interfaccia utente chiamano .

4. Il risultato della valutazione dell'espressione è un [oggetto IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che contiene il nome, il tipo e il valore del risultato della valutazione dell'espressione.

   Durante la valutazione dell'espressione, L'analizzatore di Espressioni richiede informazioni dal componente del provider di simboli. Il provider di simboli fornisce le informazioni simboliche utilizzate per identificare e comprendere l'espressione analizzata.

   Al termine della valutazione asincrona dell'espressione, un evento asincrono viene inviato dal DE tramite il gestore di sessione di debug (SDM) per notificare all'IDE che la valutazione dell'espressione è stata completata. E, il risultato della valutazione viene quindi `IDebugExpression2::EvaluateSync` restituito dalla chiamata al metodo.

## <a name="implementation-notes"></a>Note sull'implementazione
 I [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug prevedono di comunicare con l'analizzatore di espressioni utilizzando le interfacce CLR (Common Language Runtime). Di conseguenza, un analizzatore [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di espressioni che funziona con i motori di debug deve supportare CLR (un elenco completo [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]di tutte le interfacce di debug CLR è disponibile in debugref.doc, che fa parte di ).

## <a name="see-also"></a>Vedere anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
