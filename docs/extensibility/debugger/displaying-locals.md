---
title: Visualizzazione di variabili locali | Microsoft Docs
description: Informazioni sull'elenco di variabili e argomenti locali, chiamati collettivamente le variabili locali del metodo, che vengono visualizzati quando l'esecuzione viene sospesa.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ddc7bc564e4e294144eeb3fa34db8bdf73971053
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915544"
---
# <a name="display-locals"></a>Visualizza variabili locali
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L'esecuzione avviene sempre all'interno del contesto di un metodo, noto anche come metodo contenitore o metodo corrente. Quando l'esecuzione viene sospesa, Visual Studio chiama il motore di debug (DE) per ottenere un elenco di variabili e argomenti locali, chiamati collettivamente le variabili locali del metodo. Visual Studio Visualizza le variabili locali e i relativi valori nella finestra **variabili locali** .

 Per visualizzare le variabili locali, il DE chiama il metodo [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) che appartiene a EE e fornisce un contesto di valutazione, ovvero, un provider di simboli (SP), l'indirizzo di esecuzione corrente e un oggetto Binder. Per ulteriori informazioni, vedere [contesto di valutazione](../../extensibility/debugger/evaluation-context.md). Se la chiamata ha esito positivo, il `IDebugExpressionEvaluator::GetMethodProperty` metodo restituisce un oggetto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta il metodo che contiene l'indirizzo di esecuzione corrente.

 Il DE chiama [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) per ottenere un oggetto [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , che viene filtrato in modo da restituire solo variabili locali ed enumerate per produrre un elenco di strutture di [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) . Ogni struttura contiene il nome, il tipo e il valore di un oggetto locale. Il tipo e il valore vengono archiviati come stringhe formattate, adatte per la visualizzazione. Il nome, il tipo e il valore vengono in genere visualizzati insieme in una riga della finestra **variabili locali** .

> [!NOTE]
> Nelle finestre controllo **immediato** e espressione di **controllo** vengono visualizzate anche le variabili con lo stesso formato di nome, valore e tipo. Tuttavia, tali valori vengono ottenuti chiamando [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) anziché `IDebugProperty2::EnumChildren` .

## <a name="in-this-section"></a>Contenuto della sezione
 [Implementazione di esempio di variabili locali](../../extensibility/debugger/sample-implementation-of-locals.md) USA esempi per eseguire il processo di implementazione di variabili locali.

## <a name="related-sections"></a>Sezioni correlate
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md) Viene illustrato che quando il motore di debug (DE) chiama l'analizzatore di espressioni (EE), passa tre argomenti.

## <a name="see-also"></a>Vedi anche
 [Scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
