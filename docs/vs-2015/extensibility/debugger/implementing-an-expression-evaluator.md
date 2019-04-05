---
title: Implementazione di un analizzatore di espressioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b075a674d56dc7f1e79fdd03b31601b79f0b3f6e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965531"
---
# <a name="implementing-an-expression-evaluator"></a>Implementazione di un analizzatore di espressioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Valutazione di un'espressione è un'interazione complicata fra il motore di debug (DE), il provider di simboli (SP), l'oggetto strumento di associazione e l'analizzatore di espressioni (EE) stesso. Queste quattro componenti sono connesse tramite le interfacce che vengono implementate da un componente e usate da un altro.  
  
 L'analizzatore di Espressioni accetta un'espressione da DE sotto forma di stringa e analizza o lo valuta. L'analizzatore di Espressioni implementa le interfacce seguenti, che vengono usate per la Germania:  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  L'analizzatore di Espressioni chiama l'oggetto binder, fornito per la Germania, per ottenere il valore di simboli e oggetti. L'analizzatore di Espressioni Usa le interfacce seguenti, che sono implementate dal DE:  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  Implementa l'analizzatore di Espressioni [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` fornisce il meccanismo per la descrizione del risultato della valutazione di un'espressione, ad esempio una variabile locale, una primitiva o un oggetto, a Visual Studio, che consente di visualizzare le informazioni appropriate nella **variabili locali**,  **Guarda**, oppure **immediato** finestra.  
  
  Stored procedure è assegnata all'analizzatore di Espressioni per la Germania quando vengono richieste informazioni. La stored procedure SP implementa le interfacce che descrivono gli indirizzi e campi, ad esempio le interfacce seguenti e i relativi derivati:  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  L'analizzatore di Espressioni utilizza tutte queste interfacce.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Strategia di implementazione di un analizzatore di espressioni](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Definisce un processo in tre passaggi per la strategia di implementazione dell'analizzatore di espressioni (EE) di espressione.  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
