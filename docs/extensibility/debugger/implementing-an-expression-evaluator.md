---
title: Implementazione di un analizzatore di espressioni . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8c7c9a1130794dd4c28f212afd6cb3c030f5a1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738549"
---
# <a name="implement-an-expression-evaluator"></a>Implementare un analizzatore di espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 La valutazione di un'espressione è un'interazione complessa tra il motore di debug (DE), il provider di simboli (SP), l'oggetto binder e l'analizzatore di espressioni (EE). Questi quattro componenti sono connessi da interfacce implementate da un componente e utilizzate da un altro.

 L'analizzatore di Espressioni accetta un'espressione dal DE sotto forma di stringa e la analizza o la valuta. EE esegue le seguenti interfacce, che vengono utilizzate dal DE:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  L'analizzatore di oggetti e , fornito dal DE, per ottenere il valore di simboli e oggetti. EE utilizza le seguenti interfacce, che vengono implementate dal DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE esegue [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2`fornisce il meccanismo per descrivere il risultato di una valutazione dell'espressione, ad esempio una variabile locale, una primitiva o un oggetto in Visual Studio, che visualizza quindi le informazioni appropriate nella finestra **Variabili locali**, Espressioni di **controllo**o **Immediata** .

  L'SP viene fornito all'EE dal DE quando richiede informazioni. SP esegue interfacce che descrivono gli indirizzi e i campi, ad esempio le interfacce seguenti e i relativi derivati:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE utilizza tutte queste interfacce.

## <a name="in-this-section"></a>Contenuto della sezione
 [Strategia di implementazione del valutatore di espressioni](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Definisce un processo in tre fasi per la strategia di implementazione dell'analizzatore di espressioni (EE).

## <a name="see-also"></a>Vedere anche
- [Scrittura di un analizzatore di espressioni CLRWriting a CLR expression evaluator](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
