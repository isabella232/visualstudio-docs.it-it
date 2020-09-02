---
title: Eventi di controllo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4073da9036e11f90fbf7202095e70fce797ea015
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62414633"
---
# <a name="control-events"></a>Eventi di controllo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

È necessario inviare eventi durante l'esecuzione controllata del programma. Tutti gli eventi vengono inviati usando l'interfaccia [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) e hanno attributi che richiedono l'implementazione del metodo [IDebugEvent2:: GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) .  
  
## <a name="additional-methods"></a>Altri metodi  
 Per alcuni eventi è richiesta l'implementazione di metodi aggiuntivi, come indicato di seguito:  
  
- Per inviare l'interfaccia [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) quando il motore di debug (de) viene inizializzato, è necessario implementare il metodo [IDebugEngineCreateEvent2:: GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) .  
  
- Il controllo dell'esecuzione richiede l'implementazione di tali eventi di controllo come le interfacce [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) e[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) . **IDebugBreakEvent2** è obbligatorio solo per le interruzioni asincrone.  
  
- Per l'esecuzione di funzioni è necessaria l'implementazione dell'interfaccia [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) e dei relativi metodi.  
  
  Gli eventi che derivano dai punti di interruzione richiedono l'implementazione delle interfacce [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)e [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) , oltre ai metodi [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) e [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .  
  
  Per la valutazione di espressioni asincrone è necessario implementare l'interfaccia [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) e i relativi metodi [IDebugExpressionEvaluationCompleteEvent2:: GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[e GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) .  
  
  Per gli eventi sincroni è necessario implementare il metodo [IDebugEngine2:: ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .  
  
  Affinché il motore scriva l'output di tipo stringa, è necessario implementare il metodo [IDebugOutputStringEvent2:: GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
