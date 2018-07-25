---
title: Contesto di valutazione | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 523ef45d52a81a475eca0e3560243e0eb8357bbd
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232455"
---
# <a name="evaluation-context"></a>Contesto di valutazione
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [esempio analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando il motore di debug (DE) chiama l'analizzatore di espressioni (EE), tre argomenti che vengono passati al [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinare il contesto per trovare e valutare i simboli, come illustrato nella tabella seguente.  
  
## <a name="arguments"></a>Argomenti  
  
|Argomento|Descrizione|  
|--------------|-----------------|  
|`pSymbolProvider`|Un' [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) interfaccia che specifica il gestore di simboli (SH) da utilizzare per identificare il simbolo.|  
|`pAddress`|Un' [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfaccia che specifica il punto di esecuzione corrente. Questa interfaccia consente di trovare il metodo che contiene il codice in esecuzione.|  
|`pBinder`|Un' [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfaccia che consente di trovare il valore e il tipo di un simbolo in base al nome.|  
  
 `IDebugParsedExpression::EvaluateSync` Restituisce un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta il valore risultante e il relativo tipo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce dell'analizzatore di espressioni chiave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)