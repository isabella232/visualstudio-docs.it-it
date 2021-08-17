---
title: Implementazione di un analizzatore di espressioni | Microsoft Docs
description: Informazioni sulla valutazione di un'espressione, che include il motore di debug, il provider di simboli, l'oggetto binder e l'analizzatore di espressioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 19c07363ee9e9662700ca7488a9d9ff43597fbb0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080299"
---
# <a name="implement-an-expression-evaluator"></a>Implementare un analizzatore di espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 La valutazione di un'espressione è un'interazione complessa tra il motore di debug (DE), il provider di simboli (SP), l'oggetto binder e l'analizzatore di espressioni (EE). Questi quattro componenti sono connessi da interfacce implementate da un componente e utilizzate da un altro.

 L'EE accetta un'espressione dal de sotto forma di stringa e la analizza o la valuta. EE esegue le interfacce seguenti, che vengono utilizzate dal de:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  L'EE chiama l'oggetto binder, fornito dal de, per ottenere il valore di simboli e oggetti. L'EE usa le interfacce seguenti, implementate dal de:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE esegue [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2`fornisce il meccanismo per descrivere il risultato di una valutazione dell'espressione, ad esempio una variabile locale, una primitiva o un oggetto da Visual Studio, che visualizza quindi le informazioni appropriate nella finestra Variabili locali **,** **Espressione** di controllo o Controllo **immediato.**

  L'SP viene fornito all'EE dal de quando chiede informazioni. Sp esegue interfacce che descrivono indirizzi e campi, ad esempio le interfacce seguenti e i relativi derivati:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  L'EE usa tutte queste interfacce.

## <a name="in-this-section"></a>Contenuto della sezione
 [Strategia di implementazione dell'analizzatore di espressioni](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Definisce un processo in tre passaggi per la strategia di implementazione dell'analizzatore di espressioni (EE).

## <a name="see-also"></a>Vedi anche
- [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
