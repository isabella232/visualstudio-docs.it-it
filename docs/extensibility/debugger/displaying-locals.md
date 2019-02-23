---
title: Visualizzazione di variabili locali | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea6345ef56cec8e3a7d90ed964c320f96fdbcdcd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711241"
---
# <a name="display-locals"></a>Variabili locali di visualizzazione
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [esempio analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Sempre l'esecuzione avviene all'interno del contesto di un metodo, noto anche come metodo contenitore o il metodo corrente. Quando l'esecuzione viene sospesa, Visual Studio chiama il motore di debug (DE) per ottenere un elenco delle variabili locali e gli argomenti, collettivamente denominati variabili locali del metodo. Visual Studio visualizza le variabili locali e i relativi valori nel **variabili locali** finestra.

 Per visualizzare variabili locali, chiama il DE il [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metodo appartenente all'analizzatore di Espressioni e gli assegna un contesto di valutazione, che è un provider di simboli (SP), l'indirizzo di esecuzione corrente e un oggetto strumento di associazione. Per altre informazioni, vedere [contesto di valutazione](../../extensibility/debugger/evaluation-context.md). Se la chiamata ha esito positivo, il `IDebugExpressionEvaluator::GetMethodProperty` metodo restituisce un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta il metodo che contiene l'indirizzo di esecuzione corrente.

 Le chiamate DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) per ottenere un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) oggetto, che viene filtrata in modo da restituire soli variabili locali ed enumerata per produrre un elenco di [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)strutture. Ogni struttura contiene il nome, tipo e valore di una variabile locale. Il tipo e il valore vengono archiviati come stringhe formattate, adatte per la visualizzazione. Il nome, tipo e valore sono in genere visualizzati insieme in una sola riga del **variabili locali** finestra.

> [!NOTE]
>  Il **controllo immediato** e **Watch** finestre vengono visualizzate anche le variabili con lo stesso formato di nome, valore e tipo. Tuttavia, tali valori vengono ottenuti chiamando [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) invece di `IDebugProperty2::EnumChildren`.

## <a name="in-this-section"></a>Contenuto della sezione
 [Implementazione di esempio di variabili locali](../../extensibility/debugger/sample-implementation-of-locals.md) Usa esempi per eseguire passo passo il processo di implementazione di variabili locali.

## <a name="related-sections"></a>Sezioni correlate
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md) illustra che quando il motore di debug (DE) chiama l'analizzatore di espressioni (EE), passa di tre argomenti.

## <a name="see-also"></a>Vedere anche
 [Scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)