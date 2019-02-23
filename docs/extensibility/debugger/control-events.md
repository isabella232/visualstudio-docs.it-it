---
title: Eventi di controllo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8fbe2f3c3835c55fffefe4692c4e8779b48e9c5e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683389"
---
# <a name="control-events"></a>Eventi di controllo
È necessario inviare gli eventi durante l'esecuzione del programma controllato. Tutti gli eventi vengono inviati usando il [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) l'interfaccia e avere attributi che è necessario implementare il [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) (metodo).

## <a name="additional-methods"></a>Metodi aggiuntivi
 Alcuni eventi richiedono l'implementazione di metodi aggiuntivi, come indicato di seguito:

- L'invio di [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfaccia quando viene inizializzato il motore di debug (DE) richiede l'implementazione di [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) (metodo).

- Controllo dell'esecuzione è necessaria l'implementazione di tali eventi di controllo come il [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) e[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfacce. **IDebugBreakEvent2** è obbligatorio solo per le interruzioni asincrone.

- L'esecuzione di funzioni è necessaria l'implementazione del [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfaccia e i relativi metodi.

  Gli eventi che deriva da punti di interruzione richiedono l'implementazione del [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), e [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) le interfacce, così come il [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) e [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) metodi.

  Valutazione delle espressioni asincrone richiede di implementare il [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfaccia e la relativa [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md) [e GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) metodi.

  Gli eventi sincroni necessario implementare il [IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) (metodo).

  Per il motore scrivere l'output di tipo stringa, è necessario implementare il [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [Valutazione di controllo e lo stato di esecuzione](../../extensibility/debugger/execution-control-and-state-evaluation.md)