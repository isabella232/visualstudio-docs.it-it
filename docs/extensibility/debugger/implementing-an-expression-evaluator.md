---
title: Implementazione di un analizzatore di espressioni | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738549"
---
# <a name="implement-an-expression-evaluator"></a>Implementare un analizzatore di espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 La valutazione di un'espressione è un'interazione complessa tra il motore di debug (DE), il provider di simboli (SP), l'oggetto Binder e l'analizzatore di espressioni (EE). Questi quattro componenti sono connessi mediante interfacce implementate da un componente e utilizzate da un altro componente.

 EE accetta un'espressione da DE sotto forma di stringa e la analizza o la valuta. EE esegue le interfacce seguenti, che vengono utilizzate da DE:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE chiama l'oggetto Binder, fornito da DE, per ottenere il valore di simboli e oggetti. EE utilizza le interfacce seguenti, implementate da DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE esegue [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` fornisce il meccanismo per descrivere il risultato della valutazione di un'espressione, ad esempio una variabile locale, una primitiva o un oggetto a Visual Studio, che visualizza quindi le informazioni appropriate nella finestra **variabili locali**, **espressioni di controllo**o nella finestra di **controllo immediato** .

  Il SP viene assegnato all'EE dal DE quando richiede informazioni. SP esegue le interfacce che descrivono gli indirizzi e i campi, ad esempio le interfacce seguenti e i relativi derivati:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE utilizza tutte queste interfacce.

## <a name="in-this-section"></a>Contenuto della sezione
 [Strategia di implementazione dell'analizzatore di espressioni](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Definisce un processo in tre passaggi per la strategia di implementazione dell'analizzatore di espressioni (EE).

## <a name="see-also"></a>Vedere anche
- [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
