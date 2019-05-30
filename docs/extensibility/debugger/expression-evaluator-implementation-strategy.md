---
title: Strategia di implementazione dell'analizzatore di espressioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee0842f8375faeca7e715d4b20c73ca13598dbc3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353746"
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategia di implementazione dell'analizzatore di espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [esempio analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Uno degli approcci per creare rapidamente un analizzatore di espressioni (EE) consiste nell'implementare prima di tutto il codice minimo necessario per visualizzare variabili locali all'interno di **variabili locali** finestra. È utile tenere presente che in ogni riga i **variabili locali** finestra viene visualizzato il nome, tipo e valore di una variabile locale e che tutti e tre sono rappresentati da un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto. Il nome, tipo e valore di una variabile locale viene ottenuto da un' `IDebugProperty2` chiamando relativi [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (metodo). Per altre informazioni su come visualizzare variabili locali all'interno di **variabili locali** finestra, vedere [variabili locali di visualizzazione](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Discussione
 Una sequenza di implementazione possibili inizia con l'implementazione [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Il [analizzare](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) e il [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) devono essere implementati i metodi per visualizzare variabili locali. La chiamata `IDebugExpressionEvaluator::GetMethodProperty` restituisce un `IDebugProperty2` oggetto che rappresenta un metodo: vale a dire una [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) oggetto. Metodi stessi non vengono visualizzati nei **variabili locali** finestra.

 Il [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metodo deve essere implementato successivamente. Il motore di debug (DE) chiama questo metodo per ottenere un elenco di argomenti e variabili locali, passando `IDebugProperty2::EnumChildren` una `guidFilter` argomento di `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` le chiamate [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) e [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinare i risultati in un'unica enumerazione. Visualizzare [visualizzare variabili locali](../../extensibility/debugger/displaying-locals.md) per altri dettagli.

## <a name="see-also"></a>Vedere anche
- [Implementare un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Variabili locali di visualizzazione](../../extensibility/debugger/displaying-locals.md)