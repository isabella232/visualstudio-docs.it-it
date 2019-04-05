---
title: Valutazione delle espressioni (Visual Studio Debugging SDK) | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969487"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Valutazione delle espressioni (Visual Studio Debugging SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Durante la modalità di interruzione, l'IDE deve essere in grado di valutare le espressioni semplici che coinvolgono numerose variabili del programma. A tale scopo, il motore di debug (DE) deve essere in grado di analizzare e valutare un'espressione che viene immesso in una delle finestre dell'IDE.  
  
 Le espressioni vengono create usando il [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metodo e sono rappresentati da risultante [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia.  
  
 Il **IDebugExpression2** interfaccia viene implementata per la Germania e chiama relativo **EvalAsync** metodo restituisca un' [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia all'IDE, per visualizzare il risultati della valutazione dell'espressione nell'IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) restituisce una struttura che può essere utilizzata per inserire il valore di un'espressione in una finestra Espressioni di controllo o nella finestra variabili locali.  
  
 Gestione del debug del pacchetto o sessione di debug (SDM) chiama [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) oppure [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per ottenere un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta il risultato della valutazione. `IDebugProperty2` dispone di metodi che restituiscono il nome, tipo e valore dell'espressione. Queste informazioni vengono visualizzate nelle varie finestre del debugger.  
  
## <a name="using-expression-evaluation"></a>Tramite valutazione dell'espressione  
 Per usare la valutazione dell'espressione, è necessario implementare il [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metodo e tutti i metodi delle [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia, come illustrato nella tabella seguente.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Valuta un'espressione in modo asincrono.|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina la valutazione dell'espressione asincrona.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Valuta un'espressione in modo sincrono.|  
  
 Valutazione sincrona e asincrona richiedono l'implementazione del [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (metodo). Valutazione delle espressioni asincrone richiede l'implementazione di [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
