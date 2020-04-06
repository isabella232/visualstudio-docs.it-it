---
title: Visualizzazione di locali Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d44b276aeb9c6acb0ef34cc186662d49246de7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738935"
---
# <a name="display-locals"></a>Visualizza gente del posto
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L'esecuzione avviene sempre nel contesto di un metodo, noto anche come metodo contenitore o metodo corrente. Quando l'esecuzione viene sospesa, Visual Studio chiama il motore di debug (DE) per ottenere un elenco di variabili e argomenti locali, chiamati collettivamente le variabili locali del metodo. Visual Studio visualizza queste variabili locali e i relativi valori nella finestra **Variabili locali.**

 Per visualizzare le variabili locali, il DE chiama il [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metodo appartenente a EE e gli assegna un contesto di valutazione, ovvero un provider di simboli (SP), l'indirizzo di esecuzione corrente e un oggetto gestore di associazione. Per ulteriori informazioni, vedere [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md). Se la chiamata ha `IDebugExpressionEvaluator::GetMethodProperty` esito positivo, il metodo restituisce un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto, che rappresenta il metodo che contiene l'indirizzo di esecuzione corrente.

 Il DE chiama [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) per ottenere un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) oggetto, che viene filtrato per restituire solo le variabili locali ed enumerato per produrre un elenco di [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) strutture. Ogni struttura contiene il nome, il tipo e il valore di un oggetto locale. Il tipo e il valore vengono memorizzati come stringhe formattate, adatte per la visualizzazione. Il nome, il tipo e il valore vengono in genere visualizzati insieme in una riga della finestra **Variabili locali.**

> [!NOTE]
> Le finestre **Controllo immediato** e **Controllo** visualizzano anche le variabili con lo stesso formato di nome, valore e tipo. Tuttavia, tali valori vengono ottenuti `IDebugProperty2::EnumChildren`chiamando [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) anziché .

## <a name="in-this-section"></a>Contenuto della sezione
 [Esempio di implementazione di gente del posto](../../extensibility/debugger/sample-implementation-of-locals.md) Vengono utilizzati esempi per eseguire il processo di implementazione delle variabili locali.

## <a name="related-sections"></a>Sezioni correlate
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md) Viene illustrato che quando il motore di debug (DE) chiama l'analizzatore di espressioni (EE), passa tre argomenti.

## <a name="see-also"></a>Vedere anche
 [Scrivere un analizzatore di espressioni CLRWrite a CLR expression evaluator](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
