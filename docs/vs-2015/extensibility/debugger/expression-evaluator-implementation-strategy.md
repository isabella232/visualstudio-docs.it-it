---
title: Strategia di implementazione dell'analizzatore di espressioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2ded111c371fc1a42c8f1ee08769f5b06aeda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840047"
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategia di implementazione di un analizzatore di espressioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Un approccio per creare rapidamente un analizzatore di espressioni consiste nel implementare innanzitutto il codice minimo necessario per visualizzare le variabili locali nella finestra variabili **locali** . È utile tenere presente che ogni riga della finestra variabili **locali** Visualizza il nome, il tipo e il valore di una variabile locale e che tutti e tre sono rappresentati da un oggetto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) . Il nome, il tipo e il valore di una variabile locale possono essere ottenuti da un `IDebugProperty2` oggetto chiamando il relativo metodo [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Per ulteriori informazioni su come visualizzare le variabili locali nella finestra variabili **locali** , vedere Visualizzazione di variabili [locali](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Discussione  
 Una possibile sequenza di implementazione inizia con l'implementazione di [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). I metodi [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) e [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) devono essere implementati per visualizzare variabili locali. La chiamata `IDebugExpressionEvaluator::GetMethodProperty` a restituisce un `IDebugProperty2` oggetto che rappresenta un metodo, ovvero un oggetto [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . I metodi stessi non vengono visualizzati nella finestra **variabili locali** .  
  
 Il metodo [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) deve essere implementato successivamente. Il motore di debug (DE) chiama questo metodo per ottenere un elenco di variabili e argomenti locali passando `IDebugProperty2::EnumChildren` un `guidFilter` argomento di `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` chiama [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) e [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinando i risultati in un'unica enumerazione. Per altri dettagli, vedere [visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)
