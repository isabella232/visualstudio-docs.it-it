---
title: Valutazione di espressioni (SDK per il debug di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f2a84f01168dd01921d933a80fe052c1a6c6447
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562198"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Valutazione delle espressioni (Visual Studio Debugging SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Durante la modalità di rottura, l'IDE deve essere in grado di valutare espressioni semplici che coinvolgono diverse variabili del programma. A tale scopo, il motore di debug (DE) deve essere in grado di analizzare e valutare un'espressione immessa in una delle finestre dell'IDE.  
  
 Le espressioni vengono create usando il metodo [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e sono rappresentate dall'interfaccia [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) risultante.  
  
 L'interfaccia **IDebugExpression2** viene implementata da de e chiama il relativo metodo **EvalAsync** per restituire un'interfaccia [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) all'IDE, in modo da visualizzare i risultati della valutazione dell'espressione nell'IDE. [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) restituisce una struttura che può essere usata per inserire il valore di un'espressione in un finestra espressioni di controllo o nella finestra variabili locali.  
  
 Il pacchetto di debug o il gestore di debug della sessione (SDM) chiama [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per ottenere un'interfaccia [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta il risultato della valutazione. `IDebugProperty2` dispone di metodi che restituiscono il nome, il tipo e il valore dell'espressione. Queste informazioni vengono visualizzate in diverse finestre del debugger.  
  
## <a name="using-expression-evaluation"></a>Uso della valutazione delle espressioni  
 Per usare la valutazione delle espressioni, è necessario implementare il metodo [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e tutti i metodi dell'interfaccia [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , come illustrato nella tabella seguente.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Valuta un'espressione in modo asincrono.|  
|[Interruzione](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina la valutazione dell'espressione asincrona.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Valuta un'espressione in modo sincrono.|  
  
 Per la valutazione sincrona e asincrona è richiesta l'implementazione del metodo [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Per la valutazione di espressioni asincrone è necessaria l'implementazione di [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
