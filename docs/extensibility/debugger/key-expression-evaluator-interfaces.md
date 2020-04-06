---
title: Interfacce dell'analizzatore di espressioni chiave Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01527edac4000f0b2f7b89fdd507fc093f0d7734
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738496"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfacce dell'analizzatore di espressioni chiaveKey expression evaluator interfaces
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Quando si scrive un analizzatore di espressioni (EE), insieme al contesto di valutazione, è necessario avere familiarità con le interfacce seguenti.

## <a name="interface-descriptions"></a>Descrizioni dell'interfaccia

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Dispone di un singolo metodo, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), che ottiene una struttura di dati che rappresenta il punto di esecuzione corrente. Questa struttura di dati è uno dei tre argomenti che il motore di debug (DE) passa al [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) metodo per valutare un'espressione. Questa interfaccia viene in genere implementata dal provider di simboli.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Ha il [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) metodo, che ottiene l'area di memoria che contiene il valore corrente di un simbolo. Dato sia il metodo contenitore, rappresentato da un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) oggetto, e `IDebugBinder::Bind` il simbolo stesso, rappresentato da un [IDebugField](../../extensibility/debugger/reference/idebugfield.md) oggetto, restituisce il valore del simbolo. `IDebugBinder`viene in genere implementato dal DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Rappresenta un tipo di dati semplice. Per tipi più complessi, ad esempio matrici e metodi, utilizzare le interfacce [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) e [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) derivate, rispettivamente. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) è un'altra importante interfaccia derivata che rappresenta i simboli contenenti altri simboli, ad esempio metodi o classi. L'interfaccia `IDebugField` (e i relativi derivati) viene in genere implementata dal provider di simboli.

     Un `IDebugField` oggetto può essere utilizzato per trovare il nome e il tipo di un simbolo e, insieme a un [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) oggetto, può essere utilizzato per trovare il relativo valore.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Rappresenta i bit effettivi del valore in fase di esecuzione di un simbolo. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) accetta un [IDebugField](../../extensibility/debugger/reference/idebugfield.md) oggetto, che rappresenta un simbolo e restituisce un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) oggetto. Il [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) metodo restituisce il valore del simbolo in un buffer di memoria. Un DE implementa in genere questa interfaccia per rappresentare il valore di una proprietà in memoria.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Questa interfaccia rappresenta l'analizzatore di espressioni stesso. Il metodo key è [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), che restituisce un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfaccia.

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Questa interfaccia rappresenta un'espressione analizzata pronta per essere valutata. Il metodo chiave è [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) che restituisce un IDebugProperty2 che rappresenta il valore e il tipo dell'espressione.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Questa interfaccia rappresenta un valore e il relativo tipo ed è il risultato di una valutazione dell'espressione.

## <a name="see-also"></a>Vedere anche
- [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)
