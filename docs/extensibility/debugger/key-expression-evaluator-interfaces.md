---
title: Interfacce dell'analizzatore di espressioni chiave | Microsoft Docs
description: Informazioni sulle interfacce che è necessario conoscere quando si scrive un analizzatore di espressioni, insieme al contesto di valutazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 38d5fa76cb816d67f1146f3db97350900403a827
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080273"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfacce dell'analizzatore di espressioni chiave
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Quando si scrive un analizzatore di espressioni (edizione Enterprise), insieme al contesto di valutazione, è necessario avere familiarità con le interfacce seguenti.

## <a name="interface-descriptions"></a>Descrizioni dell'interfaccia

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Dispone di un singolo metodo, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), che ottiene una struttura di dati che rappresenta il punto di esecuzione corrente. Questa struttura di dati è uno dei tre argomenti passati dal motore di debug (DE) al metodo [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) per valutare un'espressione. Questa interfaccia viene in genere implementata dal provider di simboli.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Dispone del [metodo Bind,](../../extensibility/debugger/reference/idebugbinder-bind.md) che ottiene l'area di memoria che contiene il valore corrente di un simbolo. Dato sia il metodo contenitore, rappresentato da un [oggetto IDebugObject,](../../extensibility/debugger/reference/idebugobject.md) che il simbolo stesso, rappresentato da un [oggetto IDebugField,](../../extensibility/debugger/reference/idebugfield.md) restituisce il `IDebugBinder::Bind` valore del simbolo. `IDebugBinder` viene in genere implementato dal de.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Rappresenta un tipo di dati semplice. Per i tipi più complessi, ad esempio matrici e metodi, usare rispettivamente le interfacce [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) e [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) derivate. [IDebugContainerField è un'altra](../../extensibility/debugger/reference/idebugcontainerfield.md) importante interfaccia derivata che rappresenta simboli contenenti altri simboli, ad esempio metodi o classi. `IDebugField`L'interfaccia (e i relativi derivati) viene in genere implementata dal provider di simboli.

     Un oggetto può essere usato per trovare il nome e il tipo di un simbolo e, insieme a un `IDebugField` [oggetto IDebugBinder,](../../extensibility/debugger/reference/idebugbinder.md) può essere usato per trovare il relativo valore.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Rappresenta i bit effettivi del valore di run-time di un simbolo. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) accetta un [oggetto IDebugField,](../../extensibility/debugger/reference/idebugfield.md) che rappresenta un simbolo, e restituisce un [oggetto IDebugObject.](../../extensibility/debugger/reference/idebugobject.md) Il [metodo GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) restituisce il valore del simbolo in un buffer di memoria. Un de implementa in genere questa interfaccia per rappresentare il valore di una proprietà in memoria.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Questa interfaccia rappresenta l'analizzatore di espressioni stesso. Il metodo chiave è [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), che restituisce [un'interfaccia IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Questa interfaccia rappresenta un'espressione analizzata pronta per la valutazione. Il metodo chiave è [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) che restituisce un oggetto IDebugProperty2 che rappresenta il valore e il tipo dell'espressione.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Questa interfaccia rappresenta un valore e il relativo tipo ed è il risultato di una valutazione dell'espressione.

## <a name="see-also"></a>Vedi anche
- [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)
