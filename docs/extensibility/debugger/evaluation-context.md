---
title: Contesto di valutazione | Microsoft Docs
description: "Quando il motore di debug chiama l'analizzatore di espressioni, gli argomenti determinano il contesto per la ricerca e la valutazione dei simboli: pSymbolProvider, pAddress e pBinder."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: fa9b199f31dc200fe128e6435b2967ab689724bb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153550"
---
# <a name="evaluation-context"></a>Contesto di valutazione
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Quando il motore di debug (DE) chiama l'analizzatore di espressioni (edizione Enterprise), tre argomenti passati a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinano il contesto per la ricerca e la valutazione dei simboli, come illustrato nella tabella seguente.

## <a name="arguments"></a>Argomenti

|Argomento|Descrizione|
|--------------|-----------------|
|`pSymbolProvider`|Interfaccia [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) che specifica il gestore simboli (SH) da usare per identificare il simbolo.|
|`pAddress`|Interfaccia [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) che specifica il punto di esecuzione corrente. Questa interfaccia trova il metodo che contiene il codice in esecuzione.|
|`pBinder`|Interfaccia [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) che trova il valore e il tipo di un simbolo in base al nome.|

 `IDebugParsedExpression::EvaluateSync` restituisce [un'interfaccia IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta il valore risultante e il relativo tipo.

## <a name="see-also"></a>Vedi anche
- [Interfacce dell'analizzatore di espressioni chiave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
