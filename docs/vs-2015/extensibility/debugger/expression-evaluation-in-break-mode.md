---
title: Valutazione dell'espressione in modalità di interruzione | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a74119edfb390dab0a8ce0fddd96046ca80ad92d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540877"
---
# <a name="expression-evaluation-in-break-mode"></a>Valutazione delle espressioni in modalità di interruzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [valutazione delle espressioni in modalità interruzione](https://docs.microsoft.com/visualstudio/extensibility/debugger/expression-evaluation-in-break-mode).  
  
Di seguito viene descritto il processo che si verifica quando il debugger è in modalità di interruzione e deve eseguire la valutazione dell'espressione.  
  
## <a name="expression-evaluation-process"></a>Processo di valutazione di espressioni  
 Questi sono i passaggi fondamentali nella valutazione di un'espressione:  
  
1.  Gestore di sessione di debug (SDM) chiama [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere un'interfaccia di contesto, espressione [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Chiama quindi il modello SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la stringa da analizzare.  
  
3.  Se ParseText non restituisce S_OK, viene restituito il motivo dell'errore.  
  
     -in caso contrario-  
  
     Se ParseText restituisce S_OK, il modello SDM può quindi chiamare [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oppure [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere un valore finale dall'espressione analizzata.  
  
    -   In caso di utilizzo `IDebugExpression2::EvaluateSync`, l'interfaccia di callback specificato viene utilizzato per comunicare il processo continuo di valutazione. Viene restituito il valore finale un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia.  
  
    -   In caso di utilizzo `IDebugExpression2::EvaluateAsync`, l'interfaccia di callback specificato viene utilizzato per comunicare il processo continuo di valutazione. Una volta completata la valutazione, EvaluateAsync invia un' [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfaccia tramite il callback. Con questa interfaccia, è possibile ottenere il valore finale con [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)

