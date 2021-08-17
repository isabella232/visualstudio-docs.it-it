---
title: Visualizzazione delle impostazioni locali | Microsoft Docs
description: Informazioni sull'elenco di variabili e argomenti locali, chiamati collettivamente variabili locali del metodo, che vengono visualizzati quando l'esecuzione viene sospesa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: bb5706c951dd274579037cd466d6846cbd9d5dd3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096674"
---
# <a name="display-locals"></a>Visualizzare le variabili locali
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L'esecuzione avviene sempre all'interno del contesto di un metodo, noto anche come metodo contenitore o metodo corrente. Quando l'esecuzione viene sospesa, Visual Studio chiama il motore di debug (DE) per ottenere un elenco di variabili e argomenti locali, chiamati collettivamente variabili locali del metodo. Visual Studio queste variabili locali e i relativi valori vengono visualizzati nella **finestra** Variabili locali.

 Per visualizzare le variabili locali, de chiama il metodo [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) appartenente al edizione Enterprise e fornisce un contesto di valutazione, ovvero un provider di simboli (SP), l'indirizzo di esecuzione corrente e un oggetto binder. Per altre informazioni, vedere [Contesto di valutazione.](../../extensibility/debugger/evaluation-context.md) Se la chiamata ha esito positivo, il `IDebugExpressionEvaluator::GetMethodProperty` metodo restituisce un oggetto [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta il metodo che contiene l'indirizzo di esecuzione corrente.

 DE chiama [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) per ottenere un oggetto [IEnumDebugPropertyInfo2,](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) filtrato in modo da restituire solo variabili locali [ed](../../extensibility/debugger/reference/debug-property-info.md) enumerato per produrre un elenco di DEBUG_PROPERTY_INFO strutture. Ogni struttura contiene il nome, il tipo e il valore di un oggetto locale. Il tipo e il valore vengono archiviati come stringhe formattate, adatte per la visualizzazione. Il nome, il tipo e il valore vengono in genere visualizzati insieme in una riga della **finestra** Variabili locali.

> [!NOTE]
> Le **finestre Controllo immediato** e Espressioni **di** controllo visualizzano anche le variabili con lo stesso formato di nome, valore e tipo. Tuttavia, questi valori vengono ottenuti chiamando [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) anziché `IDebugProperty2::EnumChildren` .

## <a name="in-this-section"></a>Contenuto della sezione
 [Implementazione di esempio di variabili locali](../../extensibility/debugger/sample-implementation-of-locals.md) Usa esempi per eseguire il processo di implementazione delle variabili locali.

## <a name="related-sections"></a>Sezioni correlate
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md) Spiega che quando il motore di debug (DE) chiama l'analizzatore di espressioni (edizione Enterprise), passa tre argomenti.

## <a name="see-also"></a>Vedi anche
 [Scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
