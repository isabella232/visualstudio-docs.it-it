---
title: Contesto di valutazione | Microsoft Docs
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
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0bce0ea65aa025d7250c49b5d91f8d075a9720aa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253279"
---
# <a name="evaluation-context"></a>Contesto di valutazione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando il motore di debug (DE) chiama l'analizzatore di espressioni (EE), tre argomenti passati al [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinare il contesto per trovare e valutare i simboli, come illustrato nella tabella seguente.  
  
## <a name="arguments"></a>Argomenti  
  
|Argomento|Descrizione|  
|--------------|-----------------|  
|`pSymbolProvider`|Un' [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) interfaccia che specifica il gestore di simboli (SH) da utilizzare per identificare il simbolo.|  
|`pAddress`|Un' [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfaccia che specifica il punto di esecuzione corrente. Ciò consente di individuare il metodo che contiene il codice in esecuzione.|  
|`pBinder`|Un' [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfaccia che può essere utilizzata per trovare il valore e il tipo di un simbolo in base al nome.|  
  
 `IDebugParsedExpression::EvaluateSync` Restituisce un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta il valore risultante e il relativo tipo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce dell'analizzatore di espressioni chiave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

