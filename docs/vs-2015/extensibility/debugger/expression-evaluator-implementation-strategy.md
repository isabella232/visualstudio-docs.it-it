---
title: Strategia di implementazione dell'analizzatore di espressioni | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 757e74a9dde1c580a6116342948edd4eb42f9ca3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737884"
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategia di implementazione di un analizzatore di espressioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Uno degli approcci per creare rapidamente un analizzatore di espressioni (EE) consiste nell'implementare prima di tutto il codice minimo necessario per visualizzare variabili locali all'interno di **variabili locali** finestra. È utile tenere presente che in ogni riga i **variabili locali** finestra viene visualizzato il nome, tipo e valore di una variabile locale e che tutti e tre sono rappresentati da un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto. Il nome, tipo e valore di una variabile locale può essere ottenuti da un' `IDebugProperty2` chiamando relativi [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (metodo). Per altre informazioni su come visualizzare variabili locali all'interno di **variabili locali** finestra, vedere [visualizzare variabili locali](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Discussione  
 Una sequenza di implementazione possibili inizia con l'implementazione [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Il [analizzare](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) e il [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metodi devono essere implementati per visualizzare variabili locali. La chiamata `IDebugExpressionEvaluator::GetMethodProperty` restituisce un `IDebugProperty2` oggetto che rappresenta un metodo: vale a dire una [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) oggetto. Metodi stessi non vengono visualizzati nei **variabili locali** finestra.  
  
 Il [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metodo deve essere implementato successivamente. Il motore di debug (DE) chiama questo metodo per ottenere un elenco di argomenti e variabili locali, passando `IDebugProperty2::EnumChildren` una `guidFilter` argomento di `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` le chiamate [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) e [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinare i risultati in un'unica enumerazione. Visualizzare [variabili locali visualizzazione](../../extensibility/debugger/displaying-locals.md) per altri dettagli.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)

