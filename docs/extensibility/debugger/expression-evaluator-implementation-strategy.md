---
title: Strategia di implementazione dell'analizzatore di espressioni | Microsoft Docs
description: Informazioni su una strategia per la creazione di un analizzatore di espressioni implementando prima il codice per visualizzare le variabili locali nella finestra Variabili locali.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: b6576d4656dd4afeed452dce7ac9f15036d12be37886c5d105961a2c0862e188
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342752"
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategia di implementazione dell'analizzatore di espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Un approccio alla creazione rapida di un analizzatore di espressioni (edizione Enterprise) consiste nell'implementare prima il codice minimo necessario per visualizzare le variabili locali nella **finestra** Variabili locali. È utile rendersi conto che  ogni riga nella finestra Variabili locali visualizza il nome, il tipo e il valore di una variabile locale e che tutte e tre sono rappresentate da un [oggetto IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md) Il nome, il tipo e il valore di una variabile locale vengono ottenuti da un `IDebugProperty2` oggetto chiamando il relativo metodo [GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Per altre informazioni su come visualizzare le variabili locali nella finestra **Variabili** locali, vedere [Visualizzazione delle variabili locali](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Discussione
 Una possibile sequenza di implementazione inizia con [l'implementazione di IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). I [metodi Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) e [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) devono essere implementati per visualizzare le variabili locali. La `IDebugExpressionEvaluator::GetMethodProperty` chiamata a restituisce un oggetto che rappresenta un `IDebugProperty2` metodo, ad esempio un oggetto [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) I metodi stessi non vengono visualizzati nella **finestra** Variabili locali.

 Il [metodo EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) deve essere implementato successivamente. Il motore di debug chiama questo metodo per ottenere un elenco di variabili e argomenti locali passando `IDebugProperty2::EnumChildren` un `guidFilter` argomento di `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` chiama [EnumArguments ed](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinando i risultati in una singola enumerazione. Per [altri dettagli, vedere](../../extensibility/debugger/displaying-locals.md) Visualizzare variabili locali.

## <a name="see-also"></a>Vedi anche
- [Implementare un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Visualizzare le variabili locali](../../extensibility/debugger/displaying-locals.md)
