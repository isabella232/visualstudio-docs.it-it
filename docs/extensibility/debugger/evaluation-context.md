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
ms.openlocfilehash: 001a7a5b1e4d044e389317900a9192586575b44ed19caa5e09aa6ceca30a9c15
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417821"
---
# <a name="evaluation-context"></a>Contesto di valutazione
> [!IMPORTANT]
> In Visual Studio 2015 questa modalità di implementazione degli analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Quando il motore di debug chiama l'analizzatore di espressioni (edizione Enterprise), tre argomenti passati a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinano il contesto per la ricerca e la valutazione dei simboli, come illustrato nella tabella seguente.

## <a name="arguments"></a>Argomenti

|Argomento|Descrizione|
|--------------|-----------------|
|`pSymbolProvider`|Interfaccia [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) che specifica il gestore di simboli (SH) da usare per identificare il simbolo.|
|`pAddress`|Interfaccia [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) che specifica il punto di esecuzione corrente. Questa interfaccia trova il metodo che contiene il codice in esecuzione.|
|`pBinder`|Interfaccia [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) che trova il valore e il tipo di un simbolo in base al nome.|

 `IDebugParsedExpression::EvaluateSync` restituisce [un'interfaccia IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta il valore risultante e il relativo tipo.

## <a name="see-also"></a>Vedi anche
- [Interfacce dell'analizzatore di espressioni chiave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Visualizzazione delle variabili locali](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
