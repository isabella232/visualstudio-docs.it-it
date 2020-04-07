---
title: Eventi di controllo Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2c3ad9c9b63923bdf2f107e7bc582f3c76cd62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739094"
---
# <a name="control-events"></a>Eventi di controllo
È necessario inviare eventi durante l'esecuzione controllata del programma. Tutti gli eventi vengono inviati utilizzando il [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) interfaccia e dispongono di attributi che richiedono l'implementazione di [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) metodo.

## <a name="additional-methods"></a>Metodi aggiuntivi
 Alcuni eventi richiedono l'implementazione di metodi aggiuntivi, come indicato di seguito:Some events require implementation of additional methods, as follows:

- L'invio di [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfaccia quando viene inizializzato il motore di debug (DE) richiede l'implementazione di [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) metodo.

- Il controllo dell'esecuzione richiede l'implementazione di tali eventi di controllo come il [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) e[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfacce. **IDebugBreakEvent2** è necessario solo per le interruzioni asincrone.

- L'esecuzione di funzioni richiede l'implementazione dell'interfaccia [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) e dei relativi metodi.

  Gli eventi che derivano dai punti di interruzione richiedono l'implementazione delle interfacce [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)e [IDebugBreakpointBoundEvent2,](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) nonché dei metodi [IDebugBreakpointBoundEvent2::GetPendingBreakpoint e](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .

  La valutazione asincrona dell'espressione richiede l'implementazione dell'interfaccia [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) e dei relativi metodi [IDebugExpressionEvaluationCompleteEvent2::GetExpression.](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[and GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)

  Gli eventi sincroni richiedono l'implementazione del metodo [IDebugEngine2::ContinueFromSynchronousEvent.Synchronous events require implementing the IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) method.

  Affinché il motore scriva l'output in stile stringa, è necessario implementare il [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) metodo.

## <a name="see-also"></a>Vedere anche
- [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
