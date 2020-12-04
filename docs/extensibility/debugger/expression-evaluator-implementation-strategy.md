---
title: Strategia di implementazione dell'analizzatore di espressioni | Microsoft Docs
description: Informazioni su una strategia per la creazione di un analizzatore di espressioni implementando prima di tutto il codice per visualizzare le variabili locali nella finestra variabili locali.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b936b465c3a7becbdcb3ea4f36a16b839260ad74
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560148"
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategia di implementazione dell'analizzatore di espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Un approccio per creare rapidamente un analizzatore di espressioni consiste nel implementare innanzitutto il codice minimo necessario per visualizzare le variabili locali nella finestra variabili **locali** . È utile tenere presente che ogni riga della finestra variabili **locali** Visualizza il nome, il tipo e il valore di una variabile locale e che tutti e tre sono rappresentati da un oggetto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) . Il nome, il tipo e il valore di una variabile locale vengono ottenuti da un `IDebugProperty2` oggetto chiamando il relativo metodo [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Per ulteriori informazioni su come visualizzare le variabili locali nella finestra variabili **locali** , vedere Visualizzazione di variabili [locali](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Discussione
 Una possibile sequenza di implementazione inizia con l'implementazione di [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). I metodi [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) e [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) devono essere implementati per visualizzare variabili locali. La chiamata `IDebugExpressionEvaluator::GetMethodProperty` a restituisce un `IDebugProperty2` oggetto che rappresenta un metodo, ovvero un oggetto [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . I metodi stessi non vengono visualizzati nella finestra **variabili locali** .

 Il metodo [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) deve essere implementato successivamente. Il motore di debug (DE) chiama questo metodo per ottenere un elenco di variabili e argomenti locali passando `IDebugProperty2::EnumChildren` un `guidFilter` argomento di `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` chiama [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) e [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinando i risultati in un'unica enumerazione. Per altri dettagli, vedere [visualizzare le variabili locali](../../extensibility/debugger/displaying-locals.md) .

## <a name="see-also"></a>Vedere anche
- [Implementare un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Visualizza variabili locali](../../extensibility/debugger/displaying-locals.md)
