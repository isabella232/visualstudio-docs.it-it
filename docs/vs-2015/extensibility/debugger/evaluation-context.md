---
title: Contesto di valutazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7dae6ddcb0c75f0dcbc2207465aed522a4210159
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840258"
---
# <a name="evaluation-context"></a>Contesto di valutazione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando il motore di debug (DE) chiama l'analizzatore di espressioni (EE), tre argomenti passati a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinano il contesto per la ricerca e la valutazione dei simboli, come illustrato nella tabella seguente.  
  
## <a name="arguments"></a>Argomenti  
  
|Argomento|Descrizione|  
|--------------|-----------------|  
|`pSymbolProvider`|Interfaccia [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) che specifica il gestore di simboli (SH) da utilizzare per identificare il simbolo.|  
|`pAddress`|Interfaccia [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) che specifica il punto di esecuzione corrente. Può essere usato per trovare il metodo che contiene il codice in esecuzione.|  
|`pBinder`|Interfaccia [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) che può essere utilizzata per trovare il valore e il tipo di un simbolo in base al nome.|  
  
 `IDebugParsedExpression::EvaluateSync` Restituisce un'interfaccia [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta il valore risultante e il relativo tipo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce dell'analizzatore di espressioni chiave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
