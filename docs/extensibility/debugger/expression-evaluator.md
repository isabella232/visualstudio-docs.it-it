---
title: Analizzatore di espressioni | Microsoft Docs
description: Informazioni sugli analizzatori di espressioni, che esaminano la sintassi di un linguaggio per analizzare e valutare variabili ed espressioni in fase di esecuzione in modalità di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 998f361d8008257cb8f4a888b4d4fbb985c9c977
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900980"
---
# <a name="expression-evaluator"></a>Analizzatore di espressioni
Gli analizzatori di espressioni esaminano la sintassi di un linguaggio per analizzare e valutare variabili ed espressioni in fase di esecuzione, consentendone la visualizzazione da parte dell'utente quando l'IDE è in modalità di interruzione.

## <a name="use-expression-evaluators"></a>Usare gli analizzatori di espressioni
 Le espressioni vengono create usando [il metodo ParseText,](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) come indicato di seguito:

1. Il motore di debug implementa [l'interfaccia IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

2. Il pacchetto di debug ottiene un `IDebugExpressionContext2` oggetto da un'interfaccia [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) e quindi chiama il metodo su di esso per `IDebugStackFrame2::ParseText` ottenere un oggetto [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md)

3. Il pacchetto di debug chiama [il metodo EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [il metodo EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere il valore dell'espressione. `IDebugExpression2::EvaluateAsync` viene chiamato dalla finestra comando/controllo immediato. Tutti gli altri componenti dell'interfaccia utente chiamano `IDebugExpression2::EvaluateSync` .

4. Il risultato della valutazione dell'espressione è un oggetto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che contiene il nome, il tipo e il valore del risultato della valutazione dell'espressione.

   Durante la valutazione dell'espressione, EE richiede informazioni dal componente del provider di simboli. Il provider di simboli fornisce le informazioni simboliche utilizzate per identificare e comprendere l'espressione analizzata.

   Al termine della valutazione asincrona dell'espressione, il responsabile della valutazione delle espressioni invia un evento asincrono tramite gestione debug sessione (SDM) per notificare all'IDE che la valutazione delle espressioni è stata completata. Il risultato della valutazione viene quindi restituito dalla chiamata al `IDebugExpression2::EvaluateSync` metodo .

## <a name="implementation-notes"></a>Note sull'implementazione
 I [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug prevedono di parlare con l'analizzatore di espressioni usando interfacce CLR (Common Language Runtime). Di conseguenza, un analizzatore di espressioni che funziona con i motori di debug deve supportare CLR . Un elenco completo di tutte le interfacce di debug CLR è disponibile in debugref.doc, che fa parte di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

## <a name="see-also"></a>Vedere anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
