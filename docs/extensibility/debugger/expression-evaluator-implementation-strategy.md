---
title: Strategia di implementazione dell'analizzatore di espressioni Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3922689c20c839b3c0c2b2440bc9fefd5d25c80a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738677"
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategia di implementazione del valutatore di espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Un approccio per creare rapidamente un analizzatore di espressioni (EE) consiste nell'implementare prima il codice minimo necessario per visualizzare le variabili locali nella finestra **Variabili locali.** È utile tenere presente che ogni riga nella finestra **Variabili locali** visualizza il nome, il tipo e il valore di una variabile locale e che tutte e tre sono rappresentate da un [oggetto IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md) Il nome, il tipo e il valore `IDebugProperty2` di una variabile locale vengono ottenuti da un oggetto chiamando il relativo metodo [GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Per ulteriori informazioni su come visualizzare le variabili locali nella finestra **Variabili locali,** consultate [Visualizzazione delle variabili locali.](../../extensibility/debugger/displaying-locals.md)

## <a name="discussion"></a>Discussione
 Una possibile sequenza di implementazione inizia con l'implementazione di [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). I metodi [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) e [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) devono essere implementati per visualizzare le variabili locali. La `IDebugExpressionEvaluator::GetMethodProperty` chiamata `IDebugProperty2` restituisce un oggetto che rappresenta un metodo, ovvero un [oggetto IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) I metodi stessi non vengono visualizzati nella finestra **Variabili locali.**

 Il [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metodo deve essere implementato successivamente. Il motore di debug (DE) chiama questo metodo per `IDebugProperty2::EnumChildren` ottenere `guidFilter` un `guidFilterLocalsPlusArgs`elenco di variabili e argomenti locali passando un argomento di . `IDebugProperty2::EnumChildren`chiama [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) ed [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinando i risultati in un'unica enumerazione. Per ulteriori dettagli, vedere [Visualizzare la variabilile locali.](../../extensibility/debugger/displaying-locals.md)

## <a name="see-also"></a>Vedere anche
- [Implementare un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Visualizza gente del posto](../../extensibility/debugger/displaying-locals.md)
